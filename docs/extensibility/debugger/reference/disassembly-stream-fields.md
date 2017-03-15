---
title: "DISASSEMBLY_STREAM_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DISASSEMBLY_STREAM_FIELDS"
helpviewer_keywords: 
  - "Énumération de DISASSEMBLY_STREAM_FIELDS"
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# DISASSEMBLY_STREAM_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie les informations à récupérer concernant un champ de code machine.  
  
## Syntaxe  
  
```cpp#  
enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
typedef DWORD DISASSEMBLY_STREAM_FIELDS;  
```  
  
```c#  
public enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
```  
  
## Membres  
 DSF\_ADDRESS  
 Initialisez\/utilisez le champ d' `bstrAddress` .  
  
 DSF\_ADDRESSOFFSET  
 Initialisez\/utilisez le champ d' `bstrAddressOffset` .  
  
 DSF\_CODEBYTES  
 Initialisez\/utilisez le champ d' `bstrCodeBytes` .  
  
 DSF\_OPCODE  
 Initialisez\/utilisez le champ d' `bstrOpCode` .  
  
 DSF\_OPERANDS  
 Initialisez\/utilisez le champ d' `bstrOperands` .  
  
 DSF\_SYMBOL  
 Initialisez\/utilisez le champ d' `bstrSymbol` .  
  
 DSF\_CODELOCATIONID  
 Initialisez\/utilisez le champ d' `uCodeLocationId` .  
  
 DSF\_POSITION  
 Initialisez\/utilisez les champs d' `posBeg` et d' `posEnd` .  
  
 DSF\_DOCUMENTURL  
 Initialisez\/utilisez le champ d' `bstrDocumentUrl` .  
  
 DSF\_BYTEOFFSET  
 Initialisez\/utilisez le champ d' `dwByteOffset` .  
  
 DSF\_FLAGS  
 Initialisez\/utilisez le champ d' `dwFlags` \([DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)\).  
  
 DSF\_OPERANDS\_SYMBOLS  
 Incluez les noms de symboles dans le domaine de `bstrOperands` .  
  
 DSF\_ALL  
 Spécifie les champs pour le flux du code machine.  
  
## Notes  
 Passé comme un paramètre à la méthode de [Lecture](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) indiquer que des champs de la structure de [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) doivent être initialisé.  
  
 Utilisé pour le membre d' `dwFields` de la structure d' `DisassemblyData` pour indiquer les champs sont utilisés et valide lorsque la structure est retournée.  
  
 Ces valeurs peuvent être combinées avec `OR`de bits.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Lecture](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)