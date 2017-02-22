---
title: "IDebugProgram3::ExecuteOnThread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProgram3::ExecuteOnThread"
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugProgram3::ExecuteOnThread
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

exécute le programme de débogueur.  Le thread est retourné pour fournir au débogueur des informations sur lesquels le thread l'utilisateur s'affiche en exécutant le programme.  
  
## Syntaxe  
  
```cpp#  
HRESULT ExecuteOnThread(  
   [in] IDebugThread2* pThread)  
```  
  
```c#  
int ExecuteOnThread(  
   IDebugThread2 pThread  
);  
```  
  
#### Paramètres  
 `pThread`  
 \[in\]  un objet d' [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Il existe trois façons différentes qu'un débogueur peut continuer l'exécution après avoir arrêté :  
  
-   exécutez : Supprimez toute étape précédente, puis jusqu ' à le point d'arrêt suivant et ainsi de suite.  
  
-   étape : Supprimez toute étape ancienne, et exécuté jusqu'à la nouvelle étape est terminée.  
  
-   continuez : Exécutez à nouveau, et laissez toute étape ancienne active.  
  
 Le thread passé à `ExecuteOnThread` est utile lorsque vous décidez qui progressent à l'annulation.  Si vous ne connaissez pas le thread, exécution exécuter des annulations toutes les étapes.  Avec la connaissance du thread, vous devez annuler l'étape sur le thread actif.  
  
## Voir aussi  
 [Exécuter](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)