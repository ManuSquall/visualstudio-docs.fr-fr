---
title: "IDebugExceptionEvent2::CanPassToDebuggee | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExceptionEvent2::CanPassToDebuggee"
helpviewer_keywords: 
  - "IDebugExceptionEvent2::CanPassToDebuggee"
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugExceptionEvent2::CanPassToDebuggee
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Détermine si le moteur de \(DE\) débogage prennent en charge l'option de passer cette exception au programme en cours de débogage lorsque l'exécution se poursuit.  
  
## Syntaxe  
  
```cpp#  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```c#  
int CanPassToDebuggee();  
```  
  
## Valeur de retour  
 Retourne `S_OK` \(exception peut être passée au programme\) ou `S_FALSE` \(l'exception ne peut pas être transmise sur\).  
  
## Notes  
 Le De doit avoir une action par défaut pour passer au programme débogué.  L'IDE peut recevoir l'événement d' [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) et appeler la méthode d' [Continuer](../../../extensibility/debugger/reference/idebugprocess3-continue.md) sans appeler la méthode d' `CanPassToDebuggee` .  Par conséquent, le De doit avoir un cas par défaut pour passer l'exception sur ou pas.  
  
## Voir aussi  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Continuer](../../../extensibility/debugger/reference/idebugprocess3-continue.md)