---
title: IDebugFunctionObject2::CreateObject ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6de1a30a032919a90fbb3d760837d5eeca00feaf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728480"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Crée un objet qui utilise un constructeur donné paramètres de drapeau d’évaluation et une valeur de délai d’attente.

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
[dans] Un objet [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) qui représente le constructeur de l’objet à créer.

`dwArgs`\
[dans] Le nombre de paramètres `pArg` dans le tableau. Représente le nombre de paramètres transmis au constructeur.

`pArgs`\
[dans] Une gamme d’objets [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) qui représente les paramètres transmis au constructeur.

`dwEvalFlags`\
[dans] Une combinaison de drapeaux du recensement [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) qui précisent comment l’évaluation doit être effectuée.

`dwTimeout`\
[dans] Temps maximum, en millisecondes, d’attendre avant de revenir de cette méthode. Utilisez **INFINITE** pour attendre indéfiniment.

`ppObject`\
[out] Retourne un **IDebugObject** représentant l’objet nouvellement créé.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Appelez cette méthode pour créer un objet qui représente une instance d’une classe, ou tout autre type complexe qui nécessite un constructeur, qui est un paramètre.

## <a name="see-also"></a>Voir aussi
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
