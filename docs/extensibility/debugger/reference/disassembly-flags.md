---
title: "DISASSEMBLY_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DISASSEMBLY_FLAGS"
helpviewer_keywords: 
  - "Énumération de DISASSEMBLY_FLAGS"
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# DISASSEMBLY_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie des indicateurs pour le code machine.  
  
## Syntaxe  
  
```cpp#  
enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
typedef DWORD DISASSEMBLY_FLAGS;  
```  
  
```c#  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## Membres  
 DF\_DOCUMENTCHANGE  
 Indique que cette instruction est dans un document différent du précédent.  
  
 DF\_DISABLED  
 indique que cette instruction ne sera pas exécutée.  
  
 DF\_INSTRUCTION\_ACTIVE  
 Indique que cette instruction est une de l'instruction suivante à exécuter \(il peut exister plusieurs\).  
  
 DF\_DATA  
 Indique que cette instruction est vraiment données \(pas le code\).  
  
 DF\_HASSOURCE  
 Indique que cette instruction est la source.  Certaines instructions, telle que le profilage ou le code de garbage collection, n'a aucune source correspondante.  
  
 DF\_DOCUMENT\_CHECKSUM  
 Indique que le champ d' `bstrDocumentUrl` contient des données de checksum après l'URL de document.  Consultez la section Notes de la structure des [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) pour la gestion des données de checksum est enregistrée.  
  
## Notes  
 Utilisé comme membre d' `dwFlags` de la structure de [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) .  
  
 Ces indicateurs peuvent être combinées avec `OR`de bits.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)