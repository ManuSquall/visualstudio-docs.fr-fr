---
title: "IDebugProgram2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2"
helpviewer_keywords: 
  - "Interface de IDebugProgram2"
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# IDebugProgram2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface représente un programme qui s'exécute dans un processus.  
  
## Syntaxe  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le moteur \(DE\) de débogage et un fournisseur de port implémentent cette interface pour représenter un programme dans un processus.  le gestionnaire de débogage de session \(SDM\) implémente également cette interface pour fournir des informations à [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## Remarques pour les appelants  
 L'événement d' [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) retourne cette interface pour un nouveau programme.  Cette interface est également utilisée comme paramètre pour de nombreuses méthodes sur plusieurs interfaces.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugProgram2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Énumère les threads qui exécutent dans ce programme.|  
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|obtient le nom du programme.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Obtient le processus que ce programme est exécuté.|  
|[Terminer](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|termine ce programme.|  
|[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Liés à ce programme.|  
|[CanDetach](../Topic/IDebugProgram2::CanDetach.md)|Détermine si un moteur de \(DE\) débogage peut se détacher du programme.|  
|[Detach](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|détache le débogueur de ce programme.|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|obtient un identificateur global unique pour ce programme.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Obtient les propriétés de programme.|  
|[Exécuter](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continue de s'exécuter ce programme d'un état arrêté.  Tout état précédent d'exécution est désactivé.|  
|[Continuer](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continue de s'exécuter ce programme d'un état arrêté.  Tout état précédent d'exécution est conservé.|  
|[Étape](../../../extensibility/debugger/reference/idebugprogram2-step.md)|effectue une étape.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Les demandes que ce programme arrêtent l'exécution la prochaine fois un de ses thread exécute du code.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Obtient le nom et l'identificateur du moteur de débogage \(DE\) l'exécution de ce programme.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|énumère les contextes de code pour une position donnée dans un fichier source.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|obtient les octets de mémoire pour ce programme.|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Obtient le flux de code machine pour cette programme ou partie de ce programme.|  
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|énumère les modules que ce programme a chargés et exécute.|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Place la modification et continue la mise à jour \(P.J.\) pour ce programme.<br /><br /> Un moteur de débogage personnalisé n'applique pas cette méthode \(il doit toujours retourner `E_NOTIMPL`\).|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|énumère les chemins de code de ce programme.|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|écrit un dump à un fichier.|  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Notes  
 Un programme est un bon fonctionnement de conteneur de thread dans l'architecture à l'exécution particulière, alors qu'un processus contient un ou plusieurs programmes.  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../Topic/IDebugThread2::GetProgram.md)   
 [Suivant](../Topic/IEnumDebugPrograms2::Next.md)   
 [Événement](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)