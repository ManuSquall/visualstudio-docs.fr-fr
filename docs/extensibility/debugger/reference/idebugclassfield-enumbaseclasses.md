---
title: 'IDebugClassField :: EnumBaseClasses | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b8648890e030799b985a4e917be8caf85292528a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947097"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
Crée un énumérateur pour les classes de base de cette classe.

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

à Retourne un objet [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste des classes de base. Retourne une valeur null s’il n’existe aucune classe de base.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK, retourne S_SH_NO_BASE_CLASSES s’il n’existe aucune classe de base (et que le `ppEnum` paramètre est défini sur une valeur null); sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Les classes de base de l’objet énumérateur sont spécifiées dans l’ordre de la classe de base la plus immédiate (ou la plus dérivée) à la classe de base distante la plus éloignée. Par exemple, étant donné les classes C++ :

```
class Root { }
class Level1 : Root { }
class Level2 : Level1 { }
class MyClass : Level2 { }
```

 L’énumération retourne les classes de base dans l’ordre `Level2` , `Level1` , `Root` .

## <a name="see-also"></a>Voir aussi
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
