---
description: Retourne le jeu d’éléments suivant de l’énumération modules.
title: 'IEnumDebugModules2 :: suivant | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2::Next
helpviewer_keywords:
- IEnumDebugModules2::Next
ms.assetid: 46b7ccad-b07b-4ec0-b3ce-13981ffab7e8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a7c1d627579faea8bb4871feb310db79d6e5eea0
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102226395"
---
# <a name="ienumdebugmodules2next"></a>IEnumDebugModules2::Next
Retourne l'ensemble d'éléments suivants de l'énumération.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Next(
   ULONG           celt,
   IDebugModule2** rgelt,
   ULONG*          pceltFetched
);
```

```csharp
int Next(
   uint            celt,
   IDebugModule2[] rgelt,
   ref uint        pceltFetched
);
```

## <a name="parameters"></a>Paramètres
`celt`\
[in] Nombre d'éléments à récupérer. Spécifie également la taille maximale du `rgelt` tableau.

`rgelt`\
[in, out] Tableau d’éléments [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) à remplir.

`pceltFetched`\
à Retourne le nombre d’éléments réellement retournés dans `rgelt` .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si un nombre inférieur au nombre d’éléments demandés peut être retourné ; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
