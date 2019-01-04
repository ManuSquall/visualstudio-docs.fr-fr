---
title: IDebugDocumentPosition2::IsPositionInDocument | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
helpviewer_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 12c7399c85b4ad4f1bc84ae9c400c04be23837ff
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53892038"
---
# <a name="idebugdocumentposition2ispositionindocument"></a>IDebugDocumentPosition2::IsPositionInDocument
Détermine si la position du document se trouve dans le document donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsPositionInDocument(   
   IDebugDocument2* pDoc  
);  
```  
  
```csharp  
int IsPositionInDocument(   
   IDebugDocument2 pDoc  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pDoc`  
 [in] Le [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) objet qui représente le candidat de document conteneur.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est utilisée principalement dans la définition des points d’arrêt dans [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaces. Comme les documents sont chargés, la position du point d’arrêt est appelée pour déterminer si le document contient cette position.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)