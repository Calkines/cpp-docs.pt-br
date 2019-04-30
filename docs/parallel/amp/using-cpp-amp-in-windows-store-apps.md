---
title: Usando o C++ AMP em aplicativos UWP
ms.date: 11/04/2016
ms.assetid: 85577298-2c28-4209-9470-eb21048615db
ms.openlocfilehash: 31fede0a2419e56d53cb16521b08067dac5facc6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405346"
---
# <a name="using-c-amp-in-uwp-apps"></a>Usando o C++ AMP em aplicativos UWP

Você pode usar o C++ AMP (C++ Accelerated Massive Parallelism) em seu aplicativo da plataforma Universal do Windows (UWP) para executar cálculos em GPU (Graphics Processing Unit) ou outros Aceleradores computacionais. No entanto, o C++ AMP não fornece APIs para trabalhar diretamente com tipos de tempo de execução do Windows e o tempo de execução do Windows não fornece um wrapper para o C++ AMP. Quando você usa tipos de tempo de execução do Windows em seu código — incluindo aqueles que você mesmo criou — você deve converter os tipos que são compatíveis com o C++ AMP.

## <a name="performance-considerations"></a>Considerações sobre desempenho

Se você estiver usando o Visual C++ extensões de componentes C++/CX para criar seu aplicativo da plataforma Universal do Windows (UWP), é recomendável que você use tipos simples-dados antigos (POD) juntamente com o armazenamento contíguo — por exemplo, `std::vector` ou matrizes C-style — para dados que serão usados com C++ AMP. Isso pode ajudá-lo a alcançar um desempenho mais alto do que usando tipos não POD ou contêineres do Windows RT porque nenhum empacotamento deve ocorrer.

Em um kernel do C++ AMP, para acessar os dados são armazenados dessa forma, basta encapsular a `std::vector` ou o armazenamento de matriz em um `concurrency::array_view` e, em seguida, usar a visualização de matriz em um `concurrency::parallel_for_each` loop:

```cpp
// simple vector addition example
std::vector<int> data0(1024, 1);
std::vector<int> data1(1024, 2);
std::vector<int> data_out(data0.size(), 0);

concurrency::array_view<int, 1> av0(data0.size(), data0);
concurrency::array_view<int, 1> av1(data1.size(), data1);
concurrency::array_view<int, 1> av2(data_out.size(), data2);

av2.discard_data();

concurrency::parallel_for_each(av0.extent, [=](concurrency::index<1> idx) restrict(amp)
    {
        av2[idx] = av0[idx] + av1[idx];
    });
```

## <a name="marshaling-windows-runtime-types"></a>Marshaling tipos de Tempo de Execução do Windows

Quando você trabalha com APIs do Windows Runtime, você talvez queira usar o C++ AMP nos dados armazenados em um contêiner de tempo de execução do Windows, como um `Platform::Array<T>^` ou em tipos de dados complexos, como classes ou estruturas que são declaradas usando o **ref** palavra-chave ou o **valor** palavra-chave. Nessas situações, você precisa realizar algum trabalho extra para disponibilizar os dados para o C++ AMP.

### <a name="platformarrayt-where-t-is-a-pod-type"></a>Platform:: array\<T > ^, onde T é um tipo POD

Quando você encontrar um `Platform::Array<T>^` e T é um tipo POD, você pode acessar o armazenamento subjacente apenas usando o `get` função de membro:

```cpp
Platform::Array<float>^ arr; // Assume that this was returned by a Windows Runtime API
concurrency::array_view<float, 1> av(arr->Length, &arr->get(0));
```

Se T não é um tipo POD, use a técnica descrita na seção a seguir para usar os dados com o C++ AMP.

### <a name="windows-runtime-types-ref-classes-and-value-classes"></a>Tipos de Tempo de Execução do Windows: classes ref e value

C++ AMP não dá suporte a tipos de dados complexos. Isso inclui tipos não POD e quaisquer tipos que são declarados usando o **ref** palavra-chave ou o **valor** palavra-chave. Se um tipo sem suporte for usado em um `restrict(amp)` contexto, um erro de tempo de compilação é gerado.

Quando você encontrar um tipo sem suporte, você pode copiar partes interessantes dos dados em um `concurrency::array` objeto. Além de disponibilizar os dados para o C++ AMP consumir, essa abordagem de cópia manual também pode melhorar o desempenho, maximizando a localidade dos dados e garantindo que os dados que não serão usados não sejam copiados para o acelerador. Você pode melhorar ainda mais o desempenho usando um *matriz de teste*, que é uma forma especial de `concurrency::array` que fornece uma dica para o tempo de execução de AMP que a matriz deve ser otimizada para a transferência frequente entre ela e outras matrizes no acelerador especificado.

```cpp
// pixel_color.h
ref class pixel_color sealed
{
public:
    pixel_color(Platform::String^ color_name, int red, int green, int blue)
    {
        name = color_name;
        r = red;
        g = green;
        b = blue;
    }

    property Platform::String^ name;
    property int r;
    property int g;
    property int b;
};

// Some other file

std::vector<pixel_color^> pixels (256);

for (pixel_color ^pixel : pixels)
{
    pixels.push_back(ref new pixel_color("blue", 0, 0, 255));
}

// Create the accelerators
auto cpuAccelerator = concurrency::accelerator(concurrency::accelerator::cpu_accelerator);
auto devAccelerator = concurrency::accelerator(concurrency::accelerator::default_accelerator);

// Create the staging arrays
concurrency::array<float, 1> red_vec(256, cpuAccelerator.default_view, devAccelerator.default_view);
concurrency::array<float, 1>  blue_vec(256, cpuAccelerator.default_view, devAccelerator.default_view);

// Extract data from the complex array of structs into staging arrays.
concurrency::parallel_for(0, 256, [&](int i)
    {
        red_vec[i] = pixels[i]->r;
        blue_vec[i] = pixels[i]->b;
    });

// Array views are still used to copy data to the accelerator
concurrency::array_view<float, 1> av_red(red_vec);
concurrency::array_view<float, 1> av_blue(blue_vec);

// Change all pixels from blue to red.
concurrency::parallel_for_each(av_red.extent, [=](index<1> idx) restrict(amp)
    {
        av_red[idx] = 255;
        av_blue[idx] = 0;
    });
```

## <a name="see-also"></a>Consulte também

[Criar seu primeiro aplicativo UWP usando C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)<br/>
[Criando componentes de tempo de execução do Windows em C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
