---
title: IDebugManagedObject::SetFromManagedObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 92b1e794dea8d64a8c41dfd4a85627c642d438f0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53901777"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
Définit la valeur de l’instance de l’objet de classe de valeur de l’instance de la classe de la valeur fournie en tant que paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetFromManagedObject(   
   IUnknown* pManagedObject  
);  
```  
  
```csharp  
int SetFromManagedObject(  
   object pManagedObject  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pManagedObject`  
 [in] Une interface qui représente l’objet managé contenant la nouvelle valeur.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est utilisée pour modifier l’objet managé, tel que représenté par le [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) objet.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)