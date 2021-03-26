---
description: 'IDebugFunctionObject2 :: Evaluate appelle la fonction et retourne la valeur résultante sous la forme d’un objet.'
title: 'IDebugFunctionObject2 :: Evaluate | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 35b6acb64ffd894b1cff03badcf2cdea831c7260
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063576"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
Appelle la fonction et retourne la valeur résultante sous la forme d’un objet.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Evaluate (
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwEvalFlags,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate (
   IDebugObject     ppParams,
   uint             dwParams,
   uint             dwEvalFlags,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>Paramètres
`ppParams`\
dans Tableau d’objets [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) qui représente les paramètres d’entrée. Chacun de ces paramètres a été créé à l’aide de l’une des méthodes Create dans cette interface.

`dwParams`\
dans Nombre de paramètres dans le `ppParams` tableau.

`dwEvalFlags`\
dans Combinaison d’indicateurs de l’énumération [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) qui spécifie le mode d’exécution de l’évaluation.

`dwTimeout`\
dans Spécifie la durée d’attente maximale, en millisecondes, avant le retour de cette méthode. Utilisez **infinite** pour attendre indéfiniment.

`ppResult`\
à Retourne un **IDebugObject** qui représente la valeur de la fonction sous la forme d’un objet.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
