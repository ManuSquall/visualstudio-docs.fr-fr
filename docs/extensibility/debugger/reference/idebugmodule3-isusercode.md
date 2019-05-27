---
title: IDebugModule3::IsUserCode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 71ac93a0cef0fa06910e314f1983bf399e190f4a
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66203079"
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
Récupère des informations sur indique si le module représente le code utilisateur ou non.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsUserCode(
   BOOL* pfUser
);
```

```csharp
int IsUserCode(
   out int pfUser
);
```

## <a name="parameters"></a>Paramètres
`pfUser`\
[out] Différent de zéro (`TRUE`) si le module représente le code utilisateur, zéro (`FALSE`) si elle n’est pas le cas.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne le code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)