---
title: IDebugObject2::GetBackingFieldForProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5eadbed61638ff1442c4ed7033426e245abf930a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62536384"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Obtient le champ ou la variable (le cas échéant) qui peut être sauvegarde de la propriété représentée par cet objet.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetBackingFieldForProperty(
   IDebugObject2** ppObject
);
```

```csharp
int GetBackingFieldForProperty(
   out IDebugObject2 ppObject
);
```

#### <a name="parameters"></a>Paramètres
 `ppObject`

 [out] Un [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) objet décrivant le champ de stockage.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Le [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) objet représente une propriété de classe de code managé, autrement dit, une méthode avec une commande get et/ou l’accesseur set. Ces propriétés requièrent généralement une variable pour contenir la valeur manipulée par la propriété. Cette variable est connue en tant que le champ de stockage. S’il n’existe aucun champ de stockage pour l’objet, veillez à retourner une valeur null : certains les appelants ne peuvent pas payer une attention particulière à la valeur de retour mais ressemblera à la place pour voir si une valeur null a été retournée dans `ppObject`.

## <a name="see-also"></a>Voir aussi
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)