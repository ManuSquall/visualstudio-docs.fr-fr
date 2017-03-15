---
title: "STEPUNIT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "STEPUNIT"
helpviewer_keywords: 
  - "Énumération de STEPUNIT"
ms.assetid: cb8441f2-f744-4e73-acfe-ae8542df9649
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# STEPUNIT
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

spécifie l'unité d'étape pour la progression.  
  
## Syntaxe  
  
```cpp#  
enum enum_STEPUNIT {   
   STEP_STATEMENT   = 0,  
   STEP_LINE        = 1,  
   STEP_INSTRUCTION = 2  
};  
typedef DWORD STEPUNIT;  
```  
  
```c#  
enum enum_STEPUNIT {   
   STEP_STATEMENT   = 0,  
   STEP_LINE        = 1,  
   STEP_INSTRUCTION = 2  
};  
```  
  
## Membres  
 STEP\_STATEMENT  
 étapes par l'instruction.  
  
 STEP\_LINE  
 Étapes par ligne.  
  
 STEP\_INSTRUCTION  
 étapes par l'instruction.  
  
## Notes  
 passé comme argument à la méthode d' [Étape](../../../extensibility/debugger/reference/idebugprocess3-step.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Étape](../../../extensibility/debugger/reference/idebugprocess3-step.md)