---
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 88ff2a1da1f937fd4011932979bd95057eb40dfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205052"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Décrit ou spécifie les propriétés d’un processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
typedef DWORD PROCESS_INFO_FLAGS;  
```  
  
```csharp  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
```  
  
## <a name="members"></a>Membres  
 PIFLAG_SYSTEM_PROCESS  
 Indique que le processus est un processus système.  
  
 PIFLAG_DEBUGGER_ATTACHED  
 Indique que le processus est en cours de débogage par un débogueur. Il peut s’agir d’un [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] débogueur, ou il peut s’agir d’un autre débogueur, par exemple Windbg.  
  
 PIFLAG_PROCESS_STOPPED  
 Indique que le processus est arrêté. Valide uniquement si `PIFLAG_DEBUGGER_ATTACHED` est également spécifié. Disponible dans [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] et versions ultérieures.  
  
 PIFLAG_PROCESS_RUNNING  
 Indique que le processus est en cours d’exécution. Valide uniquement si `PIFLAG_DEBUGGER_ATTACHED` est également spécifié. Disponible dans [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] et versions ultérieures.  
  
## <a name="remarks"></a>Notes  
 Utilisé pour le `Flags` membre de la structure [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) .  
  
 Ces indicateurs peuvent être combinés avec une opération au niveau du bit `OR` .  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
