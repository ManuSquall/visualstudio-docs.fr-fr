---
title: IDebugClassField::EnumNestedClasses | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75b963f7a342a9ce2b276cc03ea5dece9316ff6d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313124"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
Crée un énumérateur pour les classes imbriquées dans cette classe.

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
[out] Retourne un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objet représentant la liste des classes imbriquées. Retourne une valeur null si aucune classe imbriquée.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne S_OK, ou retourne S_FALSE s’il existe des classes imbriquées. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
Chaque élément de l’énumération est un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objet décrivant une classe imbriquée.

Une classe imbriquée est une classe définie à l’intérieur d’une autre classe. Exemple :

```
class RootClass {
   class NestedClass { }
};
```

Le [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) énumération contient un objet représentant la `NestedClass` classe.

## <a name="see-also"></a>Voir aussi
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
