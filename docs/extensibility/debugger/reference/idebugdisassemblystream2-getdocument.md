---
title: IDebugDisassemblyStream2::GetDocument | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2::GetDocument
helpviewer_keywords:
- IDebugDisassemblyStream2::GetDocument
ms.assetid: 3d039a44-ebaa-4413-ac18-7cfd92c408bd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9474ebf733e134363c9b2fec999432edbcd1066a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53894780"
---
# <a name="idebugdisassemblystream2getdocument"></a>IDebugDisassemblyStream2::GetDocument
Obtient le document source associé au flux d’entrée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDocument(   
   BSTR              bstrDocumentUrl,  
   IDebugDocument2** ppDocument  
);  
```  
  
```csharp  
int GetDocument(   
   string              bstrDocumentUrl,  
   out IDebugDocument2 ppDocument  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `bstrDocumentUrl`  
 [in] L’URL du document.  
  
 `ppDocument`  
 [out] Retourne un [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) objet qui représente le document.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est implémentée par les moteurs de débogage qui contient des documents de texte qui ne sont pas stockées dans un fichier réel.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)