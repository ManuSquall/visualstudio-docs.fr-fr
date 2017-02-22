---
title: "IDebugProgram2::CauseBreak | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::CauseBreak"
helpviewer_keywords: 
  - "IDebugProgram2::CauseBreak"
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProgram2::CauseBreak
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Demande que le programme arrêtent l'exécution la prochaine fois qu'une de ses thread tente d'exécuter.  
  
## Syntaxe  
  
```cpp#  
HRESULT CauseBreak(   
   void   
);  
```  
  
```c#  
int CauseBreak();  
```  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Un événement d' [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) est envoyé lorsque les tentatives suivantes de programme d'exécuter le code après cette méthode est appelée.  
  
 Cette méthode est asynchrone car la méthode retourne immédiatement sans attendre nécessairement le programme pour arrêter.  
  
## Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)