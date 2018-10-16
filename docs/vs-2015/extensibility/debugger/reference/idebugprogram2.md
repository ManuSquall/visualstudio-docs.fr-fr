---
title: IDebugProgram2 | Microsoft Docs
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
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cca25e55c43a94859588aca56f432e5c86dd5f94
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49213432"
---
# <a name="idebugprogram2"></a>IDebugProgram2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface représente un programme qui s’exécute dans un processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Le moteur de débogage (dé) et un fournisseur de port personnalisé implémentent cette interface pour représenter un programme dans un processus. Le Gestionnaire de session de débogage (SDM) implémente également cette interface pour fournir des informations à [attacher](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Le [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) événement retourne cette interface pour un nouveau programme. Cette interface est également utilisée en tant que paramètre pour de nombreuses méthodes sur plusieurs interfaces.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugProgram2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Énumère les threads qui sont exécutent dans ce programme.|  
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Obtient le nom du programme.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Obtient le processus de ce programme est en cours d’exécution dans.|  
|[Terminate](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Met fin à ce programme.|  
|[Attacher](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Joint à ce programme.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Détermine si un moteur de débogage (dé) pouvez détacher du programme.|  
|[Détacher](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Détache le débogueur à partir de ce programme.|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Obtient un identificateur global unique pour ce programme.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Obtient les propriétés de programme.|  
|[Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continue de s’exécuter ce programme à partir d’un état arrêté. N’importe quel état de l’exécution précédente est effacé.|  
|[Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continue de s’exécuter ce programme à partir d’un état arrêté. N’importe quel état de l’exécution précédente est conservé.|  
|[Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Effectue une étape.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Demande que ce programme arrête l’exécution de la prochaine heure d’un de ses exécute le code threads.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Obtient le nom et l’identificateur du moteur de débogage (dé) ce programme en cours d’exécution.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Énumère les contextes de code pour une position donnée dans un fichier source.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Obtient les octets de mémoire pour ce programme.|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Obtient le flux de code machine pour ce programme ou une partie de ce programme.|  
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Énumère les modules que ce programme a chargé et s’exécute.|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Obtient la mise à jour de modifier & Continuer (ENC) pour ce programme.<br /><br /> Un moteur de débogage personnalisé n’implémente pas cette méthode (elle doit toujours retourner `E_NOTIMPL`).|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Énumère les chemins de code de ce programme.|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Écrit un fichier de vidage dans un fichier.|  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Notes  
 Un programme est un conteneur de thread en cours d’exécution dans une architecture particulière de l’exécution, pendant un processus est constitué d’un ou plusieurs programmes.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Suivant](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Événement](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)

