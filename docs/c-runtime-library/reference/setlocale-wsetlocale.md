---
title: setlocale, _wsetlocale
ms.date: 11/04/2016
apiname:
- _wsetlocale
- setlocale
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wsetlocale
- _tsetlocale
- setlocale
helpviewer_keywords:
- wsetlocale function
- setlocale function
- tsetlocale function
- locales, defining
- _tsetlocale function
- defining locales
- _wsetlocale function
ms.assetid: 3ffb684e-5990-4202-9553-b5339af9520d
ms.openlocfilehash: 6c9f44e9619b9c34c9424e0be78186d14f2d6a21
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327129"
---
# <a name="setlocale-wsetlocale"></a>setlocale, _wsetlocale

Define ou recupera a localidade do tempo de execução.

## <a name="syntax"></a>Sintaxe

```C
char *setlocale(
   int category,
   const char *locale
);
wchar_t *_wsetlocale(
   int category,
   const wchar_t *locale
);
```

### <a name="parameters"></a>Parâmetros

*category*<br/>
Categoria afetada pela localidade.

*locale*<br/>
Especificador de localidade.

## <a name="return-value"></a>Valor de retorno

Se for um válida *localidade* e *categoria* forem fornecidos, retornará um ponteiro para a cadeia de caracteres associada especificada *localidade* e *categoria*. Se o *localidade* ou *categoria* não é válido, retorna um ponteiro nulo e as configurações de localidade atual do programa não são alteradas.

Por exemplo, a chamada

```C
setlocale( LC_ALL, "en-US" );
```

define todas as categorias, retornando apenas a cadeia de caracteres

```Output
en-US
```

Você pode copiar a cadeia de caracteres retornada por **setlocale** para restaurar essa parte das informações de localidade do programa. Armazenamento local global ou de thread é usado para a cadeia de caracteres retornada por **setlocale**. Chamadas posteriores para **setlocale** substituir a cadeia de caracteres, o que invalida os ponteiros de cadeia de caracteres retornados pelas chamadas anteriores.

## <a name="remarks"></a>Comentários

Use o **setlocale** função para definir, alterar ou consultar algumas ou todas as informações de localidade atual do programa especificadas por *localidade* e *categoria*. *localidade* refere-se à localidade (país/região e idioma) para o qual você pode personalizar determinados aspectos do seu programa. Algumas categorias de localidade dependentes incluem a formatação de datas e o formato de exibição de valores monetários. Se você definir *localidade* à cadeia de caracteres padrão para um idioma que tenha várias formas com suporte no seu computador, você deve verificar as **setlocale** retornar o valor para ver qual linguagem está em vigor. Por exemplo, se você definir *localidade* "chinês" o valor de retorno pode ser "chinês simplificado" ou "chinês-tradicional".

**wsetlocale** é uma versão de caractere largo de **setlocale**; o *localidade* argumento e o valor retornado de **wsetlocale** são cadeias de caracteres largos. **wsetlocale** e **setlocale** se comportam de forma idêntica caso contrário.

### <a name="generic-text-routine-mappings"></a>Mapeamentos da rotina de texto genérico

|Rotina TCHAR.H|_UNICODE e _MBCS não definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**tsetlocale**|**setlocale**|**setlocale**|**_wsetlocale**|

O *categoria* argumento especifica as partes das informações de localidade de um programa que são afetadas. As macros usadas para *categoria* e as partes do programa que afetam são da seguinte maneira:

|*categoria* sinalizador|Afeta|
|-|-|
| **LC_ALL** | Todas as categorias, conforme listado abaixo. |
| **LC_COLLATE** | O **strcoll**, **stricoll**, **wcscoll**, **wcsicoll**, **strxfrm**, **_ strncoll**, **strnicoll**, **wcsncoll**, **wcsnicoll**, e **wcsxfrm** funções. |
| **LC_CTYPE** | As funções de manipulação de caracteres (exceto **isdigit**, **isxdigit**, **mbstowcs**, e **mbtowc**, que não são afetadas). |
| **LC_MONETARY** | Informações de formatação monetária retornadas pela **localeconv** função. |
| **LC_NUMERIC** | Caractere decimal para rotinas de saída formatadas (como **printf**), para as rotinas de conversão de dados e para as informações de formatação não-monetária retornadas pela **localeconv**. Além do caractere de vírgula decimal **LC_NUMERIC** separador de milhares de conjuntos e o agrupamento de controle de cadeia de caracteres retornada pela [localeconv](localeconv.md). |
| **LC_TIME** | O **strftime** e **wcsftime** funções. |

Essa função valida o parâmetro category. Se o parâmetro category não for um dos valores fornecidos na tabela anterior, o manipulador de parâmetro inválido será chamado, conforme descrito em [Validação de Parâmetro](../../c-runtime-library/parameter-validation.md). Se a execução puder continuar, a função definirá **errno** à **EINVAL** e retorna **nulo**.

O *localidade* argumento é um ponteiro para uma cadeia de caracteres que especifica a localidade. Para obter informações sobre o formato do *localidade* argumento, consulte [nomes de localidades, idiomas e cadeias de caracteres de país/região](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Se *locale* apontar para uma cadeia de caracteres vazia, a localidade será o ambiente nativo definido pela implementação. Um valor de **C** Especifica o ambiente em conformidade mínima com ANSI para conversão em C. O **C** localidade pressupõe que todos os **char** tipos de dados são de 1 byte e seu valor é sempre menor que 256.

Na inicialização do programa, o equivalente da instrução a seguir é executado:

`setlocale( LC_ALL, "C" );`

O *localidade* argumento pode assumir um nome de localidade, uma cadeia de caracteres de idioma, uma cadeia de caracteres de idioma e código de país/região, uma página de código, ou uma cadeia de caracteres de idioma, o código de país/região e página de código. O conjunto disponível de nomes de localidade, idiomas, códigos de país/região e páginas de código inclui tudo o que é suportado pela API NLS do Windows, exceto as páginas de código que exigem mais de dois bytes por caractere, como UTF-7 e UTF-8. Se você fornecer um valor de página de código de UTF-7 ou UTF-8 **setlocale** falhará, retornando **nulo**. O conjunto de nomes de localidades com suporte pelo **setlocale** descritos nos [nomes de localidades, idiomas e cadeias de caracteres de país/região](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). O conjunto de cadeias de caracteres de idioma e país/região com suporte pelo **setlocale** são listadas na [cadeias de caracteres de idioma](../../c-runtime-library/language-strings.md) e [cadeias de caracteres de país/região](../../c-runtime-library/country-region-strings.md). Recomendamos o formato do nome da localidade para o desempenho e a capacidade de manutenção de cadeias de caracteres de localidade inseridas no código ou serializadas para armazenamento. As cadeias de caracteres de nome da localidade são menos prováveis de ser alteradas por uma atualização do sistema operacional do que o formato de idioma e país/região.

Um ponteiro nulo que é passado como o *localidade* argumento informa **setlocale** consultar em vez de definir o ambiente internacional. Se o *localidade* argumento for um ponteiro nulo, a configuração de localidade atual do programa não é alterada. Em vez disso, **setlocale** retorna um ponteiro para a cadeia de caracteres que está associada com o *categoria* da localidade do thread atual. Se o *categoria* argumento é **LC_ALL**, a função retorna uma cadeia de caracteres que indica a configuração atual de cada categoria, separada por ponto e vírgula. Por exemplo, a sequência de chamadas

```C
// Set all categories and return "en-US"
setlocale(LC_ALL, "en-US");
// Set only the LC_MONETARY category and return "fr-FR"
setlocale(LC_MONETARY, "fr-FR");
printf("%s\n", setlocale(LC_ALL, NULL));
```

retorna

```Output
LC_COLLATE=en-US;LC_CTYPE=en-US;LC_MONETARY=fr-FR;LC_NUMERIC=en-US;LC_TIME=en-US
```

qual é a cadeia de caracteres que está associada com o **LC_ALL** categoria.

Os exemplos a seguir referem-se para o **LC_ALL** categoria. Qualquer uma das cadeias de caracteres “.OCP” e “.ACP” pode ser usada em vez de um número de página de código para especificar o uso da página de código OEM do usuário padrão e da página de código ANSI padrão do usuário, respectivamente.

- `setlocale( LC_ALL, "" );`

   Define a localidade para o padrão, que é a página de código ANSI padrão do usuário obtida do sistema operacional.

- `setlocale( LC_ALL, ".OCP" );`

   Define explicitamente a localidade para a página de código OEM obtida do sistema operacional.

- `setlocale( LC_ALL, ".ACP" );`

   Define a localidade para a página de código ANSI obtida do sistema operacional.

- `setlocale( LC_ALL, "<localename>" );`

   Define a localidade para o nome da localidade que é indicado por *\<localename>*.

- `setlocale( LC_ALL, "<language>_<country>" );`

   Define a localidade para o idioma e o país/região indicados por *\<language>* e *\<country>*, juntamente com a página de código padrão obtida do sistema operacional do host.

- `setlocale( LC_ALL, "<language>_<country>.<code_page>" );`

   Define a localidade para o idioma, país/região e página de código indicada pela  *\<language >*,  *\<país >*, e  *\<code_page >* cadeias de caracteres. Você pode usar várias combinações de idioma, país/região e página de código. Por exemplo, esta chamada define a localidade para francês canadense com a página de código 1252:

   `setlocale( LC_ALL, "French_Canada.1252" );`

   Esta chamada define a localidade para francês canadense com a página de código ANSI padrão:

   `setlocale( LC_ALL, "French_Canada.ACP" );`

   Esta chamada define a localidade para francês canadense com a página de código OEM padrão:

   `setlocale( LC_ALL, "French_Canada.OCP" );`

- `setlocale( LC_ALL, "<language>" );`

   Define a localidade para o idioma que é indicado por *\<language>* e usa o país/região padrão para o idioma especificado e a página de código ANSI padrão do usuário para esse país/região conforme obtidos do sistema operacional do host. Por exemplo, as seguintes chamadas para **setlocale** são funcionalmente equivalentes:

   `setlocale( LC_ALL, "en-US" );`

   `setlocale( LC_ALL, "English" );`

   `setlocale( LC_ALL, "English_United States.1252" );`

   Recomendamos o primeiro formato para o desempenho e a capacidade de manutenção.

- `setlocale( LC_ALL, ".<code_page>" );`

   Define a página de código para o valor indicado por *<code_page>*, juntamente com o país/região e o idioma padrão (conforme definidos pelo sistema operacional do host) para a página de código especificada.

A categoria deve ser **LC_ALL** ou **LC_CTYPE** para fazer uma alteração da página de código. Por exemplo, se o país/região padrão e o idioma do sistema operacional do host forem "Estados Unidos" e "Inglês", estas duas chamadas para **setlocale** são funcionalmente equivalentes:

`setlocale( LC_ALL, ".1252" );`

`setlocale( LC_ALL, "English_United States.1252");`

Para obter mais informações, consulte a diretiva de pragma [setlocale](../../preprocessor/setlocale.md) na [Referência de pré-processador C/C++](../../preprocessor/c-cpp-preprocessor-reference.md).

A função [configthreadlocale](configthreadlocale.md) é usada para controlar se **setlocale** afeta a localidade de todos os threads em um programa ou somente a localidade do thread de chamada.

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**setlocale**|\<locale.h>|
|**_wsetlocale**|\<locale.h> ou \<wchar.h>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

```C
// crt_setlocale.c
//
// This program demonstrates the use of setlocale when
// using two independent threads.
//

#include <locale.h>
#include <process.h>
#include <windows.h>
#include <stdio.h>
#include <time.h>

#define BUFF_SIZE 100

// Retrieve the date in the current
// locale's format.
int get_date(unsigned char* str)
{
    __time64_t ltime;
    struct tm  thetime;

    // Retrieve the current time
    _time64(&ltime);
    _gmtime64_s(&thetime, &ltime);

    // Format the current time structure into a string
    // "%#x" is the long date representation in the
    // current locale
    if (!strftime((char *)str, BUFF_SIZE, "%#x",
                  (const struct tm *)&thetime))
    {
        printf("strftime failed!\n");
        return -1;
    }
    return 0;
}

// This thread sets its locale to the argument
// and prints the date.
uintptr_t __stdcall SecondThreadFunc( void* pArguments )
{
    unsigned char str[BUFF_SIZE];
    char * locale = (char *)pArguments;

    // Set the thread locale
    printf("The thread locale is now set to %s.\n",
           setlocale(LC_ALL, locale));

    // Retrieve the date string from the helper function
    if (get_date(str) == 0)
    {
        printf("The date in %s locale is: '%s'\n", locale, str);
    }

    _endthreadex( 0 );
    return 0;
}

// The main thread sets the locale to English
// and then spawns a second thread (above) and prints the date.
int main()
{
    HANDLE          hThread;
    unsigned        threadID;
    unsigned char   str[BUFF_SIZE];

    // Configure per-thread locale to cause all subsequently created
    // threads to have their own locale.
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);

    // Set the locale of the main thread to US English.
    printf("The thread locale is now set to %s.\n",
           setlocale(LC_ALL, "en-US"));

    // Create the second thread with a German locale.
    // Our thread function takes an argument of the locale to use.
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc,
                                      "de-DE", 0, &threadID );

    if (get_date(str) == 0)
    {
        // Retrieve the date string from the helper function
        printf("The date in en-US locale is: '%s'\n\n", str);
    }

    // Wait for the created thread to finish.
    WaitForSingleObject( hThread, INFINITE );

    // Destroy the thread object.
    CloseHandle( hThread );
}
```

```Output
The thread locale is now set to en-US.
The time in en-US locale is: 'Wednesday, May 12, 2004'

The thread locale is now set to de-DE.
The time in de-DE locale is: 'Mittwoch, 12. Mai 2004'
```

## <a name="see-also"></a>Consulte também

[Nomes de localidades, idiomas e cadeias de caracteres de país/região](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[_configthreadlocale](configthreadlocale.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[Localidade](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[Funções strcoll](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
