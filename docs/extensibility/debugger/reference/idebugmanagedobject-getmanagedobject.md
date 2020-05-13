---
title: IDebugManagedObject::GetManagedObject (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::GetManagedObject
helpviewer_keywords:
- IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b7080760b174c51d62c44cd2757944948e0104ca
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727739"
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
Retourne une interface qui représente l’objet géré.

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

## <a name="parameters"></a>Paramètres
`ppManagedObject`\
[out] Retourne une interface qui représente l’objet géré.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK; autrement, renvoie un code d’erreur.

## <a name="remarks"></a>Notes
 L’interface restituée de cette méthode peut être demandée pour n’importe quelle interface implémentée par la classe gérée, permettant à ses méthodes d’être appelées.

## <a name="see-also"></a>Voir aussi
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
