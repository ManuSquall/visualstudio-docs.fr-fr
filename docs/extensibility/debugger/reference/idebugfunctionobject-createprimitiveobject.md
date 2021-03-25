---
description: Crée un objet de données primitif, tel qu’un entier simple.
title: 'IDebugFunctionObject :: CreatePrimitiveObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c706d8908f1fa8776d1d7304772a0c5eec03bd2d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073493"
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
Crée un objet de données primitif, tel qu’un entier simple.

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
dans Valeur de l’énumération [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) représentant le type de primitive à créer.

`ppObject`\
à Retourne un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) représentant l’objet nouvellement créé.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Appelez cette méthode pour créer un objet qui représente un objet primitif qui est un paramètre de la fonction qui est représenté par l’interface [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) . Par exemple, si la chaîne d’expression est « myString (5) », cette méthode est utilisée pour créer un objet représentant l’entier 5.

## <a name="see-also"></a>Voir aussi
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
