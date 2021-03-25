---
description: Obtient le champ ou la variable (le cas échéant) qui peut sauvegarder la propriété représentée par cet objet.
title: 'IDebugObject2 :: GetBackingFieldForProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 210381e034ccae8ab9662b77c47970af2affa095
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053800"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Obtient le champ ou la variable (le cas échéant) qui peut sauvegarder la propriété représentée par cet objet.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetBackingFieldForProperty(
   IDebugObject2** ppObject
);
```

```csharp
int GetBackingFieldForProperty(
   out IDebugObject2 ppObject
);
```

## <a name="parameters"></a>Paramètres
`ppObject`\
à Objet [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) décrivant le champ de stockage.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 L’objet [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) représente une propriété de classe de code managé, autrement dit, une méthode avec un accesseur get et/ou Set. De telles propriétés requièrent généralement une variable pour contenir la valeur manipulée par la propriété. Cette variable est connue sous le nom de champ de stockage. S’il n’y a aucun champ de stockage pour l’objet, assurez-vous de retourner une valeur NULL : certains appelants peuvent ne pas prêter attention à la valeur de retour, mais ils verront si une valeur null a été retournée dans `ppObject` .

## <a name="see-also"></a>Voir aussi
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
