---
title: Um programa de texto genérico de exemplo
ms.date: 11/04/2016
helpviewer_keywords:
- _TCHAR type
- mappings, TCHAR.H data types
- generic-text example [CRT]
- TCHAR type
- TCHAR.H data types, mapping
ms.assetid: a03de0db-8118-4bd9-a03f-640e8dfc5ed3
ms.openlocfilehash: 768d0ef2ac3dc2b407ea3725ebeaede307c98302
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490461"
---
# <a name="a-sample-generic-text-program"></a>Um programa de texto genérico de exemplo

**Seção específica da Microsoft**

O programa a seguir, GENTEXT. C, fornece uma ilustração mais detalhada do uso de mapeamentos de texto genéricos definidos em TCHAR.H:

```C
// GENTEXT.C
// use of generic-text mappings defined in TCHAR.H

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <direct.h>
#include <errno.h>
#include <tchar.h>

int __cdecl _tmain(int argc, _TCHAR **argv, _TCHAR **envp)
{
   _TCHAR buff[_MAX_PATH];
   _TCHAR *str = _T("Astring");
   char *amsg = "Reversed";
   wchar_t *wmsg = L"Is";

#ifdef _UNICODE
   printf("Unicode version\n");
#else /* _UNICODE */
#ifdef _MBCS
   printf("MBCS version\n");
#else
   printf("SBCS version\n");
#endif
#endif /* _UNICODE */

   if (_tgetcwd(buff, _MAX_PATH) == NULL)
       printf("Can't Get Current Directory - errno=%d\n", errno);
   else
       _tprintf(_T("Current Directory is '%s'\n"), buff);
   _tprintf(_T("'%s' %hs %ls:\n"), str, amsg, wmsg);
   _tprintf(_T("'%s'\n"), _tcsrev(_tcsdup(str)));
   return 0;
}
```

Se `_MBCS` tiver sido definido, GENTEXT.C será mapeado para o programa MBCS a seguir:

```C
// crt_mbcsgtxt.c

/*
 * Use of generic-text mappings defined in TCHAR.H
 * Generic-Text-Mapping example program
 * MBCS version of GENTEXT.C
 */

#include <stdio.h>
#include <stdlib.h>
#include <mbstring.h>
#include <direct.h>

int __cdecl main(int argc, char **argv, char **envp)
{
   char buff[_MAX_PATH];
   char *str = "Astring";
   char *amsg = "Reversed";
   wchar_t *wmsg = L"Is";

   printf("MBCS version\n");

   if (_getcwd(buff, _MAX_PATH) == NULL) {
       printf("Can't Get Current Directory - errno=%d\n", errno);
   }
   else {
       printf("Current Directory is '%s'\n", buff);
   }

   printf("'%s' %hs %ls:\n", str, amsg, wmsg);
   printf("'%s'\n", _mbsrev(_mbsdup((unsigned char*) str)));
   return 0;
}
```

Se `_UNICODE` tiver sido definido, GENTEXT.C será mapeado para a seguinte versão Unicode do programa. Para obter mais informações sobre como usar o `wmain` em programas Unicode como uma substituição para `main`, consulte [Usando wmain](../c-language/using-wmain.md) na *Referência da linguagem C*.

```C
// crt_unicgtxt.c

/*
 * Use of generic-text mappings defined in TCHAR.H
 * Generic-Text-Mapping example program
 * Unicode version of GENTEXT.C
 */

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <direct.h>

int __cdecl wmain(int argc, wchar_t **argv, wchar_t **envp)
{
   wchar_t buff[_MAX_PATH];
   wchar_t *str = L"Astring";
   char *amsg = "Reversed";
   wchar_t *wmsg = L"Is";

   printf("Unicode version\n");

   if (_wgetcwd(buff, _MAX_PATH) == NULL) {
      printf("Can't Get Current Directory - errno=%d\n", errno);
   }
   else {
       wprintf(L"Current Directory is '%s'\n", buff);
   }

   wprintf(L"'%s' %hs %ls:\n", str, amsg, wmsg);
   wprintf(L"'%s'\n", wcsrev(wcsdup(str)));
   return 0;
}
```

Se nem `_MBCS` nem `_UNICODE` tiver sido definido, GENTEXT.C mapeará para o código ASCII de um byte da seguinte maneira:

```C
// crt_sbcsgtxt.c
/*
 * Use of generic-text mappings defined in TCHAR.H
 * Generic-Text-Mapping example program
 * Single-byte (SBCS) Ascii version of GENTEXT.C
 */

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <direct.h>

int __cdecl main(int argc, char **argv, char **envp)
{
   char buff[_MAX_PATH];
   char *str = "Astring";
   char *amsg = "Reversed";
   wchar_t *wmsg = L"Is";

   printf("SBCS version\n");

   if (_getcwd(buff, _MAX_PATH) == NULL) {
       printf("Can't Get Current Directory - errno=%d\n", errno);
   }
   else {
       printf("Current Directory is '%s'\n", buff);
   }

   printf("'%s' %hs %ls:\n", str, amsg, wmsg);
   printf("'%s'\n", strrev(strdup(str)));
   return 0;
}
```

**Fim da seção específica da Microsoft**

## <a name="see-also"></a>Consulte também

[Mapeamentos de texto genérico](../c-runtime-library/generic-text-mappings.md)<br/>
[Mapeamentos de tipo de dados](../c-runtime-library/data-type-mappings.md)<br/>
[Mapeamentos de constante e variável global](../c-runtime-library/constant-and-global-variable-mappings.md)<br/>
[Mapeamentos de rotina](../c-runtime-library/routine-mappings.md)<br/>
[Usando mapeamentos de texto genérico](../c-runtime-library/using-generic-text-mappings.md)