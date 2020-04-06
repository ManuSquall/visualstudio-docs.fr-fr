---
title: IDebugClassField::EnumBaseClasses (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 12317c549050be31ac9e19bc7b3d8a6683f743d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734475"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
Crée un enumérateur pour les classes de base de cette classe.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumBaseClasses( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumBaseClasses(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Paramètres
`ppEnum`\

[out] Retourne un objet [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste des classes de base. Retourne une valeur nulle s’il n’y a pas de classes de base.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK, les retours S_SH_NO_BASE_CLASSES `ppEnum` s’il n’y a pas de classes de base (et le paramètre est fixé à une valeur nulle); autrement, renvoie un code d’erreur.

## <a name="remarks"></a>Notes
 Les classes de base de l’objet d’enumérateur sont spécifiées dans l’ordre de la classe de base la plus immédiate (ou la plus dérivée) à la classe de base la plus éloignée. Par exemple, compte tenu des cours de CMD :

```
class Root { }
class Level1 : Root { }
class Level2 : Level1 { }
class MyClass : Level2 { }
```

 L’énumération rendrait les classes `Level2`de `Level1` `Root`base dans l’ordre , .

## <a name="see-also"></a>Voir aussi
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
