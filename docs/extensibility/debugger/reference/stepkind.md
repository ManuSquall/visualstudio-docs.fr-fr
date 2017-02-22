---
title: "STEPKIND | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "STEPKIND"
helpviewer_keywords: 
  - "Énumération de STEPKIND"
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# STEPKIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

spécifie le type d'étape pour la progression.  
  
## Syntaxe  
  
```cpp#  
enum enum_STEPKIND {   
   STEP_INTO      = 0,  
   STEP_OVER      = 1,  
   STEP_OUT       = 2,  
   STEP_BACKWARDS = 3  
};  
typedef DWORD STEPKIND;  
```  
  
```c#  
public enum enum_STEPKIND {   
   STEP_INTO      = 0,  
   STEP_OVER      = 1,  
   STEP_OUT       = 2,  
   STEP_BACKWARDS = 3  
};  
```  
  
## Membres  
 STEP\_INTO  
 étapes dans une fonction.  
  
 STEP\_OVER  
 Étapes sur une fonction.  
  
 STEP\_OUT  
 Étapes à partir d'une fonction.  
  
 STEP\_BACKWARDS  
 Effectue un pas vers l'arrière dans une fonction.  
  
## Notes  
 passé comme argument à la méthode d' [Étape](../../../extensibility/debugger/reference/idebugprocess3-step.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Étape](../../../extensibility/debugger/reference/idebugprocess3-step.md)