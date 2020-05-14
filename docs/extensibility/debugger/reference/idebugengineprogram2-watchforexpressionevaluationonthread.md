---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e988e1d64af38a55f5d946f704e1edb4df29b1d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730366"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Permet à l’évaluation d’expression (ou de refuser) de se produire sur le thread donné, même si le programme a cessé.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WatchForExpressionEvaluationOnThread( 
   IDebugProgram2*       pOriginatingProgram,
   DWORD                 dwTid,
   DWORD                 dwEvalFlags,
   IDebugEventCallback2* pExprCallback,
   BOOL                  fWatch
);
```

```csharp
int WatchForExpressionEvaluationOnThread( 
   IDebugProgram2       pOriginatingProgram,
   uint                  dwTid,
   uint                  dwEvalFlags,
   IDebugEventCallback2 pExprCallback,
   int                   fWatch
);
```

## <a name="parameters"></a>Paramètres
`pOriginatingProgram`\
[dans] Un objet [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) représentant le programme qui évalue une expression.

`dwTid`\
[dans] Spécifie l’identifiant du fil.

`dwEvalFlags`\
[dans] Une combinaison de drapeaux du recensement [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) qui précisent comment l’évaluation doit être effectuée.

`pExprCallback`\
[dans] Un objet [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) à utiliser pour envoyer des événements de débog qui se produisent lors de l’évaluation de l’expression.

`fWatch`\
[dans] Si non-zéro`TRUE`( ), permet l’évaluation de l’expression sur le fil identifié par `dwTid`; autrement, zéro`FALSE`( ) interdit l’évaluation d’expression sur ce fil.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Lorsque le gestionnaire de déboiffés de session (SDM) demande à un programme, identifié par le `pOriginatingProgram` paramètre, d’évaluer une expression, il informe tous les autres programmes ci-joints en appelant cette méthode.

 L’évaluation de l’expression dans un programme peut faire fonctionner `IDispatch` le code dans un autre, en raison de l’évaluation ou de l’évaluation des fonctions de toutes les propriétés. Pour cette raison, cette méthode permet à l’évaluation d’expression de s’exécuter et de terminer même si le fil peut être arrêté dans ce programme.

## <a name="see-also"></a>Voir aussi
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
