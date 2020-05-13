---
title: IDebugObject2::IsUserData ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ce4a7035ac3786f0cc1644e2ebbb0c142167e2b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726090"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
Détermine si l’objet représente les données utilisateur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsUserData(
   BOOL* pfUser
);
```

```csharp
int IsUserData(
   out int pfUser
);
```

## <a name="parameters"></a>Paramètres
`pfUser`\
[out] Retourne nonzero`TRUE`( ) si l’objet représente les données de l’utilisateur; zéro`FALSE`( ) si ce n’est pas le cas.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK; autrement, renvoie un code d’erreur.

## <a name="remarks"></a>Notes
 Les données utilisateur sont tout objet qui fait partie d’un module désigné comme JustMyCode (une option configurable utilisateur qui marque un module comme code utilisateur et donc visible dans une trace de pile).

## <a name="see-also"></a>Voir aussi
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
