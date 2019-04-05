---
title: PROVIDER_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROVIDER_FIELDS
helpviewer_keywords:
- PROVIDER_FIELDS enumeration
ms.assetid: 39631545-2b0e-45b4-978b-d63656484b02
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ba0f7cb33ef0bf7fde63d53997d014536e46a85b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948880"
---
# <a name="providerfields"></a>PROVIDER_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Spécifie les propriétés associées à un fournisseur de programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum enum_PROVIDER_FIELDS {  
   PFIELD_PROGRAM_NODES       = 0x01,  
   PFIELD_IS_DEBUGGER_PRESENT = 0x02  
};  
typedef DWORD PROVIDER_FIELDS;  
```  
  
```csharp  
public enum enum_PROVIDER_FIELDS {  
   PFIELD_PROGRAM_NODES       = 0x01,  
   PFIELD_IS_DEBUGGER_PRESENT = 0x02  
};  
```  
  
## <a name="members"></a>Membres  
 PFIELD_PROGRAM_NODES  
 Le `ProgramNodes` champ est valide.  
  
 PFIELD_IS_DEBUGGER_PRESENT  
 Le `fIsDebuggerPresent` champ est valide.  
  
## <a name="remarks"></a>Notes  
 Ces valeurs sont retournées dans le `Fields` membre de la [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) structure pour indiquer les champs de la structure ont été explicitement renseignés.  
  
 Ces valeurs peuvent être combinées avec un opérateur de bits `OR`.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
