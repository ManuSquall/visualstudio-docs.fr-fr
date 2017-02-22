---
title: "REFERENCE_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "REFERENCE_TYPE"
helpviewer_keywords: 
  - "Énumération de REFERENCE_TYPE"
ms.assetid: b1ffba10-eb9d-48ba-bf48-6d8b71d6f270
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# REFERENCE_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

spécifie le type référence.  
  
## Syntaxe  
  
```cpp#  
enum enum_REFERENCE_TYPE {   
   REF_TYPE_WEAK   = 0x0001,  
   REF_TYPE_STRONG = 0x0002  
};  
typedef DWORD REFERENCE_TYPE;  
```  
  
```c#  
public enum enum_REFERENCE_TYPE {   
   REF_TYPE_WEAK   = 0x0001,  
   REF_TYPE_STRONG = 0x0002  
};  
```  
  
## Membres  
 REF\_TYPE\_WEAK  
 spécifie une référence faible.  Ne peut pas être combiné avec `REF_TYPE_STRONG`.  
  
 REF\_TYPE\_STRONG  
 spécifie une référence forte.  Ne peut pas être combiné avec `REF_TYPE_WEAK`.  
  
## Notes  
 Utilisé comme membre d' `dwRefType` de la structure de [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) .  
  
 passé comme paramètre à la méthode d' [SetReferenceType](../Topic/IDebugReference2::SetReferenceType.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [SetReferenceType](../Topic/IDebugReference2::SetReferenceType.md)