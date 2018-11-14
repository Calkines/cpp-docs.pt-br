---
title: __getmainargs, __wgetmainargs
ms.date: 11/04/2016
apiname:
- __wgetmainargs
- __getmainargs
apilocation:
- msvcr100.dll
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr110.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- __wgetmainargs
- __getmainargs
helpviewer_keywords:
- __wgetmainargs
- __getmainargs
ms.assetid: f72f54eb-9509-4bdf-8752-40fc49055439
ms.openlocfilehash: 6e2bf21f2ac50d3486af56f9581ff6c8d0e0c309
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523332"
---
# <a name="getmainargs-wgetmainargs"></a>__getmainargs, __wgetmainargs

Invoca a análise de linha de comando e copia os argumentos para `main()` através dos ponteiros passados.

## <a name="syntax"></a>Sintaxe

```cpp
int __getmainargs(
    int * _Argc,
   char *** _Argv,
   char *** _Env,
   int _DoWildCard,
_startupinfo * _StartInfo);

int __wgetmainargs (
   int *_Argc,
   wchar_t ***_Argv,
   wchar_t ***_Env,
   int _DoWildCard,
   _startupinfo * _StartInfo)
```

#### <a name="parameters"></a>Parâmetros

`_Argc`<br/>
Um inteiro que contém o número de argumentos que se seguem em `argv`. O parâmetro `argc` é sempre maior ou igual a 1.

`_Argv`<br/>
Uma matriz de cadeias de caracteres terminadas em nulo que representam argumentos de linha de comando inseridos pelo usuário do programa. Por convenção, `argv[0]` é o comando com o qual o programa é invocado, argv[1] é o primeiro argumento de linha de comando e assim por diante, até argv[argc], que sempre é **NULL**. O primeiro argumento de linha de comando sempre é `argv[1]` e o último é `argv[argc - 1]`.

`_Env`<br/>
Uma matriz de cadeias de caracteres que representam as variáveis definidas no ambiente do usuário. Essa matriz é encerrada por uma entrada **NULL**.

`_DoWildCard`<br/>
Um inteiro que, se definido como 1, expande os curingas nos argumentos de linha de comando ou, se definido como 0, não faz nada.

`_StartInfo`<br/>
Outras informações a serem passadas para a DLL do CRT.

## <a name="return-value"></a>Valor retornado

0 se for bem-sucedido; um valor negativo se não for.

## <a name="remarks"></a>Comentários

Use `__getmainargs` em plataformas que não têm caracteres largos e `__wgetmainargs` em plataformas de caractere largo (Unicode).

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|__getmainargs|internal.h|
|__wgetmainargs|internal.h|