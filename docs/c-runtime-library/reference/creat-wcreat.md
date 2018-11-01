---
title: _creat, _wcreat
ms.date: 11/04/2016
apiname:
- _creat
- _wcreat
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wcreat
- _wcreat
- _creat
- tcreat
- _tcreat
helpviewer_keywords:
- wcreat function
- _wcreat function
- files [C++], creating
- _creat function
- tcreat function
- creat function
- _tcreat function
ms.assetid: 3b3b795d-1620-40ec-bd2b-a4bbb0d20fe5
ms.openlocfilehash: 901a95a6a9361f95f38749dacf1a5001d97b3761
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494985"
---
# <a name="creat-wcreat"></a>_creat, _wcreat

Cria um novo arquivo. **Creat** e **wcreat** foram preteridos; use [sopen_s, wsopen_s](sopen-s-wsopen-s.md) em vez disso.

## <a name="syntax"></a>Sintaxe

```C
int _creat(
   const char *filename,
   int pmode
);
int _wcreat(
   const wchar_t *filename,
   int pmode
);
```

### <a name="parameters"></a>Parâmetros

*filename*<br/>
Nome do novo arquivo.

*pmode*<br/>
Configuração de permissão.

## <a name="return-value"></a>Valor de retorno

Essas funções, se tiverem êxito, retornarão um descritor de arquivo para o arquivo criado. Caso contrário, as funções retornarão -1 e defina **errno** conforme mostrado na tabela a seguir.

|**errno** configuração|Descrição|
|---------------------|-----------------|
|**EACCES**|*nome do arquivo* Especifica um arquivo somente leitura existente ou especifica um diretório em vez de um arquivo.|
|**EMFILE**|Nenhum outro descritor de arquivo disponível.|
|**ENOENT**|Não foi possível encontrar o arquivo especificado.|

Se *filename* é **nulo**, essas funções invocarão o manipulador de parâmetro inválido, conforme descrito na [validação de parâmetro](../../c-runtime-library/parameter-validation.md). Se a execução puder continuar, essas funções definirão **errno** à **EINVAL** e retornarão -1.

Para obter mais informações sobre esses e outros códigos de retorno, consulte [_doserrno, errno, _sys_errlist e _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentários

O **Creat** função cria um novo arquivo ou abre e trunca um existente. **wcreat** é uma versão de caractere largo de **Creat**; o *filename* argumento **wcreat** é uma cadeia de caracteres largos. **wcreat** e **Creat** se comportam de forma idêntica caso contrário.

### <a name="generic-text-routine-mappings"></a>Mapeamentos da rotina de texto genérico

|Rotina Tchar.h|_UNICODE e _MBCS não definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**tcreat**|**_creat**|**_creat**|**_wcreat**|

Se o arquivo especificado por *filename* não existir, um novo arquivo é criado com a configuração de permissão determinada e será aberto para gravação. Se o arquivo já existe e a configuração de permissão permite gravação, **Creat** trunca o arquivo para o tamanho 0, destruindo o conteúdo anterior e o abre para gravação. A configuração de permissão *pmode*, se aplica somente a arquivos recém-criados. O novo arquivo recebe a configuração de permissão especificada depois que ele é fechado pela primeira vez. A expressão de inteiro *pmode* contém uma ou ambas as constantes de manifesto **s_iwrite** e **s_iread**, definidas em sys\stat.h. Quando as duas constantes são informadas, elas são unidas com o bit a bit ou operador ( **&#124;** ). O *pmode* parâmetro é definido como um dos valores a seguir.

|Valor|Definição|
|-----------|----------------|
|**S_IWRITE**|Gravação permitida.|
|**S_IREAD**|Leitura permitida.|
|**S_IREAD** &AMP;#124; **S_IWRITE**|Leitura e gravação permitidas.|

Se a permissão de gravação não for fornecida, o arquivo será somente leitura. Todos os arquivos são sempre legíveis; é impossível conceder permissão somente gravação. Os modos **s_iwrite** e **s_iread** | **s_iwrite** , em seguida, são equivalentes. Arquivos abertos usando **Creat** sempre são abertos no modo de compatibilidade (consulte [sopen](sopen-wsopen.md)) com **sh_denyno**.

**Creat** aplica-se a máscara de permissão de arquivo atual a *pmode* antes de definir as permissões (consulte [umask](umask.md)). **Creat** é fornecido principalmente para compatibilidade com bibliotecas anteriores. Uma chamada para **Open** com **o_creat** e **o_trunc** no *oflag* parâmetro é equivalente à **Creat**e é preferível para o novo código.

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|Cabeçalho opcional|
|-------------|---------------------|---------------------|
|**_creat**|\<io.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|
|**_wcreat**|\<io.h> ou \<wchar.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|

Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

```C
// crt_creat.c
// compile with: /W3
// This program uses _creat to create
// the file (or truncate the existing file)
// named data and open it for writing.

#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int fh;

   fh = _creat( "data", _S_IREAD | _S_IWRITE ); // C4996
   // Note: _creat is deprecated; use _sopen_s instead
   if( fh == -1 )
      perror( "Couldn't create data file" );
   else
   {
      printf( "Created data file.\n" );
      _close( fh );
   }
}
```

```Output
Created data file.
```

## <a name="see-also"></a>Consulte também

[E/S de nível inferior](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
[_umask](umask.md)<br/>
