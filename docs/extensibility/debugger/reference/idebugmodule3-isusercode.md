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
ms.openlocfilehash: 39bbef1e8b831473b196d0609459b80a05e5fc2c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56718493"
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

#### <a name="parameters"></a>Paramètres
 `pfUser`

 [out] Différent de zéro (`TRUE`) si le module représente le code utilisateur, zéro (`FALSE`) si elle n’est pas le cas.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne le code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)