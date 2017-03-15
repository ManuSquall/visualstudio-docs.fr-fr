---
title: "PROVIDER_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROVIDER_FIELDS"
helpviewer_keywords: 
  - "Énumération de PROVIDER_FIELDS"
ms.assetid: 39631545-2b0e-45b4-978b-d63656484b02
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# PROVIDER_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie les propriétés associées à un fournisseur de programme.  
  
## Syntaxe  
  
```cpp#  
enum enum_PROVIDER_FIELDS {  
   PFIELD_PROGRAM_NODES       = 0x01,  
   PFIELD_IS_DEBUGGER_PRESENT = 0x02  
};  
typedef DWORD PROVIDER_FIELDS;  
```  
  
```c#  
public enum enum_PROVIDER_FIELDS {  
   PFIELD_PROGRAM_NODES       = 0x01,  
   PFIELD_IS_DEBUGGER_PRESENT = 0x02  
};  
```  
  
## Membres  
 PFIELD\_PROGRAM\_NODES  
 le champ d' `ProgramNodes` est valide.  
  
 PFIELD\_IS\_DEBUGGER\_PRESENT  
 le champ d' `fIsDebuggerPresent` est valide.  
  
## Notes  
 Ces valeurs sont retournées dans le membre d' `Fields` de la structure de [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md) pour indiquer que les champs de la structure ont été explicitement terminée.  
  
 Ces valeurs peuvent être combinées avec `OR`de bits.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md)