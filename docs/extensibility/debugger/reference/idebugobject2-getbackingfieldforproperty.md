---
title: IDebugObject2::GetBackingFieldForProperty | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7729f55c93274796d3c81f280618653b873bc40b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Obtient le champ ou la variable (le cas échéant) qui peut être stockage de la propriété représentée par cet objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppObject`  
 [out] Un [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) objet décrivant le champ de stockage.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Le [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) objet représente une propriété de classe du code managé, autrement dit, une méthode avec une commande get et/ou l’accesseur set. Ces propriétés requièrent généralement une variable qui doit contenir la valeur manipulée par la propriété. Cette variable est connue en tant que le champ de stockage. S’il n’existe aucun champ de stockage pour l’objet, puis assurez-vous que retourner une valeur null : certains appelants peuvent ne pas tenir compte la valeur de retour mais ressemblera à la place pour voir si une valeur null a été retournée dans `ppObject`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)