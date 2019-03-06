---
title: IDebugPointerObject::Dereference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f01e863d03f6179ef4c15f50521cc72ba21f5740
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56706585"
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

#### <a name="parameters"></a>Paramètres
 `dwIndex`

 [in] Un décalage d’octet simple à partir du début de l’objet désigné.

 `ppObject`

 [out] Retourne un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) de l’objet qui représente l’objet vers lequel pointe, ainsi que décalage, le cas échéant.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur. Retourne E_FAIL si cet objet ne pointe pas vers un autre objet.

## <a name="remarks"></a>Notes
 L’objet vers lequel pointé peut être un type primitif ou un type plus complexe comme une classe ou structure.

## <a name="see-also"></a>Voir aussi
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)