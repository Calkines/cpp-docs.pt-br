---
title: ptr::Release
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ptr.Release
- ptr::Release
- msclr.com.ptr.Release
- msclr::com::ptr::Release
helpviewer_keywords:
- Release method
ms.assetid: 7855781e-e4f6-4ad5-86a5-a81e2c3d90db
ms.openlocfilehash: 276d79688213864c31cf04a59f48a8799bf84371
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544918"
---
# <a name="ptrrelease"></a>ptr::Release

Libera todas as referências de propriedade no objeto COM.

## <a name="syntax"></a>Sintaxe

```
void Release();
```

## <a name="remarks"></a>Comentários

Chamar essa função libera a propriedade de todas as referências no objeto COM e define o identificador interno para o objeto COM para `nullptr`.  Se nenhuma outra referência no objeto COM existir, ele será destruído.

## <a name="example"></a>Exemplo

Este exemplo implementa uma classe CLR que usa um `com::ptr` encapsular seu membro privado `IXMLDOMDocument` objeto.  O `ReplaceDocument` função de membro usa `Release` para liberar qualquer objeto de documento anterior antes de anexar o novo documento.

```
// comptr_release.cpp
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
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // replace currently held COM object with another one
   void ReplaceDocument(IXMLDOMDocument* pDoc) {
      // release current document object
      m_ptrDoc.Release();
      // attach the new document object
      m_ptrDoc.Attach(pDoc);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that creates a raw XML DOM Document object
IXMLDOMDocument* CreateDocument() {
   IXMLDOMDocument* pDoc = NULL;
   Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
      CLSCTX_INPROC_SERVER, IID_IXMLDOMDocument, (void**)&pDoc));
   return pDoc;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // get another document object from unmanaged function and
      // store it in place of the one held by our ref class
      pDoc = CreateDocument();
      doc.ReplaceDocument(pDoc);
      // no further need for raw object reference
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="requirements"></a>Requisitos

**Arquivo de cabeçalho** \<msclr\com\ptr.h >

**Namespace** msclr::com

## <a name="see-also"></a>Consulte também

[Membros ptr](../dotnet/ptr-members.md)<br/>
[ptr::Detach](../dotnet/ptr-detach.md)