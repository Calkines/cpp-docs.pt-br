---
title: localeconv
ms.date: 11/04/2016
apiname:
- localeconv
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
- localeconv
helpviewer_keywords:
- lconv type
- localeconv function
- locales, getting information on
ms.assetid: 7ecdb1f2-88f5-4037-a0e7-c754ab003660
ms.openlocfilehash: bf26e4f7b7fb4f0334b57604fe5c4996312bd62a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628131"
---
# <a name="localeconv"></a>localeconv

Obtém informações detalhadas sobre configurações de localidade.

## <a name="syntax"></a>Sintaxe

```C
struct lconv *localeconv( void );
```

## <a name="return-value"></a>Valor de retorno

**localeconv** retorna um ponteiro para um objeto preenchido do tipo [struct lconv](../../c-runtime-library/standard-types.md). Os valores contidos no objeto são copiados das configurações de localidade no armazenamento local de thread e podem ser substituídos por chamadas subsequentes a **localeconv**. As alterações feitas para os valores nesse objeto não modificam as configurações de localidade. Chamadas para [setlocale](setlocale-wsetlocale.md) com *categoria* valores de **LC_ALL**, **LC_MONETARY**, ou **LC_NUMERIC** Substitua o conteúdo da estrutura.

## <a name="remarks"></a>Comentários

O **localeconv** função obtém informações detalhadas sobre a formatação numérica para a localidade atual. Essas informações são armazenadas em uma estrutura do tipo **lconv**. A estrutura **lconv**, definida em LOCALE.H, contém os seguintes membros:

|Campo|Significado|
|-|-|
decimal_point,<br/>_W_decimal_point|Ponteiro para caractere para quantidades não monetárias de ponto decimal.
thousands_sep,<br/>_W_thousands_sep|Ponteiro para o caractere que separa grupos de dígitos à esquerda do ponto decimal para quantidades não monetárias.
agrupando|Ponteiro para um **char**-tamanho inteiro que contém o tamanho de cada grupo de dígitos em quantidades não monetárias.
int_curr_symbol,<br/>_W_int_curr_symbol|Ponteiro para o símbolo de moeda internacional para a localidade atual. Os três primeiros caracteres especificam o símbolo de moeda alfabético internacional, conforme definido na norma *ISO 4217, Códigos para a Representação de Moedas e Fundos*. O quarto caractere (caractere nulo imediatamente anterior) separa o símbolo de moeda internacional da quantidade monetária.
currency_symbol,<br/>_W_currency_symbol|Ponteiro para o símbolo de moeda local para a localidade atual.
mon_decimal_point,<br/>_W_mon_decimal_point|Ponteiro para caractere para quantidades monetárias de ponto decimal.
mon_thousands_sep,<br/>_W_mon_thousands_sep|Ponteiro para o separador para grupos de dígitos à esquerda da casa decimal em quantidades monetárias.
mon_grouping|Ponteiro para um **char**-tamanho inteiro que contém o tamanho de cada grupo de dígitos em quantidades monetárias.
positive_sign,<br/>_W_positive_sign|Cadeia de caracteres indicando o sinal para quantidades monetárias não negativas.
negative_sign,<br/>_W_negative_sign|Cadeia de caracteres indicando o sinal para quantidades monetárias negativas.
int_frac_digits|Número de dígitos à direita da vírgula decimal em quantidades monetárias internacionalmente formatadas.
frac_digits|Número de dígitos à direita da vírgula decimal em quantidades monetárias formatadas.
p_cs_precedes|Definido como 1 se o símbolo de moeda preceder o valor para a quantidade monetária formatada não negativa. Definido como 0 se o símbolo seguir o valor.
p_sep_by_space|Definido como 1 se o símbolo de moeda for separado por espaço do valor para a quantidade monetária formatada não negativa. Definido como 0 se não houver nenhuma separação por espaço.
n_cs_precedes|Definido como 1 se o símbolo de moeda preceder o valor para a quantidade monetária formatada negativa. Definido como 0 se o símbolo suceder o valor.
n_sep_by_space|Definido como 1 se o símbolo de moeda for separado por espaço do valor para a quantidade monetária formatada negativa. Definido como 0 se não houver nenhuma separação por espaço.
p_sign_posn|Posição do sinal positivo em quantidades monetárias formatadas não negativas.
n_sign_posn|Posição do sinal positivo em quantidades monetárias formatadas negativas.

Exceto conforme especificados, membros do **lconv** estrutura que têm `char *` e `wchar_t *` versões são ponteiros para cadeias de caracteres. Qualquer um desses que é igual a **""** (ou **L ""** para **wchar_t** <strong>\*</strong>) é de comprimento zero ou não tem suporte no atual localidade. Observe que **decimal_point** e **_W_decimal_point** sempre terão suporte e comprimento diferente de zero.

O **char** membros da estrutura são números pequenos não negativos, não caracteres. Qualquer um desses que seja igual a **CHAR_MAX** não terá suporte na localidade atual.

Os valores de **agrupando** e **mon_grouping** são interpretados de acordo com as regras a seguir:

- **CHAR_MAX** -não execute qualquer agrupamento adicional.

- 0 - use o elemento anterior para cada um dos dígitos restantes.

- *n* -número de dígitos que compõem o grupo atual. O próximo elemento é examinado para determinar o tamanho do próximo grupo de dígitos antes do grupo atual.

Os valores para **int_curr_symbol** são interpretados de acordo com as regras a seguir:

- Os três primeiros caracteres especificam o símbolo de moeda alfabético internacional, conforme definido na norma *ISO 4217, Códigos para a Representação de Moedas e Fundos*.

- O quarto caractere (caractere nulo imediatamente anterior) separa o símbolo de moeda internacional da quantidade monetária.

Os valores para **p_cs_precedes** e **n_cs_precedes** são interpretados de acordo com as regras a seguir (a regra para **n_cs_precedes** está entre parênteses):

- 0 - o símbolo de moeda Sucede o valor para não negativo (negativo) valor monetário formatado.

- 1 - formato de moeda precede o valor para não negativo (negativo) valor monetário formatado.

Os valores para **p_sep_by_space** e **n_sep_by_space** são interpretados de acordo com as regras a seguir (a regra para **n_sep_by_space** está entre parênteses):

- 0 - o símbolo de moeda é separado por espaço para não negativo (negativo) monetária formatada do valor.

- 1 - não há nenhuma separação por espaço entre o símbolo de moeda e o valor não negativo (negativo) valor monetário formatado.

Os valores para **p_sign_posn** e **n_sign_posn** são interpretados de acordo com as regras a seguir:

- 0 - parênteses circundam os símbolos de quantidade e moeda.

- 1 - entrada de cadeia de caracteres precede a símbolos de quantidade e moeda.

- 2 - cadeia de caracteres de entrada segue os símbolos de quantidade e moeda.

- 3 - entrada de cadeia de caracteres precede o símbolo de moeda.

- 4 - entrada de cadeia de caracteres imediatamente o símbolo de moeda da seguinte maneira.

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**localeconv**|\<locale.h>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Libraries

Todas as versões das [bibliotecas em tempo de execução C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Consulte também

[Localidade](../../c-runtime-library/locale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[Funções strcoll](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
