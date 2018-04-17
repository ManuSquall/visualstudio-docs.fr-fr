---
title: IDebugObject2::GetAlias | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b5917e0f78a2872cbd684830c8a03b1156a83734
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
Obtient l’alias associé à cet objet, le cas échéant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAlias(  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int GetAlias(  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppAlias`  
 [out] Retourne un [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) l’objet représentant l’alias de cet objet ; sinon, retourne une valeur null.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Un alias pour un objet est créé par un appel à la [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)