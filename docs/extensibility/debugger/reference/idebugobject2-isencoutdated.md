---
title: IDebugObject2::IsEncOutdated | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9b2d26b49f3d2597e12e11a323a9281bd5c676fa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317414"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
Cette méthode détermine si l’état de modifier & Continuer de cet objet ou du conteneur parent est obsolète. Un évaluateur d’expression personnalisée n’implémente pas cette méthode et renvoie toujours `E_NOTIMPL`.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsEncOutdated(
   BOOL* pfEncOutdated
);
```

```csharp
int IsEncOutdated(
   out int pfEncOutdated
);
```

## <a name="parameters"></a>Paramètres
`pfEncOutdated`\
[out] Différent de zéro (`TRUE`) si l’état de modifier & Continuer est obsolète, zéro (`FALSE`) si elle n’est pas.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

> [!NOTE]
> Un évaluateur d’expression personnalisé doit toujours retourner `E_NOTIMPL`.

## <a name="see-also"></a>Voir aussi
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)