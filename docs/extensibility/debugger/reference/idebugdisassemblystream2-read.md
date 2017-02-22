---
title: "IDebugDisassemblyStream2::Read | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2::Read"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::Read"
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDisassemblyStream2::Read
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

L'instruction lectures à partir de la position actuelle dans le code machine des flux.  
  
## Syntaxe  
  
```cpp#  
HRESULT Read(   
   DWORD                     dwInstructions,  
   DISASSEMBLY_STREAM_FIELDS dwFields,  
   DWORD*                    pdwInstructionsRead,  
   DisassemblyData*          prgDisassembly  
);  
```  
  
```c#  
int Read(   
   uint                           dwInstructions,  
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,  
   out uint                       pdwInstructionsRead,  
   DisassemblyData[]              prgDisassembly  
);  
```  
  
#### Paramètres  
 `dwInstructions`  
 \[in\]  Le nombre d'instructions pour désassembler.  Cette valeur est également la longueur maximale du tableau d' `prgDisassembly` .  
  
 `dwFields`  
 \[in\]  Une combinaison des indicateurs d'énumération de [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) qui indiquent quels champs d' `prgDisassembly` doivent être effectués.  
  
 `pdwInstructionsRead`  
 \[out\]  Retourne le nombre d'instructions réellement désassemblée.  
  
 `prgDisassembly`  
 \[out\]  Un tableau de structures de [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) qui est rempli avec code désassemblé, une structure par instruction désassemblée.  La longueur de ce tableau est dicté par le paramètre d' `dwInstructions` .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Le nombre maximal d'instructions qui sont disponibles dans la portée actuelle peut être obtenu en appelant la méthode d' [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) .  
  
 La position actuelle où l'instruction suivante est lue de peut être modifié en appelant la méthode d' [Recherche](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) .  
  
 La balise d' `DSF_OPERANDS_SYMBOLS` peut être ajoutée à la balise d' `DSF_OPERANDS` dans le paramètre d' `dwFields` pour indiquer que les noms de symboles doivent être utilisés en désassemblant l'instruction.  
  
## Voir aussi  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)   
 [Recherche](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)