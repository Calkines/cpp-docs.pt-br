---
title: Outros Manipuladores de Fluxo de Saída de um Argumento
ms.date: 11/04/2016
helpviewer_keywords:
- output streams, one-argument manipulators
ms.assetid: e381dee8-6b16-4cef-805a-4a6a1d2b696b
ms.openlocfilehash: c9e9e7531733ac40022b477980297c80ac488221
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453442"
---
# <a name="other-one-argument-output-stream-manipulators"></a>Outros Manipuladores de Fluxo de Saída de um Argumento

O exemplo a seguir usa uma `money`classe, que é um tipo **longo** . O manipulador `setpic` anexa uma cadeia de caracteres de “imagem” de formatação à classe que pode ser usada pelo operador de inserção de fluxo sobrecarregado da classe `money`. A cadeia de caracteres de imagem é armazenada como uma variável estática na classe `money` em vez de como membro de dados de uma classe de fluxo, portanto não é necessário derivar uma nova classe de fluxo de saída.

## <a name="example"></a>Exemplo

```cpp
// one_arg_output.cpp
// compile with: /GR /EHsc
#include <iostream>
#include <iomanip>
#include <string>
using namespace std;

typedef char* charp;

class money
{
private:
    long value;
    static char *szCurrentPic;
public:
    money( long val ) { value = val; }
    friend ostream& operator << ( ostream& os, money m ) {
        // A more complete function would merge the picture
        // with the value rather than simply appending it
        os << m.value << '[' << money::szCurrentPic << ']';
        return os;
    }
    static void setpic( char* szPic ) {
        money::szCurrentPic = new char[strlen( szPic ) + 1];
        strcpy_s( money::szCurrentPic, strlen( szPic ) + 1, szPic );
    }
};

char *money::szCurrentPic;  // Static pointer to picture

void fb( ios_base& os, char * somename )
{
   money::setpic(somename);
/*
   ostream *pos = dynamic_cast<ostream*>(&os);
   if (pos)
   {
      for( int i=0; i < l; i++ )
      (*pos) << ' ';
   };
*/
}

_Smanip<charp>
   __cdecl setpic(char * somename)
   {
   return (_Smanip<charp>(&fb, somename));
   }

int main( )
{
    money amt = (long)35235.22;
    cout << setiosflags( ios::fixed );
    cout << setpic( "###,###,###.##" ) << "amount = " << amt << endl;
}
```

## <a name="see-also"></a>Consulte também

[Manipuladores personalizados com argumentos](../standard-library/custom-manipulators-with-arguments.md)
