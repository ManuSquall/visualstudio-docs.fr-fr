---
title: IDebugObject::IsNullReference ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e4b6e5f2d28d27deb5e4e1ff8278a071ff9110fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726516"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
Teste si cet objet est une référence nulle.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsNullReference( 
   BOOL* pfIsNull
);
```

```csharp
int IsNullReference(
   out int pfIsNull
);
```

## <a name="parameters"></a>Paramètres
`pfIsNull`\
[out] Retourne non-zéro`TRUE`( ) si cet objet est une référence nulle; autrement, retourne`FALSE`zéro ( ).

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK; autrement, renvoie un code d’erreur.

## <a name="remarks"></a>Notes
 Une référence nulle signifie un objet vide ou un objet qui n’a pas été assigné à.

## <a name="see-also"></a>Voir aussi
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
