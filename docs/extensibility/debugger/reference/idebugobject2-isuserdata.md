---
title: IDebugObject2::IsUserData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04c47390f15ff59658ba25f5c8f93918a15f47d6
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56700092"
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

#### <a name="parameters"></a>Paramètres
 `pfUser`

 [out] Retourne la valeur différente de zéro (`TRUE`) si l’objet représente les données utilisateur ; zéro (`FALSE`) si elle n’est pas le cas.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Données utilisateur sont un objet qui fait partie d’un module désigné comme JustMyCode (une option configurable par l’utilisateur qui marque un module en tant que code utilisateur et sont donc visibles dans une trace de pile).

## <a name="see-also"></a>Voir aussi
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)