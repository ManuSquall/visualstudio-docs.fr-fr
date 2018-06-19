---
title: DISASSEMBLY_STREAM_FIELDS | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1a8735992574699ba2b108fc493e9003ca52c9b2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103524"
---
# <a name="disassemblystreamfields"></a>DISASSEMBLY_STREAM_FIELDS
Spécifie les informations à récupérer sur un champ de code machine.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_DISASSEMBLY_STREAM_FIELDS {   
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
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_FIELDS {   
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
  
## <a name="members"></a>Membres  
 DSF_ADDRESS  
 Initialisation/utiliser le `bstrAddress` champ.  
  
 DSF_ADDRESSOFFSET  
 Initialisation/utiliser le `bstrAddressOffset` champ.  
  
 DSF_CODEBYTES  
 Initialisation/utiliser le `bstrCodeBytes` champ.  
  
 DSF_OPCODE  
 Initialisation/utiliser le `bstrOpCode` champ.  
  
 DSF_OPERANDS  
 Initialisation/utiliser le `bstrOperands` champ.  
  
 DSF_SYMBOL  
 Initialisation/utiliser le `bstrSymbol` champ.  
  
 DSF_CODELOCATIONID  
 Initialisation/utiliser le `uCodeLocationId` champ.  
  
 DSF_POSITION  
 Initialisation/utiliser le `posBeg` et `posEnd` champs.  
  
 DSF_DOCUMENTURL  
 Initialisation/utiliser le `bstrDocumentUrl` champ.  
  
 DSF_BYTEOFFSET  
 Initialisation/utiliser le `dwByteOffset` champ.  
  
 DSF_FLAGS  
 Initialisation/utiliser le `dwFlags` ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)) champ.  
  
 DSF_OPERANDS_SYMBOLS  
 Inclure les noms de symboles dans le `bstrOperands` champ.  
  
 DSF_ALL  
 Spécifie tous les champs pour le flux de code machine.  
  
## <a name="remarks"></a>Notes  
 Passé en tant que paramètre à la [en lecture](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) méthode pour indiquer les champs de la [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) structure doivent être initialisées.  
  
 Utilisé pour le `dwFields` membre de la `DisassemblyData` structure pour indiquer quels champs sont utilisés et valide lors de la structure est retournée.  
  
 Ces valeurs peuvent être combinées avec une opération de bits `OR`.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [En lecture](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)