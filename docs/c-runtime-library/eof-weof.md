---
title: EOF, WEOF
ms.date: 11/04/2016
f1_keywords:
- EOF
helpviewer_keywords:
- EOF function
- WEOF function
- end of file
ms.assetid: a7150563-cdae-4cdf-9798-ad509990e505
ms.openlocfilehash: f00c4003afebad580bd2ea5d6853edc3ca6e8c73
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740044"
---
# <a name="eof-weof"></a>EOF, WEOF

## <a name="syntax"></a>Sintaxe

```
#include <stdio.h>
```

## <a name="remarks"></a>Comentários

EOF é retornado por uma rotina de E/S quando o final do arquivo (ou, em alguns casos, um erro) é encontrado.

WEOF produz o valor retornado do tipo **wint_t**, usado para sinalizar o final de um fluxo grande ou relatar uma condição de erro.

## <a name="see-also"></a>Consulte também

[putc, putwc](../c-runtime-library/reference/putc-putwc.md)<br/>
[ungetc, ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[fflush](../c-runtime-library/reference/fflush.md)<br/>
[fclose, _fcloseall](../c-runtime-library/reference/fclose-fcloseall.md)<br/>
[_ungetch, _ungetwch, _ungetch_nolock, _ungetwch_nolock](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)<br/>
[_putch, _putwch](../c-runtime-library/reference/putch-putwch.md)<br/>
[isascii, __isascii, iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)<br/>
[Constantes globais](../c-runtime-library/global-constants.md)
