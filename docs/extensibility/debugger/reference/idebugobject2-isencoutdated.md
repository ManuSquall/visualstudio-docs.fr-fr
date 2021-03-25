---
description: Cette méthode détermine si l’État Modifier & continuer de cet objet ou du conteneur parent est obsolète.
title: 'IDebugObject2 :: IsEncOutdated | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e9b78eb0295d039d4f5d8ca3169cb77d04321aaf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053735"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
Cette méthode détermine si l’État Modifier & continuer de cet objet ou du conteneur parent est obsolète. Un évaluateur d’expression personnalisé n’implémente pas cette méthode et retourne toujours `E_NOTIMPL` .

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsEncOutdated(
   BOOL* pfEncOutdated
);
```

```csharp
int IsEncOutdated(
   out int pfEncOutdated
);
```

## <a name="parameters"></a>Paramètres
`pfEncOutdated`\
à Différent de zéro ( `TRUE` ) si l’État modifier & continuer est obsolète, zéro ( `FALSE` ) si ce n’est pas le cas.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

> [!NOTE]
> Un évaluateur d’expression personnalisé doit toujours retourner `E_NOTIMPL` .

## <a name="see-also"></a>Voir aussi
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
