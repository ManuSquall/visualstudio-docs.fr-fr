---
title: IDebugManagedObject::GetManagedObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::GetManagedObject
helpviewer_keywords:
- IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6df3a4f69c62e7681eade705186c802a225f060
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720770"
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
Retourne une interface qui représente l’objet managé.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetManagedObject( 
   IUnknown** ppManagedObject
);
```

```cpp
int GetManagedObject(
   out object ppManagedObject
);
```

#### <a name="parameters"></a>Paramètres
 `ppManagedObject`

 [out] Retourne une interface qui représente l’objet managé.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 L’interface retournée par cette méthode peut être interrogée pour n’importe quelle interface implémentée par la classe managée, ce qui permet de ses méthodes à appeler.

## <a name="see-also"></a>Voir aussi
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)