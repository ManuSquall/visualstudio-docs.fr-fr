---
title: PROCESS_INFO_FLAGS | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROCESS_INFO_FLAGS
helpviewer_keywords: PROCESS_INFO_FLAGS enumeration
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 228b2d3286ad0b69a2eb813e18b8837ec038f28f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS
Décrit ou spécifie les propriétés d’un processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
typedef DWORD PROCESS_INFO_FLAGS;  
```  
  
```csharp  
enum enum_PROCESS_INFO_FLAGS {   
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
 Indique que le processus est en cours de débogage par un débogueur. Il peut être un [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] débogueur, ou il peut être certains autres débogueur, par exemple, le débogueur WinDbg.  
  
 PIFLAG_PROCESS_STOPPED  
 Indique que le processus est arrêté. Valide uniquement si `PIFLAG_DEBUGGER_ATTACHED` est également spécifié. Disponible dans [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)] et versions ultérieures.  
  
 PIFLAG_PROCESS_RUNNING  
 Indique que le processus est en cours d’exécution. Valide uniquement si `PIFLAG_DEBUGGER_ATTACHED` est également spécifié. Disponible dans [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)] et versions ultérieures.  
  
## <a name="remarks"></a>Remarques  
 Utilisé pour le `Flags` membre de la [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) structure.  
  
 Ces indicateurs peuvent être combinées avec une opération de bits `OR`.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)