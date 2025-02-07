---
title: Classe strstreambuf
ms.date: 11/04/2016
f1_keywords:
- strstream/std::strstreambuf::freeze
- strstream/std::strstreambuf::overflow
- strstream/std::strstreambuf::pbackfail
- strstream/std::strstreambuf::pcount
- strstream/std::strstreambuf::seekoff
- strstream/std::strstreambuf::seekpos
- strstream/std::strstreambuf::str
- strstream/std::strstreambuf::underflow
helpviewer_keywords:
- std::strstreambuf [C++], freeze
- std::strstreambuf [C++], overflow
- std::strstreambuf [C++], pbackfail
- std::strstreambuf [C++], pcount
- std::strstreambuf [C++], seekoff
- std::strstreambuf [C++], seekpos
- std::strstreambuf [C++], str
- std::strstreambuf [C++], underflow
ms.assetid: b040b8ea-0669-4eba-8908-6a9cc159c54b
ms.openlocfilehash: f24d8fe99bc211e026172e42669cf5e430ad31e8
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459072"
---
# <a name="strstreambuf-class"></a>Classe strstreambuf

Descreve um buffer de fluxo que controla a transmissão de elementos de e para uma sequência de elementos armazenados em um objeto de matriz **Char** .

## <a name="syntax"></a>Sintaxe

```cpp
class strstreambuf : public streambuf
```

## <a name="remarks"></a>Comentários

Dependendo de como o objeto é construído, ele pode ser alocado, estendido e liberado conforme necessário para acomodar alterações na sequência.

Um objeto da classe `strstreambuf` armazena vários bits de informações sobre o modo conforme o modo `strstreambuf`. Esses bits indicam se a sequência controlada:

- Foi alocada e precisa ser eventualmente liberada.

- É modificável.

- É extensível, realocando armazenamento.

- Foi congelada e, portanto, precisa ser descongelado antes que o objeto é destruído ou liberado (se alocados) por uma agência diferente do objeto.

Uma sequência controlada que é congelada não pode ser modificada ou estendida, independentemente do estado desses bits de modo separado.

O objeto também armazena ponteiros para as duas funções que controlam `strstreambuf` alocação. Se eles forem ponteiros nulos, o objeto desenvolve seu próprio método de alocar e liberar o armazenamento para a sequência controlada.

> [!NOTE]
> Essa classe foi preterida. Considere o uso de [stringbuf](../standard-library/sstream-typedefs.md#stringbuf) ou [wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf), em vez disso.

### <a name="constructors"></a>Construtores

|Construtor|Descrição|
|-|-|
|[strstreambuf](#strstreambuf)|Constrói um objeto do tipo `strstreambuf`.|

### <a name="member-functions"></a>Funções de membro

|Função de membro|Descrição|
|-|-|
|[freeze](#freeze)|Faz com que um buffer de fluxo esteja indisponível por meio de operações de buffer de fluxo.|
|[overflow](#overflow)|Uma função virtual protegida que pode ser chamada quando um novo caractere é inserido em um buffer cheio.|
|[pbackfail](#pbackfail)|Uma função de membro virtual protegida que tenta colocar um elemento de volta no fluxo de entrada, então torná-lo elemento atual (apontando para o ponteiro seguinte).|
|[pcount](#pcount)|Retorna uma contagem do número de elementos gravados na sequência controlada.|
|[seekoff](#seekoff)|Uma função de membro virtual protegida que tenta alterar as posições atuais para os fluxos controlados.|
|[seekpos](#seekpos)|Uma função de membro virtual protegida que tenta alterar as posições atuais para os fluxos controlados.|
|[str](#str)|Chama [freeze](#freeze) e retorna um ponteiro para o início da sequência controlada.|
|[underflow](#underflow)|Uma função virtual protegida para extrair o elemento atual do fluxo de entrada.|

## <a name="requirements"></a>Requisitos

**Cabeçalho:** \<strstream>

**Namespace:** std

## <a name="freeze"></a>  strstreambuf::freeze

Faz com que um buffer de fluxo esteja indisponível por meio de operações de buffer de fluxo.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parâmetros

*_Freezeit*\
Um **bool** que indica se você deseja que o fluxo seja congelado.

### <a name="remarks"></a>Comentários

Se *_Freezeit* for true, a função alterará o modo `strstreambuf` armazenado para tornar a sequência controlada congelada. Caso contrário, torna a sequência controlada não congelada.

[str](#str) implica `freeze`.

> [!NOTE]
> Um buffer congelado não será liberado durante `strstreambuf` destruição. Será necessário descongelar o buffer antes que ele seja liberado para evitar um vazamento de memória.

### <a name="example"></a>Exemplo

```cpp
// strstreambuf_freeze.cpp
// compile with: /EHsc

#include <iostream>
#include <strstream>

using namespace std;

void report(strstream &x)
{
    if (!x.good())
        cout << "stream bad" << endl;
    else
        cout << "stream good" << endl;
}

int main()
{
    strstream x;

    x << "test1";
    cout << "before freeze: ";
    report(x);

    // Calling str freezes stream.
    cout.write(x.rdbuf()->str(), 5) << endl;
    cout << "after freeze: ";
    report(x);

    // Stream is bad now, wrote on frozen stream
    x << "test1.5";
    cout << "after write to frozen stream: ";
    report(x);

    // Unfreeze stream, but it is still bad
    x.rdbuf()->freeze(false);
    cout << "after unfreezing stream: ";
    report(x);

    // Clear stream
    x.clear();
    cout << "after clearing stream: ";
    report(x);

    x << "test3";
    cout.write(x.rdbuf()->str(), 10) << endl;

    // Clean up.  Failure to unfreeze stream will cause a
    // memory leak.
    x.rdbuf()->freeze(false);
}
```

```Output
before freeze: stream good
test1
after freeze: stream good
after write to frozen stream: stream bad
after unfreezing stream: stream bad
after clearing stream: stream good
test1test3
```

## <a name="overflow"></a>  strstreambuf::overflow

Uma função virtual protegida que pode ser chamada quando um novo caractere é inserido em um buffer cheio.

```cpp
virtual int overflow(int _Meta = EOF);
```

### <a name="parameters"></a>Parâmetros

*_Meta*\
O caractere a ser inserido no buffer ou `EOF`.

### <a name="return-value"></a>Valor de retorno

Se a função não conseguir obter êxito, ela retornará `EOF`. Caso contrário, se  *\_meta* == `EOF`, retornará algum valor diferente de `EOF`. Caso contrário, retornará  *\_meta*.

### <a name="remarks"></a>Comentários

`EOF`Se  *\_meta* ! =, a função de membro virtual protegido tentará inserir o `(char)_Meta` elemento no buffer de saída. Isso pode ser feito de várias maneiras:

- Se houver uma posição de gravação disponível, ela poderá armazenar o elemento na posição de gravação e incrementar o próximo ponteiro para o buffer de saída.

- Se o modo de strstreambuf armazenado diz que a sequência controlada é modificável, extensível e não congelada, a função pode disponibilizar uma posição de gravação ao alocar novos para o buffer de saída. Estender o buffer de saída dessa forma também estende qualquer buffer de entrada associado.

## <a name="pbackfail"></a>  strstreambuf::pbackfail

Uma função de membro virtual protegida que tenta colocar um elemento de volta no fluxo de entrada, então torná-lo elemento atual (apontando para o ponteiro seguinte).

```cpp
virtual int pbackfail(int _Meta = EOF);
```

### <a name="parameters"></a>Parâmetros

*_Meta*\
O caractere a ser inserido no buffer ou `EOF`.

### <a name="return-value"></a>Valor de retorno

Se a função não conseguir obter êxito, ela retornará `EOF`. Caso contrário, se  *\_meta* == `EOF`, retornará algum valor diferente de `EOF`. Caso contrário, retornará  *\_meta*.

### <a name="remarks"></a>Comentários

A função membro virtual protegida tenta colocar um elemento de volta no buffer de entrada e, em seguida, faz com que ele seja o elemento atual (apontado pelo próximo ponteiro).

*Se\_meta*,oelemento`EOF`para retornar é efetivamente o que já está no fluxo antes do elemento atual. ==  Caso contrário, esse elemento será substituído `ch = (char)_Meta`por. A função pode colocar um elemento de volta de várias maneiras:

- Se uma posição putback estiver disponível e o elemento armazenado nesse ponto de comparação for `ch`igual a, ele poderá diminuir o ponteiro seguinte para o buffer de entrada.

- Se uma posição putback estiver disponível e o modo strstreambuf informar que a sequência controlada pode ser modificada, a função poderá armazenar `ch` na posição putback e decrementar o próximo ponteiro para o buffer de entrada.

## <a name="pcount"></a>  strstreambuf::pcount

Retorna uma contagem do número de elementos gravados na sequência controlada.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Valor de retorno

Uma contagem do número de elementos gravados na sequência controlada.

### <a name="remarks"></a>Comentários

Especificamente, se [pptr](../standard-library/basic-streambuf-class.md#pptr) é um ponteiro nulo, a função retorna zero. Caso contrário, retornará `pptr`  -  [pbase](../standard-library/basic-streambuf-class.md#pbase).

### <a name="example"></a>Exemplo

```cpp
// strstreambuf_pcount.cpp
// compile with: /EHsc
#include <iostream>
#include <strstream>
using namespace std;

int main( )
{
   strstream x;
   x << "test1";
   cout << x.rdbuf( )->pcount( ) << endl;
   x << "test2";
   cout << x.rdbuf( )->pcount( ) << endl;
}
```

## <a name="seekoff"></a>  strstreambuf::seekoff

Uma função de membro virtual protegida que tenta alterar as posições atuais para os fluxos controlados.

```cpp
virtual streampos seekoff(streamoff _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parâmetros

*_Off*\
A posição a ser procurada em relação ao *_Way*.

*_Way*\
O ponto de partida para operações de deslocamento. Consulte [seekdir](../standard-library/ios-base-class.md#seekdir) para valores possíveis.

*_Which*\
Especifica o modo para a posição do ponteiro. O padrão é permitir que você modifique as posições de leitura e gravação.

### <a name="return-value"></a>Valor de retorno

Se a função tiver êxito na alteração de uma ou de ambas as posições de fluxo, ela retornará a posição do fluxo resultante. Caso contrário, ela falhará e retornará uma posição de fluxo inválida.

### <a name="remarks"></a>Comentários

A função de membro virtual protegida busca alterar as posições atuais para os fluxos controlados. Para um objeto da classe strstreambuf, uma posição de fluxo consiste em apenas um deslocamento de fluxo. O deslocamento zero designa o primeiro elemento da sequência controlada.

A nova posição é determinada da seguinte forma:

- Se `_Way == ios_base::beg`, a nova posição será o início do fluxo, mais *_Off*.

- Se `_Way == ios_base::cur`, a nova posição será a posição atual do fluxo mais *_Off*.

- Se `_Way == ios_base::end`, a nova posição será o final do fluxo mais *_Off*.

Se `_Which & ios_base::in` for diferente de zero e o buffer de entrada existir, a função alterará a próxima posição para ler no buffer de entrada. Se `_Which & ios_base::out` também for diferente de `_Way != ios_base::cur`zero, e o buffer de saída existir, a função também definirá a próxima posição a ser gravada para corresponder à próxima posição a ser lida.

Caso contrário, `_Which & ios_base::out` se for diferente de zero e o buffer de saída existir, a função alterará a próxima posição para gravar no buffer de saída. Caso contrário, a operação de posicionamento falhará. Para que uma operação de posicionamento seja bem-sucedida, a posição do fluxo resultante deve estar dentro da sequência controlada.

## <a name="seekpos"></a>  strstreambuf::seekpos

Uma função de membro virtual protegida que tenta alterar as posições atuais para os fluxos controlados.

```cpp
virtual streampos seekpos(streampos _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parâmetros

*_Sp*\
A posição pela qual buscar.

*_Which*\
Especifica o modo para a posição do ponteiro. O padrão é permitir que você modifique as posições de leitura e gravação.

### <a name="return-value"></a>Valor de retorno

Se a função tiver êxito na alteração de uma ou de ambas as posições de fluxo, ela retornará a posição do fluxo resultante. Caso contrário, ela falhará e retornará uma posição de fluxo inválida. Para determinar se a posição de fluxo é inválida, compare o valor retornado com `pos_type(off_type(-1))`.

### <a name="remarks"></a>Comentários

A função de membro virtual protegida busca alterar as posições atuais para os fluxos controlados. Para um objeto da classe strstreambuf, uma posição de fluxo consiste em apenas um deslocamento de fluxo. O deslocamento zero designa o primeiro elemento da sequência controlada. A nova posição é determinada por *_Sp*.

Se `_Which` & **ios_base::in** é diferente de zero e o buffer de entrada existir, a função altera a próxima posição de leitura no buffer de entrada. Se `_Which` & `ios_base::out` é diferente de zero e o buffer de saída existir, a função também define a próxima posição de gravação coincidir com a próxima posição de leitura. Caso contrário, se `_Which` & `ios_base::out` é diferente de zero e o buffer de saída existir, a função altera a próxima posição de gravação no buffer de saída. Caso contrário, a operação de posicionamento falhará. Para que uma operação de posicionamento seja bem-sucedida, a posição do fluxo resultante deve estar dentro da sequência controlada.

## <a name="str"></a>  strstreambuf::str

Chama [freeze](#freeze) e retorna um ponteiro para o início da sequência controlada.

```cpp
char *str();
```

### <a name="return-value"></a>Valor de retorno

Um ponteiro para o início da sequência controlada.

### <a name="remarks"></a>Comentários

Nenhum elemento nulo de terminação existe, a menos que você insira um explicitamente.

### <a name="example"></a>Exemplo

Consulte [strstreambuf::freeze](#freeze) para ver uma amostra que usa **str**.

## <a name="strstreambuf"></a>  strstreambuf::strstreambuf

Constrói um objeto do tipo `strstreambuf`.

```cpp
explicit strstreambuf(streamsize count = 0);

strstreambuf(void (* _Allocfunc)(size_t),
    void (* _Freefunc)(void*));

strstreambuf(char* _Getptr,
    streamsize count,
    char* _Putptr = 0);

strstreambuf(signed char* _Getptr,
    streamsize count,
    signed char* _Putptr = 0);

strstreambuf(unsigned char* _Getptr,
    streamsize count,
    unsigned char* _Putptr = 0);

strstreambuf(const char* _Getptr,
    streamsize count);

strstreambuf(const signed char* _Getptr,
    streamsize count);

strstreambuf(const unsigned char* _Getptr,
    streamsize count);
```

### <a name="parameters"></a>Parâmetros

*_Allocfunc*\
A função usada para alocar memória do buffer.

*contar*\
Determina o comprimento do buffer apontado por *_Getptr*. Se *_Getptr* não for um argumento (primeiro formulário de Construtor), um tamanho de alocação sugerido para os buffers.

*_Freefunc*\
A função usada para liberar memória do buffer.

*_Getptr*\
Um buffer usado para a entrada.

*_Putptr*\
Um buffer usado para a saída.

### <a name="remarks"></a>Comentários

O primeiro construtor armazena um ponteiro nulo em todos os ponteiros controlando o buffer de entrada, o buffer de saída e a alocação strstreambuf. Ele define o modo de strstreambuf armazenado para tornar a sequência controlada modificável e extensível. Ele também aceita *Count* como um tamanho de alocação inicial sugerido.

O segundo construtor se comporta como a primeira, exceto pelo fato de que ele armazena  *\_Allocfunc* como o ponteiro para a função a fim de chamar para alocar armazenamento e  *\_Freefunc* como o ponteiro para a função a fim de chamar gratuitamente esse armazenamento.

Os três construtores:

```cpp
strstreambuf(char *_Getptr,
    streamsize count,
    char *putptr = 0);

strstreambuf(signed char *_Getptr,
    streamsize count,
    signed char *putptr = 0);

strstreambuf(unsigned char *_Getptr,
    streamsize count,
    unsigned char *putptr = 0);
```

também se comportam como o primeiro, exceto que `_Getptr` designa o objeto de matriz usado para manter a sequência controlada. (Portanto, não deve ser um ponteiro nulo.) O número de elementos *N* na matriz é determinado como segue:

- Se (`count` > 0), *N* será `count`.

- Se (`count` = = 0), *N* `strlen`será (( **const** `char` *) `_Getptr` ).

- Se (`count` < 0), *N* será **INT_MAX**.

Se `_Putptr` for um ponteiro nulo, a função estabelece apenas um buffer de entrada, executando:

```cpp
setg(_Getptr,
    _Getptr,
    _Getptr + N);
```

Caso contrário, ele estabelece os buffers de entrada e saída, executando:

```cpp
setg(_Getptr,
    _Getptr,
    _Putptr);

setp(_Putptr,
    _Getptr + N);
```

Nesse caso, `_Putptr` deve estar no intervalo [ `_Getptr`, `_Getptr`  +  *N*].

Finalmente, os três construtores:

```cpp
strstreambuf(const char *_Getptr,
    streamsize count);

strstreambuf(const signed char *_Getptr,
    streamsize count);

strstreambuf(const unsigned char *_Getptr,
    streamsize count);
```

todos se comportam da mesma maneira, como:

```cpp
streambuf((char *)_Getptr, count);
```

exceto pelo fato que o modo armazenado não torna a sequência controlada modificável ou extensível.

## <a name="underflow"></a>  strstreambuf::underflow

Uma função virtual protegida para extrair o elemento atual do fluxo de entrada.

```cpp
virtual int underflow();
```

### <a name="return-value"></a>Valor de retorno

Se a função não conseguir obter êxito, ela retornará `EOF`. Caso contrário, retorna o elemento atual no fluxo de entrada, convertido conforme descrito acima.

### <a name="remarks"></a>Comentários

A função de membro virtual protegida `ch` tenta extrair o elemento atual do buffer de entrada, avançar a posição atual do fluxo e retornar o elemento como (`int`) (`unsigned char`) **ch**. Ele pode fazer isso em apenas uma maneira: se uma posição de leitura estiver disponível, ela `ch` será aceita como o elemento armazenado na posição de leitura e avança o próximo ponteiro para o buffer de entrada.

## <a name="see-also"></a>Consulte também

[streambuf](../standard-library/streambuf-typedefs.md#streambuf)\
[Acesso Thread-Safe na Biblioteca Padrão C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programação de iostream](../standard-library/iostream-programming.md)\
[Convenções de iostreams](../standard-library/iostreams-conventions.md)
