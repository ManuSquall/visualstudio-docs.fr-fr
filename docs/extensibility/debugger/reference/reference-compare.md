---
title: "REFERENCE_COMPARE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "REFERENCE_COMPARE"
helpviewer_keywords: 
  - "Énumération de REFERENCE_COMPARE"
ms.assetid: e31cdc78-f621-498b-9ca4-aefa790b9f6f
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# REFERENCE_COMPARE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie le type de comparaison des références.  
  
## Syntaxe  
  
```cpp#  
enum enum_REFERENCE_COMPARE {   
   REF_COMPARE_EQUAL        = 0x0001,  
   REF_COMPARE_LESS_THAN    = 0x0002,  
   REF_COMPARE_GREATER_THAN = 0x0003  
};  
typedef DWORD REFERENCE_COMPARE;  
```  
  
```c#  
public enum enum_REFERENCE_COMPARE {   
   REF_COMPARE_EQUAL        = 0x0001,  
   REF_COMPARE_LESS_THAN    = 0x0002,  
   REF_COMPARE_GREATER_THAN = 0x0003  
};  
```  
  
## Membres  
 REF\_COMPARE\_EQUAL  
 spécifie égal\-à la comparaison.  
  
 REF\_COMPARE\_LESS\_THAN  
 Spécifie un infériorité la comparaison.  
  
 REF\_COMPARE\_GREATER\_THAN  
 Spécifie un caractère supérieur à la comparaison.  
  
## Notes  
 passé comme argument à la méthode d' [Comparer](../../../extensibility/debugger/reference/idebugreference2-compare.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Comparer](../../../extensibility/debugger/reference/idebugreference2-compare.md)