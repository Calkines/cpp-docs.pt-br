---
title: Classe basic_filebuf
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_filebuf
- fstream/std::basic_filebuf::char_type
- fstream/std::basic_filebuf::int_type
- fstream/std::basic_filebuf::off_type
- fstream/std::basic_filebuf::pos_type
- fstream/std::basic_filebuf::traits_type
- fstream/std::basic_filebuf::close
- fstream/std::basic_filebuf::is_open
- fstream/std::basic_filebuf::open
- fstream/std::basic_filebuf::overflow
- fstream/std::basic_filebuf::pbackfail
- fstream/std::basic_filebuf::seekoff
- fstream/std::basic_filebuf::seekpos
- fstream/std::basic_filebuf::setbuf
- fstream/std::basic_filebuf::Swap
- fstream/std::basic_filebuf::sync
- fstream/std::basic_filebuf::uflow
- fstream/std::basic_filebuf::underflow
helpviewer_keywords:
- std::basic_filebuf [C++]
- std::basic_filebuf [C++], char_type
- std::basic_filebuf [C++], int_type
- std::basic_filebuf [C++], off_type
- std::basic_filebuf [C++], pos_type
- std::basic_filebuf [C++], traits_type
- std::basic_filebuf [C++], close
- std::basic_filebuf [C++], is_open
- std::basic_filebuf [C++], open
- std::basic_filebuf [C++], overflow
- std::basic_filebuf [C++], pbackfail
- std::basic_filebuf [C++], seekoff
- std::basic_filebuf [C++], seekpos
- std::basic_filebuf [C++], setbuf
- std::basic_filebuf [C++], Swap
- std::basic_filebuf [C++], sync
- std::basic_filebuf [C++], uflow
- std::basic_filebuf [C++], underflow
ms.assetid: 3196ba5c-bf38-41bd-9a95-70323ddfca1a
ms.openlocfilehash: ae72523c5c0a769a0267da94fead5ea29664276e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459475"
---
# <a name="basicfilebuf-class"></a>Classe basic_filebuf

Descreve um buffer de fluxo que controla a transmissão de elementos do tipo *elem*, cujas características de caractere são determinadas pela classe *TR*, de e para uma sequência de elementos armazenados em um arquivo externo.

## <a name="syntax"></a>Sintaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_filebuf : public basic_streambuf<Elem, Tr>
```

### <a name="parameters"></a>Parâmetros

*Elem*\
O elemento básico no buffer de arquivo.

*TR*\
As características do elemento básico no buffer de arquivo (geralmente `char_traits` <  `Elem`>).

## <a name="remarks"></a>Comentários

A classe de modelo descreve um buffer de fluxo que controla a transmissão de elementos do tipo *Elem*, cujas características dos caracteres são determinadas pela classe *Tr*, para e de uma sequência de elementos armazenados em um arquivo externo.

> [!NOTE]
> Objetos do tipo `basic_filebuf` são criados com um buffer interno do tipo `char *` , independentemente do `char_type` especificado pelo parâmetro de tipo *elem*. Isso significa que uma cadeia de caracteres Unicode (contendo os caracteres **wchar_t** ) será convertida em uma cadeia de caracteres ANSI (contendo caracteres **Char** ) antes de ser gravada no buffer interno. Para armazenar cadeias de caracteres Unicode no buffer, crie um novo buffer do tipo **wchar_t** e defina-o usando o método [basic_streambuf::p ubsetbuf](../standard-library/basic-streambuf-class.md#pubsetbuf) `()` . Para ver um exemplo que demonstra esse comportamento, consulte abaixo.

Um objeto da classe `basic_filebuf`< `Elem`, `Tr`> armazena um ponteiro de arquivo, que designa o objeto `FILE` que controla o fluxo associado a um arquivo aberto. Ele também armazena ponteiros para duas facetas de conversão de arquivo para uso pelas funções membro protegidas [estouro](#overflow) e [estouro negativo](#underflow). Para obter mais informações, consulte [basic_filebuf::open](#open).

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra como forçar um objeto do tipo `basic_filebuf<wchar_t>` a armazenar caracteres Unicode em seu buffer interno chamando o método `pubsetbuf()`.

```cpp
// unicode_basic_filebuf.cpp
// compile with: /EHsc

#include <iostream>
#include <string>
#include <fstream>
#include <iomanip>
#include <memory.h>
#include <string.h>

#define IBUFSIZE 16

using namespace std;

void hexdump(const string& filename);

int main()
{
    wchar_t* wszHello = L"Hello World";
    wchar_t wBuffer[128];

    basic_filebuf<wchar_t> wOutFile;

    // Open a file, wcHello.txt, then write to it, then dump the
    // file's contents in hex
    wOutFile.open("wcHello.txt",
        ios_base::out | ios_base::trunc | ios_base::binary);
    if(!wOutFile.is_open())
    {
        cout << "Error Opening wcHello.txt\n";
        return -1;
    }
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));
    wOutFile.close();
    cout << "Hex Dump of wcHello.txt - note that output is ANSI chars:\n";
    hexdump(string("wcHello.txt"));

    // Open a file, wwHello.txt, then set the internal buffer of
    // the basic_filebuf object to be of type wchar_t, then write
    // to the file and dump the file's contents in hex
    wOutFile.open("wwHello.txt",
        ios_base::out | ios_base::trunc | ios_base::binary);
    if(!wOutFile.is_open())
    {
        cout << "Error Opening wwHello.txt\n";
        return -1;
    }
    wOutFile.pubsetbuf(wBuffer, (streamsize)128);
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));
    wOutFile.close();
    cout << "\nHex Dump of wwHello.txt - note that output is wchar_t chars:\n";
    hexdump(string("wwHello.txt"));

    return 0;
}

// dump contents of filename to stdout in hex
void hexdump(const string& filename)
{
    fstream ifile(filename.c_str(),
        ios_base::in | ios_base::binary);
    char *ibuff = new char[IBUFSIZE];
    char *obuff = new char[(IBUFSIZE*2)+1];
    int i;

    if(!ifile.is_open())
    {
        cout << "Cannot Open " << filename.c_str()
             << " for reading\n";
        return;
    }
    if(!ibuff || !obuff)
    {
        cout << "Cannot Allocate buffers\n";
        ifile.close();
        return;
    }

    while(!ifile.eof())
    {
        memset(obuff,0,(IBUFSIZE*2)+1);
        memset(ibuff,0,IBUFSIZE);
        ifile.read(ibuff,IBUFSIZE);

        // corner case where file is exactly a multiple of
        // 16 bytes in length
        if(ibuff[0] == 0 && ifile.eof())
            break;

        for(i = 0; i < IBUFSIZE; i++)
        {
            if(ibuff[i] >= ' ')
                obuff[i] = ibuff[i];
            else
                obuff[i] = '.';

            cout << setfill('0') << setw(2) << hex
                 << (int)ibuff[i] << ' ';
        }
        cout << "  " << obuff << endl;
    }
    ifile.close();
}
```

```Output
Hex Dump of wcHello.txt - note that output is ANSI chars:
48 65 6c 6c 6f 20 57 6f 72 6c 64 00 00 00 00 00   Hello World.....

Hex Dump of wwHello.txt - note that output is wchar_t chars:
48 00 65 00 6c 00 6c 00 6f 00 20 00 57 00 6f 00   H.e.l.l.o. .W.o.
72 00 6c 00 64 00 00 00 00 00 00 00 00 00 00 00   r.l.d...........
```

### <a name="constructors"></a>Construtores

|Construtor|Descrição|
|-|-|
|[basic_filebuf](#basic_filebuf)|Constrói um objeto do tipo `basic_filebuf`.|

### <a name="typedefs"></a>Typedefs

|Nome de tipo|Descrição|
|-|-|
|[char_type](#char_type)|Associa um nome de tipo ao parâmetro de modelo `Elem`.|
|[int_type](#int_type)|Faz com que esse tipo no escopo de `basic_filebuf` seja equivalente ao tipo com o mesmo nome no escopo de `Tr`.|
|[off_type](#off_type)|Faz com que esse tipo no escopo de `basic_filebuf` seja equivalente ao tipo com o mesmo nome no escopo de `Tr`.|
|[pos_type](#pos_type)|Faz com que esse tipo no escopo de `basic_filebuf` seja equivalente ao tipo com o mesmo nome no escopo de `Tr`.|
|[traits_type](#traits_type)|Associa um nome de tipo ao parâmetro de modelo `Tr`.|

### <a name="member-functions"></a>Funções de membro

|Função de membro|Descrição|
|-|-|
|[close](#close)|Fecha um arquivo.|
|[is_open](#is_open)|Indica se um arquivo está aberto.|
|[open](#open)|Abre um arquivo.|
|[overflow](#overflow)|Uma função virtual protegida que pode ser chamada quando um novo caractere é inserido em um buffer cheio.|
|[pbackfail](#pbackfail)|Uma função membro virtual protegida que tenta colocar um elemento de volta no fluxo de entrada, então torná-lo elemento atual (apontando para o ponteiro seguinte).|
|[seekoff](#seekoff)|A função membro virtual protegida tenta alterar as posições atuais para os fluxos controlados.|
|[seekpos](#seekpos)|A função membro virtual protegida tenta alterar as posições atuais para os fluxos controlados.|
|[setbuf](#setbuf)|A função membro virtual protegida executa uma operação que específica para cada buffer de fluxo derivado.|
|[Swap](#swap)|Troca o conteúdo deste `basic_filebuf` pelo o conteúdo do parâmetro `basic_filebuf` fornecido.|
|[sync](#sync)|A função virtual protegida tenta sincronizar os fluxos controlados com quaisquer fluxos externos associados.|
|[uflow](../standard-library/basic-streambuf-class.md#uflow)|Função virtual protegida para extrair o elemento atual do fluxo de entrada.|
|[underflow](#underflow)|Função virtual protegida para extrair o elemento atual do fluxo de entrada.|

## <a name="requirements"></a>Requisitos

**Cabeçalho:** \<fstream>

**Namespace:** std

## <a name="basic_filebuf"></a>  basic_filebuf::basic_filebuf

Constrói um objeto do tipo `basic_filebuf`.

```cpp
basic_filebuf();

basic_filebuf(basic_filebuf&& right);
```

### <a name="remarks"></a>Comentários

O primeiro construtor armazena um ponteiro nulo em todos os ponteiros que controlam o buffer de entrada e o buffer de saída. Ele também armazena um ponteiro nulo no ponteiro do arquivo.

O segundo construtor inicializa o objeto com o conteúdo de `right`, tratado como uma referência rvalue.

## <a name="char_type"></a>  basic_filebuf::char_type

Associa um nome de tipo ao parâmetro de modelo `Elem`.

```cpp
typedef Elem char_type;
```

## <a name="close"></a>  basic_filebuf::close

Fecha um arquivo.

```cpp
basic_filebuf<Elem, Tr> *close();
```

### <a name="return-value"></a>Valor de retorno

A função membro retornará um ponteiro nulo se o ponteiro de arquivo for um ponteiro nulo.

### <a name="remarks"></a>Comentários

`close`chamadas `fclose`( **FP**). Se essa função retornar um valor diferente de zero, a função retornará um ponteiro nulo. Caso contrário, retornará **this** para indicar que o arquivo foi fechado com êxito.

Para um fluxo amplo, se qualquer inserções tiverem ocorrido desde que o fluxo foi aberto ou desde a última chamada a `streampos`, as chamadas de função [estourarão](#overflow). Ele também insere qualquer sequência necessária para restaurar o estado de conversão inicial, usando a faceta `fac` de conversão de arquivo para chamar `fac.unshift` conforme necessário. Cada elemento `byte` do tipo **Char** , portanto, produzido é gravado no fluxo associado designado pelo ponteiro `fp` do arquivo como se fosse sucessivas chamadas do formulário `fputc`( **byte**, **FP**). Se a chamada para `fac.unshift` ou qualquer gravação falhar, a função não terá êxito.

### <a name="example"></a>Exemplo

A amostra a seguir assume dois arquivos no diretório atual: basic_filebuf_close.txt (o conteúdo é "teste") e iotest.txt (o conteúdo é "ssss").

```cpp
// basic_filebuf_close.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main() {
   using namespace std;
   ifstream file;
   basic_ifstream <wchar_t> wfile;
   char c;
   // Open and close with a basic_filebuf
   file.rdbuf()->open( "basic_filebuf_close.txt", ios::in );
   file >> c;
   cout << c << endl;
   file.rdbuf( )->close( );

   // Open/close directly
   file.open( "iotest.txt" );
   file >> c;
   cout << c << endl;
   file.close( );

   // open a file with a wide character name
   wfile.open( L"iotest.txt" );

   // Open and close a nonexistent with a basic_filebuf
   file.rdbuf()->open( "ziotest.txt", ios::in );
   cout << file.fail() << endl;
   file.rdbuf( )->close( );

   // Open/close directly
   file.open( "ziotest.txt" );
   cout << file.fail() << endl;
   file.close( );
}
```

```Output
t
s
0
1
```

## <a name="int_type"></a>  basic_filebuf::int_type

Torna esse tipo dentro do escopo basic_filebuf's equivalente ao tipo de mesmo nome no `Tr` escopo.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="is_open"></a>  basic_filebuf::is_open

Indica se um arquivo está aberto.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Valor de retorno

**true** se o ponteiro do arquivo não for um ponteiro nulo.

### <a name="example"></a>Exemplo

```cpp
// basic_filebuf_is_open.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;
   ifstream file;
   cout << boolalpha << file.rdbuf( )->is_open( ) << endl;

   file.open( "basic_filebuf_is_open.cpp" );
   cout << file.rdbuf( )->is_open( ) << endl;
}
```

```Output
false
true
```

## <a name="off_type"></a>  basic_filebuf::off_type

Torna esse tipo dentro do escopo basic_filebuf's equivalente ao tipo de mesmo nome no `Tr` escopo.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="open"></a>  basic_filebuf::open

Abre um arquivo.

```cpp
basic_filebuf<Elem, Tr> *open(
    const char* _Filename,
    ios_base::openmode _Mode,
    int _Prot = (int)ios_base::_Openprot);

basic_filebuf<Elem, Tr> *open(
    const char* _Filename,
    ios_base::openmode _Mode);

basic_filebuf<Elem, Tr> *open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode,
    int _Prot = (int)ios_base::_Openprot);

basic_filebuf<Elem, Tr> *open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode);
```

### <a name="parameters"></a>Parâmetros

*_Filename*\
O nome do arquivo a ser aberto.

*_Mode*\
Uma das enumerações em [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
O arquivo padrão que abre a proteção, equivalente ao parâmetro *shflag* em [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="return-value"></a>Valor de retorno

Se o ponteiro do arquivo for um ponteiro nulo, a função retornará um ponteiro nulo. Caso contrário, retornará **this**.

### <a name="remarks"></a>Comentários

A função membro abre o arquivo com o nome do arquivo *filename*, chamando [fopen](../c-runtime-library/reference/fopen-wfopen.md)( *filename*, **strmode**). `strmode`é determinado do **modo &** ~ ( [ATA](../standard-library/ios-base-class.md#openmode) & &#124; [binário](../standard-library/ios-base-class.md#openmode)):

- `ios_base::in`torna-se **"r"** (abrir arquivo existente para leitura).

- [ios_base::out](../standard-library/ios-base-class.md#fmtflags) ou **ios_base::out &#124; ios_base::trunc** se torna **"w"** (truncar o arquivo existente ou criar para gravação).

- **ios_base::out &#124; app** torna-se **"a"** (abrir arquivo existente para acrescentar todas as gravações).

- **ios_base::in &#124; ios_base::out** se torna **"r+"** (abrir arquivo existente para leitura e gravação).

- **ios_base::in &#124; ios_base::out &#124; ios_base::trunc** se torna **"w +"** (truncar o arquivo existente ou criar para leitura e gravação).

- **ios_base::in &#124; ios_base::out &#124; ios_base::app** se torna **"+"** (abrir arquivo existente para leitura e para acrescentar todas as gravações).

Se **Mode & ios_base:: Binary** for diferente de zero, a função `b` acrescentará ao `strmode` para abrir um fluxo binário em vez de um fluxo de texto. Em seguida, ele armazena o valor `fopen` retornado pelo no ponteiro `fp`do arquivo. Se **mode & ios_base::ate** for diferente de zero e o ponteiro do arquivo não for um ponteiro nulo, a função chamará `fseek`( **fp**, 0, `SEEK_END`) para posicionar o fluxo no final do arquivo. Se essa operação de posicionamento falhar, a função [](#close)chamará `fp`Close () e armazenará um ponteiro nulo no ponteiro do arquivo.

Se o ponteiro do arquivo não for um ponteiro nulo, a função determinará a faceta de conversão de arquivo: `use_facet`< `codecvt`< **Elem**, `char`, **traits_type::** [state_type](../standard-library/char-traits-struct.md#state_type)> > ( [getloc](../standard-library/basic-streambuf-class.md#getloc)), para uso por [estouro](#overflow) [negativo](#underflow) .

Se o ponteiro do arquivo for um ponteiro nulo, a função retornará um ponteiro nulo. Caso contrário, retornará **this**.

### <a name="example"></a>Exemplo

Consulte [basic_filebuf::close](#close) para ver um exemplo que usa `open`.

## <a name="op_eq"></a>  basic_filebuf::operator=

Atribua o conteúdo deste objeto de buffer de fluxo. Essa é uma atribuição de movimentação que envolve um rvalue que não deixa uma cópia.

```cpp
basic_filebuf& operator=(basic_filebuf&& right);
```

### <a name="parameters"></a>Parâmetros

*Certo*\
Uma referência rvalue para um objeto [basic_filebuf](../standard-library/basic-filebuf-class.md).

### <a name="return-value"></a>Valor de retorno

Retorna *this.

### <a name="remarks"></a>Comentários

O operador member substitui o conteúdo do objeto usando o conteúdo de *Right*, tratado como uma referência rvalue. Para obter mais informações, consulte [Declarador de referência Rvalue: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="overflow"></a>  basic_filebuf::overflow

Chamado quando um novo caractere é inserido em um buffer cheio.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Parâmetros

*_Meta*\
O caractere a ser inserido no buffer ou `traits_type::eof`.

### <a name="return-value"></a>Valor de retorno

Se a função não conseguir obter êxito, ela retornará `traits_type::eof`. Caso contrário, retornará **traits_type::** [not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Comentários

Se *_Meta* **! = traits_type::** [EOF](../standard-library/char-traits-struct.md#eof), a função de membro virtual protegida se comportará para inserir o elemento **ch = traits_type::** [to_char_type](../standard-library/char-traits-struct.md#to_char_type)( *_Meta*) no buffer de saída. Isso pode ser feito de várias maneiras:

- Se houver uma posição de gravação disponível, ela poderá armazenar o elemento na posição de gravação e incrementar o próximo ponteiro para o buffer de saída.

- Ele pode disponibilizar uma posição de gravação alocando armazenamento novo ou adicional ao buffer de saída.

- Ele pode converter qualquer saída pendente no buffer de saída, seguido por `ch`, usando a faceta `fac` de conversão de arquivo para `fac.out` chamar conforme necessário. Cada elemento `ch` do tipo *Char* , portanto, produzido é gravado no fluxo associado designado pelo ponteiro `fp` do arquivo como se fosse sucessivas chamadas do formulário `fputc`( **ch**, **FP**). Se qualquer conversão ou gravação falhar, a função não será bem-sucedida.

## <a name="pbackfail"></a>  basic_filebuf::pbackfail

Tenta colocar um elemento de volta no fluxo de entrada e torná-lo o elemento atual (apontado pelo ponteiro seguinte).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Parâmetros

*_Meta*\
O caractere a ser inserido no buffer ou `traits_type::eof`.

### <a name="return-value"></a>Valor de retorno

Se a função não conseguir obter êxito, ela retornará `traits_type::eof`. Caso contrário, retornará **traits_type::** [not_eof](../standard-library/char-traits-struct.md#not_eof)( *\_meta*).

### <a name="remarks"></a>Comentários

A função membro virtual protegida coloca um elemento de volta no buffer de entrada, então o torna o elemento atual (apontando para o ponteiro seguinte). *Se\_meta* **= = traits_type::** [EOF](../standard-library/char-traits-struct.md#eof), o elemento a ser enviado novamente será efetivamente o que já está no fluxo antes do elemento atual. Caso contrário, esse elemento será substituído por **ch = traits_type::** [to_char_type](../standard-library/char-traits-struct.md#to_char_type)( *\_meta*). A função pode colocar um elemento de volta de várias maneiras:

- Se uma posição putback estiver disponível e o elemento armazenado nesse ponto de comparação for `ch`igual a, ele poderá diminuir o ponteiro seguinte para o buffer de entrada.

- Se a função puder tornar uma `putback` posição disponível, ela poderá fazer isso, definir o próximo ponteiro para apontar para essa posição e armazená `ch` -la nessa posição.

- Se a função puder enviar um elemento por push para o fluxo de entrada, isso poderá fazer isso, por exemplo `ungetc` , chamando um elemento do tipo **Char**.

## <a name="pos_type"></a>  basic_filebuf::pos_type

Torna esse tipo dentro do escopo basic_filebuf's equivalente ao tipo de mesmo nome no `Tr` escopo.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="seekoff"></a>  basic_filebuf::seekoff

Tenta alterar as posições atuais para os fluxos controlados.

```cpp
virtual pos_type seekoff(off_type _Off,
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

Retorna a nova posição ou uma posição de fluxo inválida.

### <a name="remarks"></a>Comentários

A função de membro virtual protegida busca alterar as posições atuais para os fluxos controlados. Para um objeto da classe [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, uma posição de fluxo pode ser representada por um objeto do tipo `fpos_t`, que armazena um deslocamento e quaisquer informações de estado necessárias analisar um fluxo grande. Deslocamento zero designa o primeiro elemento do fluxo. (Um objeto do tipo [pos_type](../standard-library/basic-streambuf-class.md#pos_type) armazena a pelo menos um objeto `fpos_t`.)

Para um arquivo aberto para leitura e gravação, os fluxos de entrada e saída são posicionados em tandem. Para mudar entre a inserção e extração, chame [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff) ou [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos). Chamadas para `pubseekoff` (e, portanto, para `seekoff`) têm várias limitações para [fluxos de texto](../c-runtime-library/text-and-binary-streams.md), [fluxos binários](../c-runtime-library/text-and-binary-streams.md) e [fluxos largos](../c-runtime-library/byte-and-wide-streams.md).

Se o ponteiro `fp` do arquivo for um ponteiro nulo, a função falhará. Caso contrário, ele busca alterar a posição do fluxo chamando `fseek`( **fp**, `_Off`, `_Way`). Se essa função for bem sucedido e a `fposn` posição resultante puder ser determinada `fgetpos`chamando ( **FP**, **& fposn**), a função terá sucesso. Se a função for realizada com sucesso, ela retornará um valor `pos_type` do `fposn`tipo que contém. Caso contrário, retorna uma posição de fluxo inválida.

## <a name="seekpos"></a>  basic_filebuf::seekpos

Tenta alterar as posições atuais para os fluxos controlados.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parâmetros

*_Sp*\
A posição pela qual buscar.

*_Which*\
Especifica o modo para a posição do ponteiro. O padrão é permitir que você modifique as posições de leitura e gravação.

### <a name="return-value"></a>Valor de retorno

Se o ponteiro `fp` do arquivo for um ponteiro nulo, a função falhará. Caso contrário, ele tenta alterar a posição do `fsetpos`fluxo chamando ( **FP**, **& fposn**), em que `fposn` é o `fpos_t` objeto armazenado em. `pos` Se essa função for bem-sucedida, a função retornará `pos`. Caso contrário, retorna uma posição de fluxo inválida. Para determinar se a posição de fluxo é inválida, compare o valor retornado com `pos_type(off_type(-1))`.

### <a name="remarks"></a>Comentários

A função de membro virtual protegida busca alterar as posições atuais para os fluxos controlados. Para um objeto da classe [basic_filebuf](../standard-library/basic-filebuf-class.md)\< **Elem**, **Tr**>, uma posição de fluxo pode ser representada por um objeto do tipo `fpos_t`, que armazena um deslocamento e quaisquer informações de estado necessárias analisar um fluxo grande. Deslocamento zero designa o primeiro elemento do fluxo. (Um objeto do tipo `pos_type` armazena a pelo menos um objeto `fpos_t`.)

Para um arquivo aberto para leitura e gravação, os fluxos de entrada e saída são posicionados em tandem. Para mudar entre a inserção e extração, chame [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff) ou [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos). Chamadas para `pubseekoff` (e, portanto, para `seekoff`) têm várias limitações para fluxos de texto, fluxos binários e fluxos largos.

Para um fluxo amplo, se qualquer inserções tiverem ocorrido desde que o fluxo foi aberto ou desde a última chamada a `streampos`, as chamadas de função [estourarão](#overflow). Ele também insere qualquer sequência necessária para restaurar o estado de conversão inicial, usando a faceta `fac` de conversão de arquivo para chamar **fac** `.unshift` , conforme necessário. Cada elemento `byte` do tipo **Char** , portanto, produzido é gravado no fluxo associado designado pelo ponteiro `fp` do arquivo como se fosse sucessivas chamadas do formulário `fputc`( **byte**, **FP**). Se a chamada para `fac.unshift` ou qualquer gravação falhar, a função não terá êxito.

## <a name="setbuf"></a>  basic_filebuf::setbuf

Executa um operação específica para cada buffer de fluxo derivado.

```cpp
virtual basic_streambuf<Elem, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parâmetros

*_Buffer*\
Ponteiro para um buffer.

*contar*\
O tamanho do buffer.

### <a name="return-value"></a>Valor de retorno

A função membro protegido retornará zero se o ponteiro do arquivo `fp` for um ponteiro nulo.

### <a name="remarks"></a>Comentários

`setbuf` chama `setvbuf`( **fp**, ( `char` \*) `_Buffer`, `_IOFBF`, `count` \* `sizeof` ( **Elem**) ) para oferecer a matriz de elementos `count` começando no _ *Buffer* como um buffer para o fluxo. Se essa função retornar um valor diferente de zero, a função retornará um ponteiro nulo. Caso contrário, retornará **this** para indicar o sucesso.

## <a name="swap"></a>  basic_filebuf::swap

Troca o conteúdo desse `basic_filebuf` pelo conteúdo do `basic_filebuf` fornecido.

```cpp
void swap(basic_filebuf& right);
```

### <a name="parameters"></a>Parâmetros

*Certo*\
Um `lvalue` referência a outro `basic_filebuf`.

## <a name="sync"></a>  basic_filebuf::sync

Tenta sincronizar os fluxos controlados com quaisquer fluxos externos associados.

```cpp
virtual int sync();
```

### <a name="return-value"></a>Valor de retorno

Retornará zero se o ponteiro `fp` do arquivo for um ponteiro nulo. Caso contrário, retornará zero somente se chamadas tanto para [overflow](#overflow) quanto para `fflush`( **fp**) obtiverem sucesso em liberar qualquer saída para o fluxo.

## <a name="traits_type"></a>  basic_filebuf::traits_type

Associa um nome de tipo ao parâmetro de modelo `Tr`.

```cpp
typedef Tr traits_type;
```

## <a name="underflow"></a>  basic_filebuf::underflow

Extrai o elemento atual do fluxo de entrada.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Valor de retorno

Se a função não conseguir obter êxito, ela retornará **traits_type::** [eof](../standard-library/char-traits-struct.md#eof). Caso contrário, ele `ch`retorna, convertido conforme descrito na seção comentários.

### <a name="remarks"></a>Comentários

A função de membro virtual protegida tem o esforço de extrair o `ch` elemento atual do fluxo de entrada e retornar o elemento como **traits_type::** [to_int_type](../standard-library/char-traits-struct.md#to_int_type)(`ch`). Isso pode ser feito de várias maneiras:

- Se uma posição de leitura estiver disponível, ela `ch` será aceita como o elemento armazenado na posição de leitura e avança o próximo ponteiro para o buffer de entrada.

- Ele pode ler um ou mais elementos do tipo **Char**, como se houvesse sucessivas chamadas do formulário `fgetc`(**FP**) e convertê-los em um elemento **ch** do `Elem` tipo usando a faceta de conversão de arquivo fac `fac.in` para chamar conforme necessário. Se qualquer leitura ou conversão falhar, a função não será bem-sucedida.

## <a name="see-also"></a>Consulte também

[\<fstream>](../standard-library/fstream.md)\
[Acesso Thread-Safe na Biblioteca Padrão C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programação de iostream](../standard-library/iostream-programming.md)\
[Convenções de iostreams](../standard-library/iostreams-conventions.md)
