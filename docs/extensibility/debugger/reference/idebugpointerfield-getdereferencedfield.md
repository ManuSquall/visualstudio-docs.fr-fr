---
title: 'IDebugPointerField :: GetDereferencedField | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9b502b83ec793733ef642585b6ded260f72aa1be
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869659"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
Cette méthode retourne le type d’objet vers lequel pointe cet objet pointeur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetDereferencedField(
   IDebugField** ppField
);
```

```csharp
int GetDereferencedField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Paramètres
`ppField`\
à Retourne un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) décrivant le type d’objet cible.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 Si, par exemple, l’objet [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) pointe vers un entier, le type [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) retourné par cette méthode décrit ce type entier.

## <a name="see-also"></a>Voir aussi
- [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
