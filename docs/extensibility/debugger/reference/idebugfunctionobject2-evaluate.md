---
title: IDebugFunctionObject2::Evaluate | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9cd9aafd9157f6d14bb7d37f4ba0301485a35991
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66200686"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
Appelle la fonction et retourne la valeur obtenue en tant qu’objet.

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
[in] Un tableau de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objets qui représente les paramètres d’entrée. Chacun de ces paramètres a été créé en utilisant l’une des méthodes de créer dans cette interface.

`dwParams`\
[in] Le nombre de paramètres dans le `ppParams` tableau.

`dwEvalFlags`\
[in] Une combinaison d’indicateurs de la [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) énumération qui spécifient la façon dont l’évaluation doit être effectuée.

`dwTimeout`\
[in] Spécifie la durée maximale, en millisecondes, à attendre avant de retourner à partir de cette méthode. Utilisez **infinie** pour attendre indéfiniment.

`ppResult`\
[out] Retourne un **IDebugObject** qui représente la valeur de la fonction en tant qu’objet.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)