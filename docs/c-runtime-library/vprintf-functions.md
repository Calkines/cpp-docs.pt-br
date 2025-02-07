---
title: Funções vprintf
ms.date: 11/04/2016
api_location:
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- vprintf
helpviewer_keywords:
- vprintf function
- formatted text [C++]
ms.assetid: 02ac7c51-eab1-4bf0-bf4c-77065e3fa744
ms.openlocfilehash: 3c04879c7ec90aaba1199264c0c2128b9d1ea27c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957231"
---
# <a name="vprintf-functions"></a>Funções vprintf

Cada uma das funções do `vprintf` usa um ponteiro para uma lista de argumentos e então formata e grava os dados determinados em um destino em particular. As funções diferem na validação de parâmetro executada, se as funções obtêm cadeias de caracteres com caracteres largos e de byte único, o destino de saída e o suporte para a especificação na qual os parâmetros são usados na cadeia de caracteres de formatação.

|||
|-|-|
|[_vcprintf, _vcwprintf](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md)|[vfprintf, vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|
|[_vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)|[vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|
|[vprintf, vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[_vprintf_p, _vprintf_p_l, _vwprintf_p, _vwprintf_p_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)|
|[vprintf_s, _vprintf_s_l, vwprintf_s, _vwprintf_s_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|[vsprintf, vswprintf](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|
|[_vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|[vsprintf_s, _vsprintf_s_l, vswprintf_s, _vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|
|[_vscprintf, _vscprintf_l, _vscwprintf, _vscwprintf_l](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|[_vsnprintf, _vsnwprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)|

## <a name="remarks"></a>Comentários

As funções `vprintf` são semelhantes às funções correspondentes, conforme listado na tabela a seguir. No entanto, cada função `vprintf` aceita um ponteiro para uma lista de argumentos, enquanto cada uma das funções equivalentes aceita uma lista de argumentos.

Essas funções formatam os dados de saída para destinos como os seguintes.

|Função|Função equivalente|Destino de saída|Validação do parâmetro|Suporte a parâmetros posicionais|
|--------------|--------------------------|------------------------|--------------------------|----------------------------------|
|`_vcprintf`|[_cprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|console|Verifique se há nulos.|no|
|`_vcwprintf`|[_cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|console|Verifique se há nulos.|no|
|`vfprintf`|[fprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*Fluxo*|Verifique se há nulos.|no|
|**vfprintf_p**|[fprintf_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*Fluxo*|Verifique se há nulos e formato válido.|sim|
|`vfprintf_s`|[fprintf_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*Fluxo*|Verifique se há nulos e formato válido.|no|
|`vfwprintf`|[fwprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*Fluxo*|Verifique se há nulos.|no|
|**vfwprintf_p**|[fwprintf_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*Fluxo*|Verifique se há nulos e formato válido.|sim|
|`vfwprintf_s`|[fwprintf_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*Fluxo*|Verifique se há nulos e formato válido.|no|
|`vprintf`|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Verifique se há nulos.|no|
|**vprintf_p**|[printf_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Verifique se há nulos e formato válido.|sim|
|`vprintf_s`|[printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Verifique se há nulos e formato válido.|no|
|`vwprintf`|[wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Verifique se há nulos.|no|
|**vwprintf_p**|[wprintf_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Verifique se há nulos e formato válido.|sim|
|`vwprintf_s`|[wprintf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Verifique se há nulos e formato válido.|no|
|**vsprintf**|[sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|memória apontada pelo *buffer*|Verifique se há nulos.|no|
|**vsprintf_p**|[sprintf_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|memória apontada pelo *buffer*|Verifique se há nulos e formato válido.|sim|
|`vsprintf_s`|[sprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|memória apontada pelo *buffer*|Verifique se há nulos e formato válido.|no|
|`vswprintf`|[swprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|memória apontada pelo *buffer*|Verifique se há nulos.|no|
|**vswprintf_p**|[swprintf_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|memória apontada pelo *buffer*|Verifique se há nulos e formato válido.|sim|
|`vswprintf_s`|[swprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|memória apontada pelo *buffer*|Verifique se há nulos e formato válido.|no|
|`_vscprintf`|[_vscprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|memória apontada pelo *buffer*|Verifique se há nulos.|no|
|`_vscwprintf`|[_vscwprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|memória apontada pelo *buffer*|Verifique se há nulos.|no|
|`_vsnprintf`|[_snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|memória apontada pelo *buffer*|Verifique se há nulos.|no|
|`_vsnwprintf`|[_snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|memória apontada pelo *buffer*|Verifique se há nulos.|no|

O argumento `argptr` tem o tipo `va_list`, definido em VARARGS.H e STDARG.H. A variável `argptr` deve ser inicializada por **va_start** e podem ser reinicializadas por chamadas `va_arg` subsequentes; `argptr` aponta para o início de uma lista de argumentos que são convertidos e transmitidos para saída de acordo com as especificações correspondentes no argumento *format*. O *formato* tem a mesma forma e função do que o argumento *format* para [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md). Nenhuma dessas funções invoca `va_end`. Para obter uma descrição mais completa de cada `vprintf` funcionam, consulte a descrição de sua função equivalente, conforme listado na tabela anterior.

`_vsnprintf` é diferente **vsprintf** já que grava até *count* bytes no *buffer*.

As versões dessas funções com o infixo **w** no nome são versões de caractere largo das funções correspondentes sem o infixo **w**; em cada uma dessas funções de caractere largo, *buffer* e *format* são sequências de caracteres largos. Caso contrário, cada função de caractere largo se comporta de forma idêntica à sua função equivalente do SBCS.

As versões dessas funções com os sufixos **_s** e **_p** são as versões mais seguras. Essas versões validam as cadeias de caracteres de formato e gerarão uma exceção se a cadeia de caracteres de formato não for bem formada (por exemplo, se caracteres de formatação inválidos forem usados).

As versões dessas funções com o **_p** sufixo fornecem a capacidade de especificar a ordem na qual os argumentos fornecidos são substituídos na cadeia de caracteres de formato. Para obter mais informações, consulte [Parâmetros posicionais printf_p](../c-runtime-library/printf-p-positional-parameters.md).

Para **vsprintf**, `vswprintf`, `_vsnprintf` e `_vsnwprintf`, se ocorrer cópia entre cadeias de caracteres que se sobrepõem, o comportamento será indefinido.

> [!IMPORTANT]
>  Verifique se *format* não é uma cadeia de caracteres definida pelo usuário. Para obter mais informações, consulte [Avoiding Buffer Overruns](/windows/win32/SecBP/avoiding-buffer-overruns) (Evitando estouros de buffer). Se estiver usando as versões seguras dessas funções (os sufixos **_s** ou **_p**), uma cadeia de caracteres de formato fornecida pelo usuário poderia disparar uma exceção de parâmetro inválido caso a cadeia de caracteres fornecida pelo usuário contivesse caracteres de formatação inválidos.

## <a name="see-also"></a>Consulte também

[E/S de fluxo](../c-runtime-library/stream-i-o.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)
