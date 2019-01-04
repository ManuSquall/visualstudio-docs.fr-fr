---
title: DISASSEMBLY_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7b0e4f793b0dcfe7a8a35bfeb06a3acd53c969d5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53960988"
---
# <a name="disassemblyflags"></a>DISASSEMBLY_FLAGS
Spécifie les indicateurs pour le code machine.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
```csharp  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## <a name="members"></a>Membres  
 DF_DOCUMENTCHANGE  
 Indique que cette instruction est dans un autre document que le précédent.  
  
 DF_DISABLED  
 Indique que cette instruction ne sera pas exécutée.  
  
 DF_INSTRUCTION_ACTIVE  
 Indique que cette instruction est une des instructions à exécuter suivantes (il peut en avoir plusieurs).  
  
 DF_DATA  
 Indique que cette instruction est réellement données (pas de code).  
  
 DF_HASSOURCE  
 Indique que cette instruction a source. Des instructions, tel que le code de collection de profilage ou garbage, n’ont aucune source correspondante.  
  
 DF_DOCUMENT_CHECKSUM  
 Indique que `bstrDocumentUrl` champ contient des données de la somme de contrôle après l’URL du document. Consultez la section Notes pour la [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) structure pour le stockage des données de la somme de contrôle.  
  
## <a name="remarks"></a>Notes  
 Utilisé en tant que le `dwFlags` membre de la [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) structure.  
  
 Ces indicateurs peuvent être combinées avec un opérateur de bits `OR`.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)