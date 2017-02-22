---
title: "CANSTOP_REASON | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CANSTOP_REASON"
helpviewer_keywords: 
  - "Énumération de CANSTOP_REASON"
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# CANSTOP_REASON
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Utilisé pour déterminer si un programme peut arrêter l'exécution après positionnement d'un point spécifique de l'exécution.  
  
## Syntaxe  
  
```cpp#  
enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
typedef DWORD CANSTOP_REASON;  
```  
  
```c#  
public enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
```  
  
## Membres  
 CANSTOP\_ENTRYPOINT  
 spécifie le point d'entrée du programme donné.  
  
 CANSTOP\_STEPIN  
 Spécifie le pas \- à \- pas dans une fonction.  
  
## Notes  
 Passé comme argument à la méthode d' [GetReason](../Topic/IDebugCanStopEvent2::GetReason.md) confirmer avec le gestionnaire de débogage de session \(SDM\) s'il est correct d'arrêter après positionnement du point d'entrée du programme ou après entrant dans une fonction ou une méthode.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../Topic/IDebugCanStopEvent2::GetReason.md)