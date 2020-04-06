---
title: IDebugObject::GetManagedDebugObject ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67d0d7a8642c9dd90067b0e197f420d4cc821faa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726691"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
Crée une copie de l’objet géré dans l’espace d’adresse du moteur de débogé.

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

## <a name="parameters"></a>Paramètres
`ppObject`\
[out] Retourne un objet [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) représentant l’objet géré nouvellement créé.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK; autrement, renvoie un code d’erreur. Retourne E_FAIL si cet [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) ne représente pas une instance de classe de valeur gérée.

## <a name="remarks"></a>Notes
 Cet objet [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) doit représenter un instance `System.Decimal` de classe de valeur gérée, comme une instance. En ayant une copie locale, les frais généraux d’appel [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) sont éliminés.

## <a name="see-also"></a>Voir aussi
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
