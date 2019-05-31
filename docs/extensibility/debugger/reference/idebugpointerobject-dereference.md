---
title: IDebugPointerObject::Dereference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 381c6f392cccb398497204cc5772c5f9a00fd5b0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331660"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Obtient l’objet désigné.

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
[in] Un décalage d’octet simple à partir du début de l’objet désigné.

`ppObject`\
[out] Retourne un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) de l’objet qui représente l’objet vers lequel pointe, ainsi que décalage, le cas échéant.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur. Retourne E_FAIL si cet objet ne pointe pas vers un autre objet.

## <a name="remarks"></a>Notes
 L’objet vers lequel pointé peut être un type primitif ou un type plus complexe comme une classe ou structure.

## <a name="see-also"></a>Voir aussi
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)