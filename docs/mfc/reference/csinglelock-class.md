---
title: Classe CSingleLock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSingleLock
- AFXMT/CSingleLock
- AFXMT/CSingleLock::CSingleLock
- AFXMT/CSingleLock::IsLocked
- AFXMT/CSingleLock::Lock
- AFXMT/CSingleLock::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CSingleLock [MFC], CSingleLock
- CSingleLock [MFC], IsLocked
- CSingleLock [MFC], Lock
- CSingleLock [MFC], Unlock
ms.assetid: 7dae7288-8066-4a3e-85e0-78d28bfc6bc8
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 063ad23a9d356af0cac6c5b9dd8903e81530d2df
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50061333"
---
# <a name="csinglelock-class"></a>Classe CSingleLock

Representa o mecanismo de controle de acesso usado no controle de acesso a um recurso em um programa multi-threaded.

## <a name="syntax"></a>Sintaxe

```
class CSingleLock
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores Públicos

|Nome|Descrição|
|----------|-----------------|
|[CSingleLock::CSingleLock](#csinglelock)|Constrói um objeto `CSingleLock`.|

### <a name="public-methods"></a>Métodos Públicos

|Nome|Descrição|
|----------|-----------------|
|[CSingleLock::IsLocked](#islocked)|Determina se o objeto está bloqueado.|
|[CSingleLock::Lock](#lock)|Espera-se em um objeto de sincronização.|
|[CSingleLock::Unlock](#unlock)|Libera um objeto de sincronização.|

## <a name="remarks"></a>Comentários

`CSingleLock` não tem uma classe base.

Para usar as classes de sincronização [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md), e [CEvent](../../mfc/reference/cevent-class.md), você deve criar um `CSingleLock` ou [CMultiLock](../../mfc/reference/cmultilock-class.md) objeto para aguardar e liberar o objeto de sincronização. Use `CSingleLock` quando você só precisa esperar em um objeto por vez. Use `CMultiLock` quando houver vários objetos que você poderia usar em um momento específico.

Para usar um `CSingleLock` de objeto, chame seu construtor dentro de uma função de membro na classe do recurso controlado. Em seguida, chame o [IsLocked](#islocked) a função de membro para determinar se o recurso está disponível. Se for, continue com o restante da função de membro. Se o recurso estiver disponível, aguarde até que uma quantidade especificada de tempo para o recurso seja liberado, ou retornar falha. Após a conclusão do uso do recurso, chamar o [Unlock](#unlock) funcionará se o `CSingleLock` objeto deve ser usado novamente ou permitir que o `CSingleLock` objeto a ser destruído.

`CSingleLock` objetos exigem a presença de um objeto derivado de [CSyncObject](../../mfc/reference/csyncobject-class.md). Isso geralmente é um membro de dados da classe do recurso controlado. Para obter mais informações sobre como usar `CSingleLock` objetos, consulte o artigo [Multithreading: como usar as Classes de sincronização](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

`CSingleLock`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** afxmt.h

##  <a name="csinglelock"></a>  CSingleLock::CSingleLock

Constrói um objeto `CSingleLock`.

```
explicit CSingleLock(
    CSyncObject* pObject,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>Parâmetros

*pObject*<br/>
Aponta para o objeto de sincronização a ser acessado. Não pode ser NULL.

*bInitialLock*<br/>
Especifica se deve ser inicialmente tentar acessar o objeto fornecido.

### <a name="remarks"></a>Comentários

Geralmente, essa função é chamada de dentro de uma função de membro de acesso do recurso controlado.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_MFC_Utilities#19](../../mfc/codesnippet/cpp/csinglelock-class_1.h)]

##  <a name="islocked"></a>  CSingleLock::IsLocked

Determina se o objeto associado a `CSingleLock` objeto está não sinalizado (não disponível).

```
BOOL IsLocked();
```

### <a name="return-value"></a>Valor de retorno

Diferente de zero se o objeto está bloqueado; Caso contrário, 0.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_MFC_Utilities#20](../../mfc/codesnippet/cpp/csinglelock-class_2.h)]

##  <a name="lock"></a>  CSingleLock::Lock

Chame essa função para acessar o recurso controlado pelo objeto de sincronização fornecido para o `CSingleLock` construtor.

```
BOOL Lock(DWORD dwTimeOut = INFINITE);
```

### <a name="parameters"></a>Parâmetros

*dwTimeOut*<br/>
Especifica a quantidade de tempo de espera para o objeto de sincronização estejam disponíveis (sinalizado). Se for infinito, `Lock` aguardará até que o objeto é sinalizado antes de retornar.

### <a name="return-value"></a>Valor de retorno

Diferente de zero se a função for bem-sucedida; Caso contrário, 0.

### <a name="remarks"></a>Comentários

Se o objeto de sincronização é sinalizado, `Lock` retornará com êxito e agora, o thread possui o objeto. Se o objeto de sincronização é não sinalizado (não disponível) `Lock` aguardará o objeto de sincronização ficar sinalizado até o número de milissegundos especificado na *dwTimeOut* parâmetro. Se o objeto de sincronização não sinalizado na quantidade especificada de tempo, `Lock` retorna falha.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

##  <a name="unlock"></a>  CSingleLock::Unlock

Libera o objeto de sincronização pertencente a `CSingleLock`.

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>Parâmetros

*lCount*<br/>
Número de acessos a versão. Deve ser maior que 0. Se a quantidade especificada faria com que a contagem de objeto exceder seu máximo, a contagem não será alterada e a função retornará FALSE.

*lPrevCount*<br/>
Aponta para uma variável para receber a contagem anterior do objeto de sincronização. Se for NULL, a contagem anterior não é retornada.

### <a name="return-value"></a>Valor de retorno

Diferente de zero se a função for bem-sucedida; Caso contrário, 0.

### <a name="remarks"></a>Comentários

Essa função é chamada pelo `CSingleLock`do destruidor.

Se você precisar liberar mais de uma contagem de acesso de um semáforo, use a segunda forma de `Unlock` e especifique o número de acessos para liberar.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

## <a name="see-also"></a>Consulte também

[Gráfico da hierarquia](../../mfc/hierarchy-chart.md)<br/>
[Classe CMultiLock](../../mfc/reference/cmultilock-class.md)
