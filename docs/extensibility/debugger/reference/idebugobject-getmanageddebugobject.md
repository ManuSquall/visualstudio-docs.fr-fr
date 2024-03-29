---
description: Crée une copie de l’objet managé dans l’espace d’adressage du moteur de débogage.
title: 'IDebugObject :: GetManagedDebugObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 56961930e08e7d53dfe387c00642ae7266c230c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081917"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
Crée une copie de l’objet managé dans l’espace d’adressage du moteur de débogage.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetManagedDebugObject( 
   IDebugManagedObject** ppObject
);
```

```csharp
int GetManagedDebugObject(
   out IDebugManagedObject ppObject
);
```

## <a name="parameters"></a>Paramètres
`ppObject`\
à Retourne un objet [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) qui représente l’objet managé nouvellement créé.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur. Retourne E_FAIL si ce [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) ne représente pas une instance de classe de valeur managée.

## <a name="remarks"></a>Notes
 Cet objet [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) doit représenter une instance de classe de valeur managée, telle qu’une `System.Decimal` instance. En ayant une copie locale, la surcharge liée à l’appel de [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) est éliminée.

## <a name="see-also"></a>Voir aussi
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
