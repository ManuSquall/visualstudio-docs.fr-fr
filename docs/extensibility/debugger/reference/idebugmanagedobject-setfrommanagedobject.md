---
title: IDebugManagedObject::SetFromManagedObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dbaaf27222754d4a68d7de6367a2c0d7a1a8be73
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66210630"
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

## <a name="parameters"></a>Paramètres
`pManagedObject`\
[in] Une interface qui représente l’objet managé contenant la nouvelle valeur.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode est utilisée pour modifier l’objet managé, tel que représenté par le [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) objet.

## <a name="see-also"></a>Voir aussi
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)