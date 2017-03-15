---
title: "IDebugThread2::Resume | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::Resume"
helpviewer_keywords: 
  - "IDebugThread2::Resume"
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugThread2::Resume
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Reprend l'exécution d'un thread.  
  
## Syntaxe  
  
```cpp#  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```c#  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### Paramètres  
 `pdwSuspendCount`  
 \[out\]  Retourne le compteur de suspension après l'opération de réexécuter.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Chaque appel à cette méthode décrémente le compteur de suspension jusqu'à ce qu'il atteigne 0 lorsque, l'exécution se poursuivre réellement.  Ce compteur de suspension s'affiche dans la fenêtre de débogage de **Threads** .  
  
 Pour chaque appel à cette méthode, il doit exister un appel précédent à la méthode de [Interrompre](../Topic/IDebugThread2::Suspend.md) .  le compteur de suspension détermine combien de fois la méthode d' `IDebugThread2::Suspend` a été appelées jusqu'à présent.  
  
## Voir aussi  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Interrompre](../Topic/IDebugThread2::Suspend.md)