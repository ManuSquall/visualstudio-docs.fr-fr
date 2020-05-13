---
title: IDebugFunctionObject2::Evaluate Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d87d7d3531d198a1478b4aaa55b354c3ac101302
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728444"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
Appelle la fonction et renvoie la valeur résultante comme objet.

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
[dans] Une gamme d’objets [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) qui représente les paramètres d’entrée. Chacun de ces paramètres a été créé en utilisant l’une des méthodes Create dans cette interface.

`dwParams`\
[dans] Le nombre de paramètres `ppParams` dans le tableau.

`dwEvalFlags`\
[dans] Une combinaison de drapeaux du recensement [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) qui précisent comment l’évaluation doit être effectuée.

`dwTimeout`\
[dans] Spécifie le temps maximum, en millisecondes, d’attendre avant de revenir de cette méthode. Utilisez **INFINITE** pour attendre indéfiniment.

`ppResult`\
[out] Retourne un **IDebugObject** qui représente la valeur de la fonction en tant qu’objet.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
