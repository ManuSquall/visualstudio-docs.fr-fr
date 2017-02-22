---
title: "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread"
helpviewer_keywords: 
  - "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread"
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Permet \(ou rejette\) à l'évaluation de l'expression pour se produire sur le thread donné, même si le programme a arrêté.  
  
## Syntaxe  
  
```cpp#  
HRESULT WatchForExpressionEvaluationOnThread(   
   IDebugProgram2*       pOriginatingProgram,  
   DWORD                 dwTid,  
   DWORD                 dwEvalFlags,  
   IDebugEventCallback2* pExprCallback,  
   BOOL                  fWatch  
);  
```  
  
```c#  
int WatchForExpressionEvaluationOnThread(   
   IDebugProgram2       pOriginatingProgram,  
   uint                  dwTid,  
   uint                  dwEvalFlags,  
   IDebugEventCallback2 pExprCallback,  
   int                   fWatch  
);  
```  
  
#### Paramètres  
 `pOriginatingProgram`  
 \[in\]  un objet d' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) représentant le programme qui évalue une expression.  
  
 `dwTid`  
 \[in\]  Spécifie l'ID du thread.  
  
 `dwEvalFlags`  
 \[in\]  Une combinaison des indicateurs d'énumération d' [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) qui spécifient comment l'évaluation doit être exécutée.  
  
 `pExprCallback`  
 \[in\]  Un objet d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) à utiliser pour envoyer les événements de débogage qui se produisent pendant l'évaluation d'une expression.  
  
 `fWatch`  
 \[in\]  Si la valeur est différente de zéro \(`TRUE`\), permet l'évaluation d'une expression sur le thread identifié par `dwTid`; sinon, le zéro \(`FALSE`\) interdit l'évaluation d'une expression sur ce thread.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Lorsque le gestionnaire de débogage de session \(SDM\) demande un programme, identifié par le paramètre d' `pOriginatingProgram` , évaluer une expression, elle signale tous les autres programmes attachés en appelant la méthode.  
  
 L'évaluation d'une expression dans un programme peut provoquer l'exécution du code dans les autres, en raison de l'évaluation de fonction ou de l'évaluation de toutes les propriétés d' `IDispatch` .  De ce fait, cette méthode permet à l'évaluation de l'expression pour exécuter et effectuer bien que le thread ait être arrêté dans ce programme.  
  
## Voir aussi  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)