---
title: "DOCCONTEXT_COMPARE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DOCCONTEXT_COMPARE"
helpviewer_keywords: 
  - "Énumération de DOCCONTEXT_COMPARE"
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# DOCCONTEXT_COMPARE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

spécifie les critères pour comparer deux contextes de document.  
  
## Syntaxe  
  
```cpp#  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
typedef DWORD DOCCONTEXT_COMPARE;  
```  
  
```c#  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
```  
  
## Membres  
 DOCCONTEXT\_EQUAL  
 recherchez le premier contexte de document dans la liste qui est égale au contexte de document cible.  
  
 DOCCONTEXT\_LESS\_THAN  
 Recherchez le premier contexte de document dans la liste inférieure au contexte de document cible.  
  
 DOCCONTEXT\_GREATER\_THAN  
 Recherchez le premier contexte de document dans la liste supérieure au contexte de document cible.  
  
 DOCCONTEXT\_SAME\_DOCUMENT  
 Recherchez le premier contexte de document dans la liste qui se trouve dans le même document que le contexte de document cible.  
  
## Notes  
 passé comme argument à la méthode d' [Comparer](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) .  
  
 Ces valeurs sont utilisées pour spécifier des critères de comparaison pour rechercher le premier contexte de document dans une liste.  Un contexte de document est fourni une liste des contextes de document pour la comparer à via la méthode d' `IDebugDocumentContext2::Compare` .  Le premier contexte de document dans la liste pour laquelle l'opérateur de comparaison est `true` est ensuite retournée.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Comparer](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)