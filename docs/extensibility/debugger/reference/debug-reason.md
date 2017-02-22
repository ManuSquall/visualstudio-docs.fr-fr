---
title: "DEBUG_REASON | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUG_REASON"
helpviewer_keywords: 
  - "Énumération de DEBUG_REASON"
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# DEBUG_REASON
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie la raison pour laquelle le processus a été lancé pour le débogage.  
  
## Syntaxe  
  
```cpp#  
enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
typedef DWORD DEBUG_REASON;  
```  
  
```c#  
public enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
```  
  
#### Paramètres  
 DEBUG\_REASON\_ERROR  
 Une erreur non spécifique produite \(cela est utilisé comme état par défaut lorsqu'aucune des autres raisons ne rentre\).  
  
 DEBUG\_REASON\_USER\_LAUNCHED  
 le processus a été lancé à la requête du client.  
  
 DEBUG\_REASON\_USER\_ATTACHED  
 Le processus de déjà\-fonctionnement a été attaché par l'utilisateur.  
  
 DEBUG\_REASON\_AUTO\_ATTACHED  
 Le processus a été automatiquement joint la valeur lorsqu'il a été lancé.  
  
 DEBUG\_REASON\_CAUSALITY  
 Le processus a été lancé en raison d'un \(JIT\) événement de débogage juste\-à\-temps.  
  
## Notes  
 Retourné par la méthode d' [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)