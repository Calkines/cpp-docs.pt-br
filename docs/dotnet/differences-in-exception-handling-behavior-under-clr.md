---
title: Diferenças no comportamento de tratamento de exceções em-CLR
ms.date: 11/04/2016
helpviewer_keywords:
- EXCEPTION_CONTINUE_EXECUTION macro
- set_se_translator function
ms.assetid: 2e7e8daf-d019-44b0-a51c-62d7aaa89104
ms.openlocfilehash: b84c51bc6adbb4fd879aadbca2856887e51fc401
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "70311633"
---
# <a name="differences-in-exception-handling-behavior-under-clr"></a>Diferenças no comportamento do tratamento de exceções em /CLR

[Conceitos básicos no uso de exceções gerenciadas](../dotnet/basic-concepts-in-using-managed-exceptions.md) discute o tratamento de exceções em aplicativos gerenciados. Neste tópico, as diferenças do comportamento padrão de manipulação de exceção e algumas restrições são discutidas em detalhes. Para obter mais informações, consulte [a função _set_se_translator](../c-runtime-library/reference/set-se-translator.md).

##  <a name="vcconjumpingoutofafinallyblock"></a>Pulando para fora de um bloco finally

No C/C++ Code nativo, é permitido sair de um bloco _**finally por** meio de SEH (manipulação de exceção estruturada), embora ele produza um aviso.  Em [/CLR](../build/reference/clr-common-language-runtime-compilation.md), saltar de um bloco **finally** causa um erro:

```cpp
// clr_exception_handling_4.cpp
// compile with: /clr
int main() {
   try {}
   finally {
      return 0;   // also fails with goto, break, continue
    }
}   // C3276
```

##  <a name="vcconraisingexceptionswithinanexceptionfilter"></a>Gerando exceções dentro de um filtro de exceção

Quando uma exceção é gerada durante o processamento de um [filtro de exceção](../cpp/writing-an-exception-filter.md) dentro do código gerenciado, a exceção é capturada e tratada como se o filtro retorne 0.

Isso está em contraste com o comportamento no código nativo em que uma exceção aninhada é gerada, o campo **ExceptionRecord** na estrutura **EXCEPTION_RECORD** (conforme retornado por [GetExceptionInformation](/windows/win32/Debug/getexceptioninformation)) é definido e o **ExceptionFlags** campo define o bit 0x10. O exemplo a seguir ilustra essa diferença no comportamento:

```cpp
// clr_exception_handling_5.cpp
#include <windows.h>
#include <stdio.h>
#include <assert.h>

#ifndef false
#define false 0
#endif

int *p;

int filter(PEXCEPTION_POINTERS ExceptionPointers) {
   PEXCEPTION_RECORD ExceptionRecord =
                     ExceptionPointers->ExceptionRecord;

   if ((ExceptionRecord->ExceptionFlags & 0x10) == 0) {
      // not a nested exception, throw one
      *p = 0; // throw another AV
   }
   else {
      printf("Caught a nested exception\n");
      return 1;
    }

   assert(false);

   return 0;
}

void f(void) {
   __try {
      *p = 0;   // throw an AV
   }
   __except(filter(GetExceptionInformation())) {
      printf_s("We should execute this handler if "
                 "compiled to native\n");
    }
}

int main() {
   __try {
      f();
   }
   __except(1) {
      printf_s("The handler in main caught the "
               "exception\n");
    }
}
```

### <a name="output"></a>Saída

```Output
Caught a nested exception
We should execute this handler if compiled to native
```

##  <a name="vccondisassociatedrethrows"></a>Relançações desassociadas

o **/CLR** não dá suporte à regeração de uma exceção fora de um manipulador catch (conhecido como uma Rethrow não associada). Exceções desse tipo são tratadas como um relançamento padrão C++ . Se uma regeração desassociada for encontrada quando houver uma exceção gerenciada ativa, a exceção será encapsulada como C++ uma exceção e, em seguida, relançada. Exceções desse tipo só podem ser capturadas como uma exceção do tipo <xref:System.Runtime.InteropServices.SEHException>.

O exemplo a seguir demonstra uma exceção gerenciada relançada C++ como uma exceção:

```cpp
// clr_exception_handling_6.cpp
// compile with: /clr
using namespace System;
#include <assert.h>
#include <stdio.h>

void rethrow( void ) {
   // This rethrow is a dissasociated rethrow.
   // The exception would be masked as SEHException.
   throw;
}

int main() {
   try {
      try {
         throw gcnew ApplicationException;
      }
      catch ( ApplicationException^ ) {
         rethrow();
         // If the call to rethrow() is replaced with
         // a throw statement within the catch handler,
         // the rethrow would be a managed rethrow and
         // the exception type would remain
         // System::ApplicationException
      }
   }

    catch ( ApplicationException^ ) {
      assert( false );

      // This will not be executed since the exception
      // will be masked as SEHException.
    }
   catch ( Runtime::InteropServices::SEHException^ ) {
      printf_s("caught an SEH Exception\n" );
    }
}
```

### <a name="output"></a>Saída

```Output
caught an SEH Exception
```

##  <a name="vcconexceptionfiltersandexception_continue_execution"></a>Filtros de exceção e EXCEPTION_CONTINUE_EXECUTION

Se um filtro retornar `EXCEPTION_CONTINUE_EXECUTION` em um aplicativo gerenciado, ele será tratado como se o filtro fosse `EXCEPTION_CONTINUE_SEARCH`retornado. Para obter mais informações sobre essas constantes, consulte [instrução try-Except](../cpp/try-except-statement.md).

O exemplo a seguir demonstra essa diferença:

```cpp
// clr_exception_handling_7.cpp
#include <windows.h>
#include <stdio.h>
#include <assert.h>

int main() {
   int Counter = 0;
   __try {
      __try  {
         Counter -= 1;
         RaiseException (0xe0000000|'seh',
                         0, 0, 0);
         Counter -= 2;
      }
      __except (Counter) {
         // Counter is negative,
         // indicating "CONTINUE EXECUTE"
         Counter -= 1;
      }
    }
    __except(1) {
      Counter -= 100;
   }

   printf_s("Counter=%d\n", Counter);
}
```

### <a name="output"></a>Saída

```Output
Counter=-3
```

##  <a name="vcconthe_set_se_translatorfunction"></a>A função _set_se_translator

A função tradutor, definida por uma chamada para `_set_se_translator`, afeta apenas o código não gerenciado. O exemplo a seguir demonstra essa limitação:

```cpp
// clr_exception_handling_8.cpp
// compile with: /clr /EHa
#include <iostream>
#include <windows.h>
#include <eh.h>
#pragma warning (disable: 4101)
using namespace std;
using namespace System;

#define MYEXCEPTION_CODE 0xe0000101

class CMyException {
public:
   unsigned int m_ErrorCode;
   EXCEPTION_POINTERS * m_pExp;

   CMyException() : m_ErrorCode( 0 ), m_pExp( NULL ) {}

   CMyException( unsigned int i, EXCEPTION_POINTERS * pExp )
         : m_ErrorCode( i ), m_pExp( pExp ) {}

   CMyException( CMyException& c ) : m_ErrorCode( c.m_ErrorCode ),
                                      m_pExp( c.m_pExp ) {}

   friend ostream& operator <<
                 ( ostream& out, const CMyException& inst ) {
      return out <<  "CMyException[\n" <<
             "Error Code: " << inst.m_ErrorCode <<  "]";
    }
};

#pragma unmanaged
void my_trans_func( unsigned int u, PEXCEPTION_POINTERS pExp ) {
   cout <<  "In my_trans_func.\n";
   throw CMyException( u, pExp );
}

#pragma managed
void managed_func() {
   try  {
      RaiseException( MYEXCEPTION_CODE, 0, 0, 0 );
   }
   catch ( CMyException x ) {}
   catch ( ... ) {
      printf_s("This is invoked since "
               "_set_se_translator is not "
               "supported when /clr is used\n" );
    }
}

#pragma unmanaged
void unmanaged_func() {
   try  {
      RaiseException( MYEXCEPTION_CODE,
                      0, 0, 0 );
   }
   catch ( CMyException x ) {
      printf("Caught an SEH exception with "
             "exception code: %x\n", x.m_ErrorCode );
    }
    catch ( ... ) {}
}

// #pragma managed
int main( int argc, char ** argv ) {
   _set_se_translator( my_trans_func );

   // It does not matter whether the translator function
   // is registered in managed or unmanaged code
   managed_func();
   unmanaged_func();
}
```

### <a name="output"></a>Saída

```Output
This is invoked since _set_se_translator is not supported when /clr is used
In my_trans_func.
Caught an SEH exception with exception code: e0000101
```

## <a name="see-also"></a>Consulte também

[Tratamento de Exceção](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[Tratamento de Exceção](../cpp/exception-handling-in-visual-cpp.md)
