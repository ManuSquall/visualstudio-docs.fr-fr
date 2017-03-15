---
title: "IDebugEngine2::CauseBreak | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::CauseBreak"
helpviewer_keywords: 
  - "IDebugEngine2::CauseBreak"
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugEngine2::CauseBreak
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Demandes que tous les programmes débogué par ce moteur de débogage \(DE\) pour arrêter l'exécution la prochaine fois qu'une de leurs thread essaie d'exécuter.  
  
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
 cette méthode est asynchrone : un événement d' [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) est envoyé lorsque les tentatives suivantes de programme d'exécuter après cette méthode est appelée.  
  
## Voir aussi  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)