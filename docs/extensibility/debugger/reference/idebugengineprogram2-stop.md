---
title: "IDebugEngineProgram2::Stop | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineProgram2::Stop"
helpviewer_keywords: 
  - "IDebugEngineProgram2::Stop"
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugEngineProgram2::Stop
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Arrête tous les threads exécuter dans ce programme.  
  
## Syntaxe  
  
```cpp#  
HRESULT Stop(   
   void   
);  
```  
  
```c#  
int Stop();  
```  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode est appelée lorsque ce programme est débogué dans un environnement de multiprogrammation.  Lorsqu'un événement arrêtant d'un autre programme est accepté, cette méthode est appelée sur ce programme.  L'implémentation de cette méthode doit être asynchrone ; autrement dit, tous les threads doivent être tenu d'être arrêtés avant que cette méthode retourne.  L'implémentation de cette méthode peut être aussi simple que l'appel de la méthode d' [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) sur ce programme.  
  
 aucun événement de débogage n'est envoyé en réponse à cette méthode.  
  
## Voir aussi  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)