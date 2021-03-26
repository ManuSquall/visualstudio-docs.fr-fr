---
description: Obtient l’objet vers lequel pointe.
title: IDebugPointerObject ::D votre | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 226e8471d83208e9647578fca0fa16cc7b49e4eb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087637"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Obtient l’objet vers lequel pointe.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT DeReference( 
   DWORD          dwIndex,
   IDebugObject** ppObject
);
```

```csharp
int Dereference(
   uint             dwIndex,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Paramètres
`dwIndex`\
dans Offset d’octet simple à partir du début de l’objet vers lequel pointe.

`ppObject`\
à Retourne un objet [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) représentant l’objet vers lequel pointe, le décalage, le cas échéant.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur. Retourne E_FAIL si cet objet ne pointe pas vers un autre objet.

## <a name="remarks"></a>Notes
 L’objet pointé peut être un type primitif ou plus complexe, tel qu’une classe ou une structure.

## <a name="see-also"></a>Voir aussi
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
