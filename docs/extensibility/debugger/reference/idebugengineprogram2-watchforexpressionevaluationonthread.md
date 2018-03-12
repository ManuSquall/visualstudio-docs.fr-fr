---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e40af42d1dd639b80ffac3e2f3cf9c4501782b45
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Autorise (ou interdit) évaluation d’expression en se produisent sur le thread donné, même si le programme s’est arrêté.  
  
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
 [in] Une combinaison d’indicateurs à partir de la [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) énumération qui spécifie la manière dont l’évaluation doit être effectuée.  
  
 `pExprCallback`  
 [in] Un [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objet à être utilisé pour envoyer des événements de débogage qui se produisent pendant l’évaluation d’expression.  
  
 `fWatch`  
 [in] Si non nul (`TRUE`), permet l’évaluation d’une expression sur le thread identifié par `dwTid`; sinon, zéro (`FALSE`) n’autorise pas d’évaluation d’une expression sur ce thread.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Lorsque le Gestionnaire de session de débogage (SDM) demande un programme, identifié par le `pOriginatingProgram` paramètre, d’évaluer une expression, il avertit tous les autres programmes attachés en appelant cette méthode.  
  
 Évaluation de l’expression dans un programme peut entraîner le code d’exécution dans un autre, en raison d’une version d’évaluation de fonction ou de n’importe quel `IDispatch` propriétés. Pour cette raison, cette méthode permet d’évaluation d’expression exécuter et terminer même si le thread peut être arrêté à ce programme.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)