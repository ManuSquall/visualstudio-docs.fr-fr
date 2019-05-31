---
title: IDebugObject::IsReadOnly | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 21c8a21f3cc85247f1cef4131768984f99fff764
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349952"
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
Détermine si cet objet est en lecture seule.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsReadOnly( 
   BOOL* pfIsReadOnly
);
```

```csharp
int IsReadOnly(
   out int pfIsReadOnly
);
```

## <a name="parameters"></a>Paramètres
`pfIsReadOnly`\
[out] Retourne zéro (`TRUE`) si cet objet est en lecture seule ; sinon, retourne la valeur zéro (`FALSE`).

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Un objet en lecture seule ne peut pas avoir de sa valeur modifiée après sa création.

## <a name="see-also"></a>Voir aussi
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)