---
title: IDebugObject2::GetBackingFieldForProperty - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b5b9fed9b071f34c119c8e4a5af12c1df7990f4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726241"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Obtient le champ ou variable (le cas échéant) qui peut soutenir la propriété représentée par cet objet.

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

## <a name="parameters"></a>Paramètres
`ppObject`\
[out] Un objet [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) décrivant le champ de soutien.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK; autrement, renvoie un code d’erreur.

## <a name="remarks"></a>Notes
 [L’objet IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) représente une propriété de classe de code gérée, c’est-à-dire une méthode avec un accesseur d’accès et/ou de set. Ces propriétés nécessitent généralement une variable pour contenir la valeur manipulée par la propriété. Cette variable est connue sous le nom de champ de soutien. S’il n’y a pas de champ d’appui pour l’objet, assurez-vous de retourner une valeur nulle: certains `ppObject`appelants peuvent ne pas prêter attention à la valeur de retour, mais cherchera plutôt à voir si une valeur nulle a été retournée en .

## <a name="see-also"></a>Voir aussi
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
