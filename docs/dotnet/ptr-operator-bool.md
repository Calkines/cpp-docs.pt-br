---
title: 'bool PTR:: | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ptr::operator bool
- ptr.operator bool
- operator bool
- msclr::com::ptr::operator bool
- msclr.com.ptr.operator bool
dev_langs: C++
helpviewer_keywords: ptr::operator bool
ms.assetid: 31123377-6ecd-4cef-9b75-3db3996fbcd1
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5aaec44d5b8f2e8b43a94fa5d0e8b4250ac7bf49
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="ptroperator-bool"></a>Bool ptr::operator
Operador para o uso de `com::ptr` em uma expressão condicional.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
operator bool();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 `true`Se o objeto COM propriedade é válido. `false` caso contrário.  
  
## <a name="remarks"></a>Comentários  
 O objeto COM propriedade é válido se não for `nullptr`.  
  
 Esse operador realmente converte em `_detail_class::_safe_bool` que é mais seguro que `bool` porque ele não pode ser convertido em um tipo integral.  
  
## <a name="example"></a>Exemplo  
 Este exemplo implementa uma classe CLR que usa um `com::ptr` para incluir o membro privado `IXMLDOMDocument` objeto. O `CreateInstance` usa a função de membro `operator bool` depois de criar o novo objeto de documento para determinar se ele é válido e grava no console se ele for.  
  
```  
// comptr_op_bool.cpp  
// compile with: /clr /link msxml2.lib  
#include <msxml2.h>  
#include <msclr\com\ptr.h>  
  
#import <msxml3.dll> raw_interfaces_only  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
using namespace msclr;  
  
// a ref class that uses a com::ptr to contain an   
// IXMLDOMDocument object  
ref class XmlDocument {  
public:  
   void CreateInstance(String^ progid) {  
      if (!m_ptrDoc) {  
         m_ptrDoc.CreateInstance(progid);     
         if (m_ptrDoc) { // uses operator bool  
            Console::WriteLine("DOM Document created.");  
         }  
      }  
   }  
  
   // note that the destructor will call the com::ptr destructor  
   // and automatically release the reference to the COM object  
  
private:  
   com::ptr<IXMLDOMDocument> m_ptrDoc;  
};  
  
// use the ref class to handle an XML DOM Document object  
int main() {  
   try {  
      XmlDocument doc;  
      // create the instance from a progid string  
      doc.CreateInstance("Msxml2.DOMDocument.3.0");  
   }  
   catch (Exception^ e) {  
      Console::WriteLine(e);     
   }  
}  
```  
  
```Output  
DOM Document created.  
```  
  
## <a name="requirements"></a>Requisitos  
 **Arquivo de cabeçalho** \<msclr\com\ptr.h >  
  
 **Namespace** msclr::com  
  
## <a name="see-also"></a>Consulte também  
 [Membros PTR](../dotnet/ptr-members.md)   
 [ptr::operator!](../dotnet/ptr-operator-logical-not.md)