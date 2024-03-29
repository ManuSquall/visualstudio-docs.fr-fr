---
description: Détermine si l’objet représente des données utilisateur.
title: 'IDebugObject2 :: IsUserData | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 485583c0d6ef8ac42b78612e68995462ef900795
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053722"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
Détermine si l’objet représente des données utilisateur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsUserData(
   BOOL* pfUser
);
```

```csharp
int IsUserData(
   out int pfUser
);
```

## <a name="parameters"></a>Paramètres
`pfUser`\
à Retourne une valeur différente de zéro ( `TRUE` ) si l’objet représente des données utilisateur ; zéro ( `FALSE` ) si ce n’est pas le cas.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Les données utilisateur sont des objets qui font partie d’un module désigné comme JustMyCode (option configurable par l’utilisateur qui marque un module en tant que code utilisateur et qui est donc visible dans une trace de la pile).

## <a name="see-also"></a>Voir aussi
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
