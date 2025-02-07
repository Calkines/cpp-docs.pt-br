---
title: Bem-vindo ao C++ (C++ moderno)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: 5b2868d20c047eef7762256ff8c9bf43de7a0de0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209522"
---
# <a name="welcome-back-to-c-modern-c"></a>Bem-vindo ao C++ (C++ moderno)

A C++ é uma das linguagens de programação mais usadas do mundo e os programas bem escritos que a utilizam são rápidos e eficientes. Essa linguagem é mais flexível que as demais porque é possível usá-la para criar diversos aplicativos, desde jogos divertidos e envolventes a softwares científicos de alto desempenho, drivers de dispositivos, programas incorporados e aplicativos clientes do Windows. Há mais de 20 anos, C++ é usada para solucionar problemas como esses e de muitos outros tipos. Mas talvez você ainda não saiba que cada vez mais programadores C++ estão deixando a programação C para trás e usando a moderna linguagem C++ em seu lugar.

Um dos requisitos originais da C++ é a compatibilidade com as versões anteriores da linguagem C. Com isso, a linguagem C++ passou por diversas iterações — C com classes, especificações da linguagem C++ original e muitas outras melhorias. Por causa dessa herança, a linguagem C++ muitas vezes é chamada de linguagem de programação multiparadigma. Com a C++, você pode deixar a programação estritamente processual em estilo C que envolve ponteiros brutos, matrizes, cadeias de caracteres com terminação nula, estruturas de dados personalizadas e outros recursos que podem garantir um desempenho ótimo, mas que também geram muitos bugs e aumentam a complexidade.  Como a programação em C vem acompanhada de todos esses riscos, um dos principais objetivos da linguagem C++ era possibilitar a criação de programas fortemente tipados, fáceis de gravar, ampliar e manter. No início, a linguagem C++ adotou paradigmas de programação como a programação orientada a objetos. Com os anos, outros recursos foram adicionados à linguagem com bibliotecas padrão de estruturas de dados e algoritmos altamente testados. Foram essas adições que possibilitaram o estilo C++ moderno.

Destaques do C++ moderno:

- Escopo baseado em heap, em vez de escopo global estático ou heap.

- Dedução de tipo, em vez de nomes de tipo explícitos.

- Ponteiros inteligentes, em vez de ponteiros duplos.

- `std::string` e `std::wstring` tipos (consulte [ \<cadeia de caracteres >](../standard-library/string.md)), em vez de brutos `char[]` matrizes.

- [Biblioteca padrão C++](../standard-library/cpp-standard-library-header-files.md) como contêineres `vector`, `list`, e `map` em vez de matrizes brutas ou contêineres personalizados. Ver [ \<vector >](../standard-library/vector.md), [ \<lista >](../standard-library/list.md), e [ \<mapa >](../standard-library/map.md).

- Biblioteca padrão C++ [algoritmos](../standard-library/algorithm.md) em vez de manualmente codificados.

- Exceções para relatar e lidar com condições de erro.

- Comunicação entre threads usando a biblioteca padrão C++ livres de bloqueio `std::atomic<>` (consulte [ \<atomic >](../standard-library/atomic.md)) em vez de outros mecanismos de comunicação entre threads.

- Embutido [funções lambda](../cpp/lambda-expressions-in-cpp.md) em vez de pequenas funções implementadas separadamente.

- Baseado em intervalo para loops para gravar loops mais robustos que funcionam com matrizes, contêineres da biblioteca padrão C++ e tempo de execução do Windows coleções na forma `for ( for-range-declaration : expression )`. Isso faz parte do suporte à linguagem base. Para obter mais informações, consulte [de instrução (C++) baseado em intervalo](../cpp/range-based-for-statement-cpp.md).

A linguagem C++ também evoluiu. Compare os snippets de código a seguir. Este trecho mostra como a linguagem C++ era antigamente:

```cpp
#include <vector>

void f()
{
    // Assume circle and shape are user-defined types
    circle* p = new circle( 42 );
    vector<shape*> v = load_shapes();

    for( vector<circle*>::iterator i = v.begin(); i != v.end(); ++i ) {
        if( *i && **i == *p )
            cout << **i << " is a match\n";
    }

    // CAUTION: If v's pointers own the objects, then you
    // must delete them all before v goes out of scope.
    // If v's pointers do not own the objects, and you delete
    // them here, any code that tries to dereference copies
    // of the pointers will cause null pointer exceptions.
    for( vector<circle*>::iterator i = v.begin();
            i != v.end(); ++i ) {
        delete *i; // not exception safe
    }

    // Don't forget to delete this, too.
    delete p;
} // end f()
```

Veja o mesmo código com a linguagem C++ moderna:

```cpp
#include <memory>
#include <vector>

void f()
{
    // ...
    auto p = make_shared<circle>( 42 );
    vector<shared_ptr<shape>> v = load_shapes();

    for( auto& s : v )
    {
        if( s && *s == *p )
        {
            cout << *s << " is a match\n";
        }
    }
}
```

Na linguagem C++ moderna, você não precisa usar novos tratamentos de exceções nem excluí-los, pois é possível usar ponteiros inteligentes. Quando você usa o **automática** dedução de tipo e [função lambda](../cpp/lambda-expressions-in-cpp.md), você pode escrever código mais rápido, restringi-lo e compreendê-los melhor. E um baseado em intervalo **para** loop é mais limpo, mais fácil de usar e menos propenso a erros não intencional de um estilo C **para** loop. Você pode usar texto clichê com linhas de código mínimas para gravar seu aplicativo. Você também pode fazer com que o código seja à prova de exceções e memória e que ele não precise lidar com alocação/desalocação ou códigos de erros.

A linguagem C++ moderna incorpora dois tipos de poliformismo: tempo de compilação, por meio de modelos, e tempo de execução, por meio de herança e virtualização. É possível combinar esses dois tipos de poliformismo para melhorar a eficiência. O modelo de biblioteca padrão C++ `shared_ptr` usa métodos virtuais internos para realizar seu tipo aparentemente sem esforços. Porém, não use a virtualização em excesso no poliformismo quando um modelo for a melhor opção. Os modelos podem ser muito úteis.

Se está migrando de outra linguagem para C++, principalmente de uma linguagem gerenciada em que a maioria dos tipos é de referência e poucos são de valor, você precisa saber que as classes C++ são tipos de valor por padrão. No entanto, você pode especificá-los como tipos de referência para habilitar o comportamento polimórfico que possibilita usar a programação orientada a objetos. Uma perspectiva útil: os tipos de valor estão mais relacionados à memória e ao controle de layouts. Já os tipos de referência estão mais relacionados às classes básicas e funções virtuais para possibilitar o uso de poliformismo. Por padrão, os tipos de valor podem ser copiados. Cada um deles tem um construtor de cópia ou operador de atribuição de cópia. Ao especificar um tipo de referência, desabilite a funcionalidade de cópia das classes, o construtor de cópia e o operador de atribuição de cópia, e use um destruidor virtual, que é compatível com poliformismo. Os tipos de valor também estão relacionados ao conteúdo que, quando copiado, gera dois valores independentes, que podem ser modificados separadamente. Porém, os tipos de referência estão relacionados à identidade: o tipo de objeto. Por isso, esses tipos também são chamados de polimórficos.

A C++ está passando por uma renovação porque a potência voltou a ser essencial. Linguagens como Java e C# são úteis quando a produtividade do programador é um aspecto importante. Contudo, elas têm suas limitações quando potência e desempenho são essenciais. Para obter alta eficiência e potência, principalmente em dispositivos com hardware limitado, não há páreo para a linguagem C++.

Além de a linhagem ser moderna, as ferramentas de desenvolvimento também são. Visual Studio faz todas as partes do ciclo de desenvolvimento robusto e eficiente. Ele conta com ferramentas de ALM (Gerenciamento de ciclo de vida de aplicativos), melhorias de IDE, como IntelliSense, mecanismos úteis para ferramentas, como XAML, e ferramentas de compilação, depuração e muitas outras.

Os artigos da documentação sobre esse assunto fornecem diretrizes de alto nível e melhores práticas para os recursos e as técnicas mais importantes para gravar programas C++ modernos.

- [Sistema de tipo C++](../cpp/cpp-type-system-modern-cpp.md)

- [Inicialização uniforme e delegação de construtores](../cpp/uniform-initialization-and-delegating-constructors.md)

- [Tempo de vida do objeto e gerenciamento de recursos](../cpp/object-lifetime-and-resource-management-modern-cpp.md)

- [Recursos de objetos próprios (RAII)](../cpp/objects-own-resources-raii.md)

- [Ponteiros inteligentes](../cpp/smart-pointers-modern-cpp.md)

- [Pimpl para encapsulamento do tempo de compilação](../cpp/pimpl-for-compile-time-encapsulation-modern-cpp.md)

- [Contêineres](../cpp/containers-modern-cpp.md)

- [Algoritmos](../cpp/algorithms-modern-cpp.md)

- [Cadeia de caracteres e formatação (C++ moderno) de e/s](../cpp/string-and-i-o-formatting-modern-cpp.md)

- [Erros e tratamento de exceções](../cpp/errors-and-exception-handling-modern-cpp.md)

- [Portabilidade em limites ABI](../cpp/portability-at-abi-boundaries-modern-cpp.md)

Para obter mais informações, consulte o artigo de Stack Overflow [expressões do C++ que foram preteridas no c++11](https://stackoverflow.com/questions/9299101/which-c-idioms-are-deprecated-in-c11).

## <a name="see-also"></a>Consulte também

[Referência da linguagem C++](../cpp/cpp-language-reference.md)<br/>
[Expressões Lambda](../cpp/lambda-expressions-in-cpp.md)<br/>
[Biblioteca Padrão do C++](../standard-library/cpp-standard-library-reference.md)<br/>
[Conformidade com a linguagem Visual C++](../overview/visual-cpp-language-conformance.md)