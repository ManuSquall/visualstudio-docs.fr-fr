---
title: IDebugPointerObject::Dereference Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe87d5db40ce663d84c9561e89a84e6fcb1684ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725565"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Obtient l’objet pointé vers.

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
[dans] Un simple byte décalé dès le début de l’objet pointé du doigt.

`ppObject`\
[out] Renvoie un objet [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) représentant l’objet pointé, plus décalage, le cas échéant.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK; autrement, renvoie un code d’erreur. Retourne E_FAIL si cet objet ne pointe pas vers un autre objet.

## <a name="remarks"></a>Notes
 L’objet pointé vers lui peut être un type primitif ou plus complexe comme une classe ou une structure.

## <a name="see-also"></a>Voir aussi
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
