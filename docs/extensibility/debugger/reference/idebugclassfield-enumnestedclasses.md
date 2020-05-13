---
title: IDebugClassField::EnumNestedClasses (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3e6ef918b55d8b311380264d688085b0d2803601
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734429"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
Crée un enumérateur pour les classes imbriquées dans cette classe.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumNestedClasses(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedClasses(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Paramètres
`ppEnum`\
[out] Retourne un objet [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste des classes imbriquées. Retourne une valeur nulle s’il n’y a pas de classes imbriquées.

## <a name="return-value"></a>Valeur de retour
En cas de succès, les retours S_OK ou retournent S_FALSE s’il n’y a pas de classes imbriquées. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
Chaque élément de l’énumération est un objet [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) décrivant une classe imbriquée.

Une classe imbriquée est une classe définie à l’intérieur d’une autre classe. Par exemple :

```
class RootClass {
   class NestedClass { }
};
```

Le recensement [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) contiendrait `NestedClass` un objet représentant la classe.

## <a name="see-also"></a>Voir aussi
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
