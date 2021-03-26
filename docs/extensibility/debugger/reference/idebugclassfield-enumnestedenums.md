---
description: Crée un énumérateur pour les énumérateurs imbriqués de cette classe.
title: 'IDebugClassField :: EnumNestedEnums | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b2e0d908c88b82e9ed706ab919050e1f4943df0c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088560"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Crée un énumérateur pour les énumérateurs imbriqués de cette classe.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumNestedEnums(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedEnums(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Paramètres
`ppEnum`\
à Retourne un objet [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste des énumérations imbriquées. Retourne une valeur null s’il n’existe aucune énumération imbriquée.

## <a name="return-value"></a>Valeur renvoyée
En cas de réussite, retourne S_OK ou retourne S_FALSE s’il n’y a pas d’énumérateurs imbriqués. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
Chaque élément de l’énumération est un objet [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) décrivant une énumération imbriquée.

Une énumération déclarée dans une classe est considérée comme une énumération imbriquée. Prenons l’exemple suivant :

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

La `EnumNestedEnums` méthode retourne un objet [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) qui contient un objet [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) qui représente l' `NestedEnum` énumération.

## <a name="see-also"></a>Voir aussi
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
