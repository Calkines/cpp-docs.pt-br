---
title: Classe CArchiveException | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CArchiveException
- AFX/CArchiveException
- AFX/CArchiveException::CArchiveException
- AFX/CArchiveException::m_cause
- AFX/CArchiveException::m_strFileName
dev_langs:
- C++
helpviewer_keywords:
- exceptions [C++], serialization
- serialization [C++], exceptions
- CArchiveException class
- exceptions [C++], archive
- archive exceptions [C++]
ms.assetid: da31a127-e86c-41d1-b0b6-bed0865b1b49
caps.latest.revision: 21
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: e927bea5b8d9e6dbaafb191f6c3bdcf0f0d076cc
ms.lasthandoff: 02/25/2017

---
# <a name="carchiveexception-class"></a>Classe CArchiveException
Representa uma condição de exceção de serialização  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class CArchiveException : public CException  
```  
  
## <a name="members"></a>Membros  
  
### <a name="public-constructors"></a>Construtores públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CArchiveException::CArchiveException](#carchiveexception)|Constrói um objeto `CArchiveException`.|  
  
### <a name="public-data-members"></a>Membros de Dados Públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CArchiveException::m_cause](#m_cause)|Indica a causa da exceção.|  
|[CArchiveException::m_strFileName](#m_strfilename)|Especifica o nome do arquivo para essa condição de exceção.|  
  
## <a name="remarks"></a>Comentários  
 O `CArchiveException` classe inclui um membro de dados pública que indicam a causa da exceção.  
  
 `CArchiveException`objetos são construídos e lançados dentro [CArchive](../../mfc/reference/carchive-class.md) funções de membro. Você pode acessar esses objetos dentro do escopo de um **CATCH** expressão. O código de causa é independente do sistema operacional. Para obter mais informações sobre o processamento de exceção, consulte [tratamento de exceção (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarquia de herança  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CArchiveException`  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** AFX. h  
  
##  <a name="carchiveexception"></a>CArchiveException::CArchiveException  
 Constrói uma `CArchiveException` objeto, armazenar o valor de `cause` no objeto.  
  
```  
CArchiveException(
    int cause = CArchiveException::none,  
    LPCTSTR lpszArchiveName = NULL);
```  
  
### <a name="parameters"></a>Parâmetros  
 `cause`  
 Uma variável do tipo enumerado que indica o motivo da exceção. Para obter uma lista dos enumeradores, consulte o [m_cause](#m_cause) membro de dados.  
  
 `lpszArchiveName`  
 Aponta para uma cadeia de caracteres que contém o nome do `CArchive` objeto que causou a exceção.  
  
### <a name="remarks"></a>Comentários  
 Você pode criar um `CArchiveException` do objeto no heap e lançá-la ou permitir que a função global [AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception) manipulá-lo para você.  
  
 Não use esse construtor diretamente. em vez disso, chame a função global `AfxThrowArchiveException`.  
  
##  <a name="m_cause"></a>CArchiveException::m_cause  
 Especifica a causa da exceção.  
  
```  
int m_cause;  
```  
  
### <a name="remarks"></a>Comentários  
 Esse membro de dados é uma variável pública do tipo `int`. Seus valores são definidos por um `CArchiveException` tipo enumerado. Os enumeradores e seus significados são os seguintes:  
  
- **CArchiveException::none** nenhum erro ocorreu.  
  
- **CArchiveException::genericException** erro não especificado.  
  
- **CArchiveException::readOnly** tentou gravar em um arquivo aberto para carregamento.  
  
- **CArchiveException::endOfFile** atingida final do arquivo durante a leitura de um objeto.  
  
- **CArchiveException::writeOnly** tentou ler de um arquivo aberto para armazenamento.  
  
- **CArchiveException::badIndex** formato de arquivo inválido.  
  
- **CArchiveException::badClass** tentou ler um objeto em um objeto do tipo errado.  
  
- **CArchiveException::badSchema** tentou ler um objeto com uma versão diferente da classe.  
  
    > [!NOTE]
    >  Esses enumeradores de causa de `CArchiveException` são diferentes dos enumeradores de causa de `CFileException`.  
  
    > [!NOTE]
    > **CArchiveException::generic** foi preterido. Use **genericException** em vez disso. Se **genérico** é usada em um aplicativo e compilado com /clr, haverá erros de sintaxe que não são fáceis de decifrar.  
  
##  <a name="m_strfilename"></a>CArchiveException::m_strFileName  
 Especifica o nome do arquivo para essa condição de exceção.  
  
```  
CString m_strFileName;  
```  
  
## <a name="see-also"></a>Consulte também  
 [Classe CException](../../mfc/reference/cexception-class.md)   
 [Gráfico de hierarquia](../../mfc/hierarchy-chart.md)   
 [Classe CArchive](../../mfc/reference/carchive-class.md)   
 [AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)   
 [Processamento de exceção](../../mfc/reference/exception-processing.md)

