---
title: IDebugFunctionObject::CreatePrimitiveObject (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 24b26a072a3bebda2d01a89baaf2910de96e77d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728534"
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
Crée un objet de données primitif, comme un simple intégrant.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreatePrimitiveObject( 
   OBJECT_TYPE    ot,
   IDebugObject** ppObject
);
```

```csharp
int CreatePrimitiveObject(
   enum_OBJECT_TYPE ot,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Paramètres
`ot`\
[dans] Une valeur de [l’énumération OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) représentant le type de primitif à créer.

`ppObject`\
[out] Retourne un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) représentant l’objet nouvellement créé.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK; autrement, renvoie un code d’erreur.

## <a name="remarks"></a>Notes
 Appelez cette méthode pour créer un objet qui représente un objet primitif qui est un paramètre à la fonction qui est représenté par [l’interface IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md) Par exemple, si la chaîne d’expression est "myString(5)", cette méthode serait utilisée pour créer un objet représentant l’intégriste 5.

## <a name="see-also"></a>Voir aussi
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
