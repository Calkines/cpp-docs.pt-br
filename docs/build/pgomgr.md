---
title: pgomgr
ms.date: 03/14/2018
helpviewer_keywords:
- pgomgr program
- profile-guided optimizations, pgomgr
ms.assetid: 74589126-df18-42c9-8739-26d60e148d6a
ms.openlocfilehash: 4e3eb08c88db9d0ed4e47649014a600c3e0ccb78
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295218"
---
# <a name="pgomgr"></a>pgomgr

Adiciona dados de perfil de um ou mais arquivos. PGC para o arquivo. PGD.

## <a name="syntax"></a>Sintaxe

> **pgomgr** [*opções*] *pgcfiles* *pgdfile*

### <a name="parameters"></a>Parâmetros

*options*<br/>
As opções a seguir podem ser especificadas para **pgomgr**:

- **/Help** ou **/?** Exibe disponíveis **pgomgr** opções.

- **/clear** faz com que o arquivo. PGD seja limpo de todas as informações de perfil. Não é possível especificar um. PGC arquivo quando **/limpar** for especificado.

- **/Detail** exibe as estatísticas detalhadas, incluindo informações de cobertura de gráfico de fluxo.

- **/ summary** exibe de estatísticas por função.

- **/Unique** quando usado com **/summary**, causas decorado nomes de função para exibir. O padrão, quando **/Unique** não for usado, é não decorado para nomes de função a ser exibido.

- **/ merge**\[**:**<em>n</em>] faz com que os dados no arquivo. PGC ou arquivos a serem adicionados ao arquivo. PGD. O parâmetro opcional, *n*, permite que você especifique que os dados devem ser adicionados *n* vezes. Por exemplo, se um cenário normalmente seria feitos seis vezes refletir a frequência com que isso é feito por clientes, você pode fazer isso vez em uma execução de teste e adicioná-lo para o arquivo. PGD seis vezes com **pgomgr /merge:6**.

*pgcfiles*<br/>
. PGC um ou mais arquivos cujos dados de perfil que você deseja mesclar com o arquivo. PGD. Você pode especificar um arquivo. PGC único ou vários arquivos. PGC. Se você não especificar todos os arquivos. PGC, **pgomgr** mescla todos os arquivos. PGC cujos nomes de arquivo são os mesmos que o arquivo. PGD.

*pgdfile*<br/>
O arquivo. PGD para a qual você está mesclando dados do arquivo. PGC ou arquivos.

## <a name="remarks"></a>Comentários

> [!NOTE]
> Você pode iniciar essa ferramenta apenas de um prompt de comando do desenvolvedor de Visual Studio. Você não pode iniciá-lo em um prompt de comando do sistema ou no Explorador de arquivos.

## <a name="example"></a>Exemplo

Este exemplo de comando limpa o arquivo myapp.pgd dos dados de perfil:

`pgomgr /clear myapp.pgd`

Este exemplo de comando adiciona dados de perfil no myapp1.pgc para o arquivo. PGD três vezes:

`pgomgr /merge:3 myapp1.pgc myapp.pgd`

Neste exemplo, dados de perfil de todos os arquivos. PGC do n º de myapp são adicionados ao arquivo myapp.pgd.

`pgomgr -merge myapp1.pgd`

## <a name="see-also"></a>Consulte também

[Otimizações guiadas por perfil](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
[pgosweep](pgosweep.md)<br/>
