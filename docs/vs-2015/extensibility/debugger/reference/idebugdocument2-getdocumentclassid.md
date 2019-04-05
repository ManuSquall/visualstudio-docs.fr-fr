---
title: IDebugDocument2::GetDocumentClassID | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetDocumentClassID
helpviewer_keywords:
- IDebugDocument2::GetDocumentClassID
ms.assetid: 111c2b85-ebfa-487f-b896-2ec4a3eac4d1
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4ac97400d09e77b0910b945d78c2f0cf28073a01
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58949403"
---
# <a name="idebugdocument2getdocumentclassid"></a>IDebugDocument2::GetDocumentClassID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient l’identificateur de classe du document.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetDocumentClassID(   
   CLSID* pclsid  
);  
```  
  
```csharp  
int GetDocumentClassID(   
   out Guid pclsid  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pclsid`  
 [out] Retourne un GUID représentant l’ID de classe du document.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Le GUID de classe peut être utilisé pour instancier des classes individuelles, chacune représentant un document.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
