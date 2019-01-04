---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1e6d6379d708caeb746a7b609083131ec1bbcce2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53879093"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Autorise (ou interdit) d’évaluation d’expression se produise sur le thread donné, même si le programme s’est arrêté.  
  
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
  
#### <a name="parameters"></a>Paramètres  
 `pOriginatingProgram`  
 [in] Un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objet représentant le programme qui évalue une expression.  
  
 `dwTid`  
 [in] Spécifie l’identificateur du thread.  
  
 `dwEvalFlags`  
 [in] Une combinaison d’indicateurs de la [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) énumération qui spécifient la façon dont l’évaluation doit être effectuée.  
  
 `pExprCallback`  
 [in] Un [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objet à utiliser pour envoyer des événements de débogage qui se produisent pendant l’évaluation d’expression.  
  
 `fWatch`  
 [in] Si non nulle (`TRUE`), permet l’évaluation de l’expression sur le thread identifié par `dwTid`; sinon, zéro (`FALSE`) n’autorise pas d’évaluation de l’expression sur ce thread.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Lorsque le Gestionnaire de session de débogage (SDM) demande un programme, identifié par le `pOriginatingProgram` paramètre, pour évaluer une expression, il avertit tous les autres programmes attachés en appelant cette méthode.  
  
 Évaluation des expressions dans un programme peut entraîner le code à exécuter dans un autre, en raison d’une version d’évaluation de fonction ou de n’importe quel `IDispatch` propriétés. Pour cette raison, cette méthode permet d’évaluation d’expression exécuter et terminer même si le thread peut être arrêté dans ce programme.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)