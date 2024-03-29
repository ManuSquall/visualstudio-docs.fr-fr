---
description: Crée un objet qui utilise un constructeur donné des paramètres d’indicateur d’évaluation et une valeur de délai d’attente.
title: 'IDebugFunctionObject2 :: CreateObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b75cd2fae72d0ce8901445c3271a955100391d75
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063563"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Crée un objet qui utilise un constructeur donné des paramètres d’indicateur d’évaluation et une valeur de délai d’attente.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateObject (
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject (
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   out IDebugObject**   ppObject
);
```

## <a name="parameters"></a>Paramètres
`pConstructor`\
dans Objet [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) qui représente le constructeur de l’objet à créer.

`dwArgs`\
dans Nombre de paramètres dans le `pArg` tableau. Représente le nombre de paramètres passés au constructeur.

`pArgs`\
dans Tableau d’objets [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) qui représente les paramètres passés au constructeur.

`dwEvalFlags`\
dans Combinaison d’indicateurs de l’énumération [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) qui spécifie le mode d’exécution de l’évaluation.

`dwTimeout`\
dans Durée d’attente maximale, en millisecondes, avant le retour de cette méthode. Utilisez **infinite** pour attendre indéfiniment.

`ppObject`\
à Retourne un **IDebugObject** représentant l’objet nouvellement créé.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Appelez cette méthode pour créer un objet qui représente une instance d’une classe ou un autre type complexe qui requiert un constructeur, c’est-à-dire un paramètre.

## <a name="see-also"></a>Voir aussi
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
