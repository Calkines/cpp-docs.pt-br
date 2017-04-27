---
title: Classe CAtlTransactionManager | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlTransactionManager
- ATLTRANSACTIONMANAGER/ATL::CAtlTransactionManager
- ATLTRANSACTIONMANAGER/ATL::CAtlTransactionManager
- ATLTRANSACTIONMANAGER/ATL::Close
- ATLTRANSACTIONMANAGER/ATL::Commit
- ATLTRANSACTIONMANAGER/ATL::Create
- ATLTRANSACTIONMANAGER/ATL::CreateFile
- ATLTRANSACTIONMANAGER/ATL::DeleteFile
- ATLTRANSACTIONMANAGER/ATL::FindFirstFile
- ATLTRANSACTIONMANAGER/ATL::GetFileAttributes
- ATLTRANSACTIONMANAGER/ATL::GetFileAttributesEx
- ATLTRANSACTIONMANAGER/ATL::GetHandle
- ATLTRANSACTIONMANAGER/ATL::IsFallback
- ATLTRANSACTIONMANAGER/ATL::MoveFile
- ATLTRANSACTIONMANAGER/ATL::RegCreateKeyEx
- ATLTRANSACTIONMANAGER/ATL::RegDeleteKey
- ATLTRANSACTIONMANAGER/ATL::RegOpenKeyEx
- ATLTRANSACTIONMANAGER/ATL::Rollback
- ATLTRANSACTIONMANAGER/ATL::SetFileAttributes
- ATLTRANSACTIONMANAGER/ATL::m_bFallback
- ATLTRANSACTIONMANAGER/ATL::m_hTransaction
dev_langs:
- C++
helpviewer_keywords:
- CAtlTransactionManager class
ms.assetid: b01732dc-1d16-4b42-bfac-b137fca2b740
caps.latest.revision: 25
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: bc6162eaf1a4c8c3848a32e861019ff50e4f850c
ms.lasthandoff: 02/25/2017

---
# <a name="catltransactionmanager-class"></a>Classe CAtlTransactionManager
Classe CAtlTransactionManager fornece um wrapper para funções de gerente KTM (Kernel Transaction).  
  
> [!IMPORTANT]
>  Essa classe e seus membros não podem ser usados em aplicativos executados no tempo de execução do Windows.  
  
## <a name="syntax"></a>Sintaxe  
  
```
class CAtlTransactionManager;
```  
  
## <a name="members"></a>Membros  
  
### <a name="public-constructors"></a>Construtores públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[~ CAtlTransactionManager](#dtor)|Destruidor de CAtlTransactionManager.|  
|[CAtlTransactionManager](#catltransactionmanager)|Construtor CAtlTransactionManager.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[Fechar](#close)|Fecha um identificador de transação.|  
|[Confirmação](#commit)|Solicitações que a transação ser confirmada.|  
|[Criar](#create)|Cria o identificador de transação.|  
|[CreateFile](#createfile)|Cria ou abre um arquivo, o fluxo de arquivos ou a pasta como uma operação transacionada.|  
|[DeleteFile](#deletefile)|Exclui um arquivo existente como uma operação transacionada.|  
|[FindFirstFile](#findfirstfile)|Pesquisa um diretório para um arquivo ou subdiretório como uma operação transacionada.|  
|[GetFileAttributes](#getfileattributes)|Recupera os atributos de sistema de arquivo para um arquivo ou diretório especificado como uma operação transacionada.|  
|[GetFileAttributesEx](#getfileattributesex)|Recupera os atributos de sistema de arquivo para um arquivo ou diretório especificado como uma operação transacionada.|  
|[GetHandle](#gethandle)|Retorna o identificador da transação.|  
|[IsFallback](#isfallback)|Determina se as chamadas de fallback estão habilitadas.|  
|[MoveFile](#movefile)|Move um arquivo existente ou um diretório, incluindo seus filhos, como uma operação transacionada.|  
|[RegCreateKeyEx](#regcreatekeyex)|Cria uma chave do Registro especificada e a associa a uma transação. Se a chave já existir, a função é aberto.|  
|[RegDeleteKey](#regdeletekey)|Exclui uma subchave e seus valores de modo de exibição específico de plataforma especificado do registro como uma operação transacionada.|  
|[RegOpenKeyEx](#regopenkeyex)|Abre a chave do Registro especificada e a associa a uma transação.|  
|[Reversão](#rollback)|Solicitações que a transação ser revertida.|  
|[SetFileAttributes](#setfileattributes)|Define os atributos de um arquivo ou diretório como uma operação transacionada.|  
  
### <a name="protected-data-members"></a>Membros de dados protegidos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[m_bFallback](#m_bfallback)|`TRUE`Se houver suporte para o fallback; `FALSE` caso contrário.|  
|[m_hTransaction](#m_htransaction)|O identificador da transação.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="inheritance-hierarchy"></a>Hierarquia de herança  
 [ATL::CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** atltransactionmanager.h  
  
##  <a name="dtor"></a>~ CAtlTransactionManager  
 Destruidor de CAtlTransactionManager.  
  
```
virtual ~CAtlTransactionManager();
```  
  
### <a name="remarks"></a>Comentários  
 No processamento normal, a transação é confirmada automaticamente e fechada. Se o destruidor é chamado durante um desenrolamento de exceção, a transação é revertida e fechada.  
  
##  <a name="catltransactionmanager"></a>CAtlTransactionManager  
 Construtor CAtlTransactionManager.  
  
```
CAtlTransactionManager(BOOL bFallback = TRUE, BOOL bAutoCreateTransaction = TRUE);
```  
  
### <a name="parameters"></a>Parâmetros  
 `bFallback`  
 `TRUE`indica suporte fallback. Se transacionado função falhar, a classe automaticamente chama a função "transacionado". `FALSE`não indica que nenhuma chamada "fallback".  
  
 `bAutoCreateTransaction`  
 `TRUE`indica que o manipulador de transações é criado automaticamente no construtor. `FALSE`indica que não é.  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="close"></a>Fechar  
 Fecha o identificador de transação.  
  
```
inline BOOL Close();
```  
  
### <a name="return-value"></a>Valor de retorno  
 `TRUE` caso bem-sucedido; caso contrário, `FALSE`.  
  
### <a name="remarks"></a>Comentários  
 Esse wrapper chama o `CloseHandle` função. O método é chamado automaticamente no destruidor.  
  
##  <a name="commit"></a>Confirmação  
 Solicitações que a transação ser confirmada.  
  
```
inline BOOL Commit();
```  
  
### <a name="return-value"></a>Valor de retorno  
 `TRUE` caso bem-sucedido; caso contrário, `FALSE`.  
  
### <a name="remarks"></a>Comentários  
 Esse wrapper chama o `CommitTransaction` função. O método é chamado automaticamente no destruidor.  
  
##  <a name="create"></a>Criar  
 Cria o identificador de transação.  
  
```
inline BOOL Create();
```  
  
### <a name="return-value"></a>Valor de retorno  
 `TRUE` caso bem-sucedido; caso contrário, `FALSE`.  
  
### <a name="remarks"></a>Comentários  
 Esse wrapper chama o `CreateTransaction` função. Verifique a existência de  
  
##  <a name="createfile"></a>CreateFile  
 Cria ou abre um arquivo, o fluxo de arquivos ou a pasta como uma operação transacionada.  
  
```
inline HANDLE CreateFile(
  LPCTSTR lpFileName,
    DWORD dwDesiredAccess,
    DWORD dwShareMode,
    LPSECURITY_ATTRIBUTES lpSecurityAttributes,
    DWORD dwCreationDisposition,
    DWORD dwFlagsAndAttributes,
    HANDLE hTemplateFile);
```  
  
### <a name="parameters"></a>Parâmetros  
 `lpFileName`  
 O nome de um objeto a ser criado ou aberto.  
  
 `dwDesiredAccess`  
 O acesso ao objeto, que pode ser resumido como leitura, gravação, ambos ou nenhum (zero). Os valores mais comumente usados são GENERIC_READ, GENERIC_WRITE ou ambos: GENERIC_READ | GENERIC_WRITE.  
  
 `dwShareMode`  
 O modo de compartilhamento de um objeto, que pode ser de leitura, gravação, ambos, excluir, todos eles, ou nenhum: 0, FILE_SHARE_DELETE, FILE_SHARE_READ, FILE_SHARE_WRITE.  
  
 `lpSecurityAttributes`  
 Um ponteiro para uma estrutura SECURITY_ATTRIBUTES que contém um descritor de segurança opcional e também determina se ou não o identificador retornado pode ser herdado pelos processos filhos. O parâmetro pode ser `NULL`.  
  
 `dwCreationDisposition`  
 Uma ação em arquivos que já existem e não existem. Esse parâmetro deve ser um dos valores a seguir, que não podem ser combinados: CREATE_ALWAYS, CREATE_NEW, OPEN_ALWAYS, OPEN_EXISTING ou TRUNCATE_EXISTING.  
  
 `dwFlagsAndAttributes`  
 Os atributos de arquivo e sinalizadores. Este parâmetro pode incluir qualquer combinação de atributos de arquivo disponível (FILE_ATTRIBUTE_ *). Todos os outros atributos de arquivo substituem FILE_ATTRIBUTE_NORMAL. Esse parâmetro também pode conter combinações dos sinalizadores (FILE_FLAG_\*) para o controle do comportamento de buffer, acessar modos e outros sinalizadores de finalidade especial. Elas são combinadas com qualquer FILE_ATTRIBUTE_\* valores.  
  
 `hTemplateFile`  
 Um identificador válido para um arquivo de modelo com o direito de acesso GENERIC_READ. O arquivo de modelo fornece atributos de arquivo e os atributos estendidos para o arquivo que está sendo criado. Esse parâmetro pode ser `NULL`.  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna um identificador que pode ser usado para acessar o objeto.  
  
### <a name="remarks"></a>Comentários  
 Esse wrapper chama o `CreateFileTransacted` função.  
  
##  <a name="deletefile"></a>DeleteFile  
 Exclui um arquivo existente como uma operação transacionada.  
  
```
inline BOOL DeleteFile(LPCTSTR lpFileName);
```  
  
### <a name="parameters"></a>Parâmetros  
 `lpFileName`  
 O nome do arquivo a ser excluído.  
  
### <a name="remarks"></a>Comentários  
 Esse wrapper chama o `DeleteFileTransacted` função.  
  
##  <a name="findfirstfile"></a>FindFirstFile  
 Pesquisa um diretório para um arquivo ou subdiretório como uma operação transacionada.  
  
```
inline HANDLE FindFirstFile(
  LPCTSTR lpFileName,
  WIN32_FIND_DATA* pNextInfo);
```  
  
### <a name="parameters"></a>Parâmetros  
 `lpFileName`  
 O diretório ou o caminho e o nome do arquivo para procurar. Este parâmetro pode incluir caracteres curinga, como um asterisco (*) ou um (do ponto de interrogação).  
  
 `pNextInfo`  
 Um ponteiro para a estrutura WIN32_FIND_DATA que recebe informações sobre um arquivo encontrado ou subdiretório.  
  
### <a name="return-value"></a>Valor de retorno  
 Se a função obtiver êxito, o valor de retorno é um identificador de pesquisa usado em uma chamada subsequente para `FindNextFile` ou `FindClose`. Se a função falhar ou se não conseguir localizar os arquivos da cadeia de pesquisa no `lpFileName` parâmetro, o valor de retorno será INVALID_HANDLE_VALUE.  
  
### <a name="remarks"></a>Comentários  
 Esse wrapper chama o `FindFirstFileTransacted` função.  
  
##  <a name="getfileattributes"></a>GetFileAttributes  
 Recupera os atributos de sistema de arquivo para um arquivo ou diretório especificado como uma operação transacionada.  
  
```
inline DWORD GetFileAttributes(LPCTSTR lpFileName);
```  
  
### <a name="parameters"></a>Parâmetros  
 `lpFileName`  
 O nome do arquivo ou diretório.  
  
### <a name="remarks"></a>Comentários  
 Esse wrapper chama o `GetFileAttributesTransacted` função.  
  
##  <a name="getfileattributesex"></a>GetFileAttributesEx  
 Recupera os atributos de sistema de arquivo para um arquivo ou diretório especificado como uma operação transacionada.  
  
```
inline BOOL GetFileAttributesEx(
    LPCTSTR lpFileName,
    GET_FILEEX_INFO_LEVELS fInfoLevelId,
    LPVOID lpFileInformation);
```  
  
### <a name="parameters"></a>Parâmetros  
 `lpFileName`  
 O nome do arquivo ou diretório.  
  
 `fInfoLevelId`  
 O nível de informações de atributo devem ser recuperadas.  
  
 `lpFileInformation`  
 Um ponteiro para um buffer que receberá as informações de atributo. O tipo de informações de atributo que são armazenadas nesse buffer é determinado pelo valor de `fInfoLevelId`. Se o `fInfoLevelId` parâmetro for GetFileExInfoStandard, esse parâmetro aponta para uma estrutura WIN32_FILE_ATTRIBUTE_DATA.  
  
### <a name="remarks"></a>Comentários  
 Esse wrapper chama o `GetFileAttributesTransacted` função.  
  
##  <a name="gethandle"></a>GetHandle  
 Retorna o identificador da transação.  
  
```
HANDLE GetHandle() const;
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna o identificador de transação para uma classe. Retorna `NULL` se o `CAtlTransactionManager` não está anexado a um identificador.  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="isfallback"></a>IsFallback  
 Determina se as chamadas de fallback estão habilitadas.  
  
```
BOOL IsFallback() const;
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna `TRUE` é a classe oferece suporte a chamadas de retorno. `FALSE`Caso contrário.  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="m_bfallback"></a>m_bFallback  
 `TRUE`Se houver suporte para o fallback; `FALSE` caso contrário.  
  
```
BOOL m_bFallback;
```  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="m_htransaction"></a>m_hTransaction  
 O identificador da transação.  
  
```
HANDLE m_hTransaction;
```  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="movefile"></a>MoveFile  
 Move um arquivo existente ou um diretório, incluindo seus filhos, como uma operação transacionada.  
  
```
inline BOOL MoveFile(LPCTSTR lpOldFileName, LPCTSTR lpNewFileName);
```  
  
### <a name="parameters"></a>Parâmetros  
 `lpOldFileName`  
 O nome atual do arquivo ou diretório no computador local.  
  
 `lpNewFileName`  
 O novo nome para o arquivo ou diretório. Esse nome não deve existir. Pode ser um novo arquivo em uma unidade ou um sistema de arquivos diferente. Um novo diretório deve estar na mesma unidade.  
  
### <a name="remarks"></a>Comentários  
 Esse wrapper chama o `MoveFileTransacted` função.  
  
##  <a name="regcreatekeyex"></a>RegCreateKeyEx  
 Cria uma chave do Registro especificada e a associa a uma transação. Se a chave já existir, a função é aberto.  
  
```
inline LSTATUS RegCreateKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD dwReserved,
    LPTSTR lpClass,
    DWORD dwOptions,
    REGSAM samDesired,
    CONST LPSECURITY_ATTRIBUTES lpSecurityAttributes,
    PHKEY phkResult,
    LPDWORD lpdwDisposition);
```  
  
### <a name="parameters"></a>Parâmetros  
 `hKey`  
 Um identificador para uma chave do Registro aberta.  
  
 `lpSubKey`  
 O nome de uma subchave que essa função abre ou cria.  
  
 `dwReserved`  
 Esse parâmetro é reservado e deve ser zero.  
  
 `lpClass`  
 A classe definida pelo usuário dessa chave. Esse parâmetro pode ser ignorado. Esse parâmetro pode ser NULL.  
  
 `dwOptions`  
 Esse parâmetro pode ser um dos seguintes valores: REG_OPTION_BACKUP_RESTORE, REG_OPTION_NON_VOLATILE ou REG_OPTION_VOLATILE.  
  
 `samDesired`  
 Uma máscara que especifica os direitos de acesso para a chave.  
  
 `lpSecurityAttributes`  
 Ponteiro para uma estrutura SECURITY_ATTRIBUTES que determina se o identificador retornado pode ser herdado por processos filhos. Se `lpSecurityAttributes` é `NULL`, o identificador não pode ser herdado.  
  
 `phkResult`  
 Um ponteiro para uma variável que recebe um identificador para a chave aberto ou criado. Se a chave não é uma das chaves de registro predefinidos, chame o `RegCloseKey` depois de terminar de usar o identificador de função.  
  
 `lpdwDisposition`  
 Um ponteiro para uma variável que recebe um dos seguintes valores de disposição: REG_CREATED_NEW_KEY ou REG_OPENED_EXISTING_KEY.  
  
### <a name="return-value"></a>Valor de retorno  
 Se a função obtiver êxito, o valor de retorno é ERROR_SUCCESS. Se a função falhar, o valor de retorno é um código de erro diferente de zero definido no Winerror. h.  
  
### <a name="remarks"></a>Comentários  
 Esse wrapper chama o `RegCreateKeyTransacted` função.  
  
##  <a name="regdeletekey"></a>RegDeleteKey  
 Exclui uma subchave e seus valores de modo de exibição específico de plataforma especificado do registro como uma operação transacionada.  
  
```
inline LSTATUS RegDeleteKeyEx(HKEY hKey, LPCTSTR lpSubKey);
```  
  
### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`hKey`|Um identificador para uma chave do Registro aberta.|  
|`lpSubKey`|O nome da chave a ser excluída.|  
  
### <a name="return-value"></a>Valor de retorno  
 Se a função obtiver êxito, o valor de retorno é ERROR_SUCCESS. Se a função falhar, o valor de retorno é um código de erro diferente de zero definido no Winerror. h.  
  
### <a name="remarks"></a>Comentários  
 Esse wrapper chama o `RegDeleteKeyTransacted` função.  
  
##  <a name="regopenkeyex"></a>RegOpenKeyEx  
 Abre a chave do Registro especificada e a associa a uma transação.  
  
```
inline LSTATUS RegOpenKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD ulOptions,
    REGSAM samDesired,
    PHKEY phkResult);
```  
  
### <a name="parameters"></a>Parâmetros  
 `hKey`  
 Um identificador para uma chave do Registro aberta.  
  
 `lpSubKey`  
 O nome da subchave do registro a ser aberto.  
  
 `ulOptions`  
 Esse parâmetro é reservado e deve ser zero.  
  
 `samDesired`  
 Uma máscara que especifica os direitos de acesso para a chave.  
  
 `phkResult`  
 Um ponteiro para uma variável que recebe um identificador para a chave aberto ou criado. Se a chave não é uma das chaves de registro predefinidos, chame o `RegCloseKey` depois de terminar de usar o identificador de função.  
  
### <a name="return-value"></a>Valor de retorno  
 Se a função obtiver êxito, o valor de retorno é ERROR_SUCCESS. Se a função falhar, o valor de retorno é um código de erro diferente de zero definido no Winerror. h  
  
### <a name="remarks"></a>Comentários  
 Esse wrapper chama o `RegOpenKeyTransacted` função.  
  
##  <a name="rollback"></a>Reversão  
 Solicitações que a transação ser revertida.  
  
```
inline BOOL Rollback();
```  
  
### <a name="return-value"></a>Valor de retorno  
 `TRUE` caso bem-sucedido; caso contrário, `FALSE`.  
  
### <a name="remarks"></a>Comentários  
 Esse wrapper chama o `RollbackTransaction` função.  
  
##  <a name="setfileattributes"></a>SetFileAttributes  
 Define os atributos de um arquivo ou diretório como uma operação transacionada.  
  
```
inline BOOL SetFileAttributes(LPCTSTR lpFileName, DWORD dwAttributes);
```  
  
### <a name="parameters"></a>Parâmetros  
 `lpFileName`  
 O nome do arquivo ou diretório.  
  
 `dwAttributes`  
 Os atributos de arquivo definido para o arquivo. Para obter mais informações, consulte [SetFileAttributesTransacted](http://go.microsoft.com/fwlink/linkid=158699).  
  
### <a name="remarks"></a>Comentários  
 Esse wrapper chama o `SetFileAttributesTransacted` função.  
  
## <a name="see-also"></a>Consulte também  
 [Componentes da área de trabalho COM de ATL](../../atl/atl-com-desktop-components.md)
