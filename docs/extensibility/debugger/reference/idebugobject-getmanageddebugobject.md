---
title: IDebugObject::GetManagedDebugObject | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject::GetManagedDebugObject
helpviewer_keywords: IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a01823a2409b15ba101ad4b55d5584e385872574
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
Crée une copie de l’objet managé dans l’espace d’adressage du moteur de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetManagedDebugObject(   
   IDebugManagedObject** ppObject  
);  
```  
  
```csharp  
int GetManagedDebugObject(  
   out IDebugManagedObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppObject`  
 [out] Retourne un [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) objet représentant l’objet managé qui vient d’être créé.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur. Retourne E_FAIL si cette [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) ne représente pas une instance de classe de valeur managé.  
  
## <a name="remarks"></a>Remarques  
 Cela [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objet doit représenter une instance de classe valeur managé, comme un `System.Decimal` instance. En ayant une copie locale, la surcharge de l’appel de [évaluer](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) est éliminé.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)