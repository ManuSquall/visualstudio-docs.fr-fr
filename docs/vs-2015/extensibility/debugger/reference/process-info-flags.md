---
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 03eb17934620a1ec8bf23d28519d5615fab62ef6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49298309"
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Décrivent ou spécifient les propriétés d’un processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 Indique que le processus est en cours de débogage par un débogueur. Il peut être un [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] débogueur, ou il peut être certains autres débogueur, par exemple WinDbg.  
  
 PIFLAG_PROCESS_STOPPED  
 Indique que le processus est arrêté. Valide uniquement si `PIFLAG_DEBUGGER_ATTACHED` est également spécifié. Disponible dans [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] et versions ultérieures.  
  
 PIFLAG_PROCESS_RUNNING  
 Indique que le processus est en cours d’exécution. Valide uniquement si `PIFLAG_DEBUGGER_ATTACHED` est également spécifié. Disponible dans [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] et versions ultérieures.  
  
## <a name="remarks"></a>Notes  
 Utilisé pour le `Flags` membre de la [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) structure.  
  
 Ces indicateurs peuvent être combinées avec un opérateur de bits `OR`.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)

