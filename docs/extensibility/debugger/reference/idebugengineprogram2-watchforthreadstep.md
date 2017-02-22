---
title: "IDebugEngineProgram2::WatchForThreadStep | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineProgram2::WatchForThreadStep"
helpviewer_keywords: 
  - "IDebugEngineProgram2::WatchForThreadStep"
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugEngineProgram2::WatchForThreadStep
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

La recherche de l'exécution \(ou stop recherche de l'exécution\) se produire sur le thread donné.  
  
## Syntaxe  
  
```cpp#  
HRESULT WatchForThreadStep(   
   IDebugProgram2* pOriginatingProgram,  
   DWORD           dwTid,  
   BOOL            fWatch,  
   DWORD           dwFrame  
);  
```  
  
```c#  
int WatchForThreadStep(   
   IDebugProgram2 pOriginatingProgram,  
   uint           dwTid,  
   int            fWatch,  
   uint           dwFrame  
);  
```  
  
#### Paramètres  
 `pOriginatingProgram`  
 \[in\]  Un objet d' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) représentant le programme en cours \- pas.  
  
 `dwTid`  
 \[in\]  Spécifie l'ID du thread pour le consulter.  
  
 `fWatch`  
 \[in\]  Les méthodes non nuls \(d'`TRUE`\) commencent surveiller l'exécution sur un thread identifié par `dwTid`; sinon, ce qui signifie que zéro \(d'`FALSE`\) cessent de les surveiller l'exécution sur `dwTid`.  
  
 `dwFrame`  
 \[in\]  spécifie un index de frame qui contrôle le type d'étape.  Lorsqu'il est valeur est 0 \(zéro\), le type d'étape est « étape dans » et le programme doit arrêter toutes les fois que le thread identifié par `dwTid` exécute.  Lorsque `dwFrame` est différente de zéro, le type d'étape est « étape sur » et le programme doit arrêter uniquement si le thread identifié par `dwTid` est en cours de exécution dans un frame dont l'index est égal ou supérieur sur la pile qu' `dwFrame`.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Lorsque que le gestionnaire de débogage \(SDM\) de session un programme, identifié par le paramètre d' `pOriginatingProgram` , il signale tous les autres programmes attachés en appelant la méthode.  
  
 Cette méthode ne s'applique qu'à la progression de même\-thread.  
  
## Voir aussi  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)