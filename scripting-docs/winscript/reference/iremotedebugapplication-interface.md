---
title: Interface IRemoteDebugApplication | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication interface
ms.assetid: 96bf2a3f-049f-46ba-86ad-57fc184343a2
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a231818def210f7c88ab031059f8561c67b33d1
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159151"
---
# <a name="iremotedebugapplication-interface"></a>IRemoteDebugApplication, interface
Représente une application en cours d’exécution. Il n’a pas besoin de correspondre à un processus de système d’exploitation. En règle générale, un débogueur cible une application pour le débogage. Le Gestionnaire de débogage de processus implémente généralement l’objet d’application.  
  
 Outre les méthodes héritées de `IUnknown`, le `IRemoteDebugApplication` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)|Continue une application en cours d’un point d’arrêt.|  
|[IRemoteDebugApplication::CauseBreak](../../winscript/reference/iremotedebugapplication-causebreak.md)|Oblige l’application à arrêter dans le débogueur au plus tôt.|  
|[IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)|Se connecte à un débogueur à cette application.|  
|[IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md)|Déconnecte le débogueur en cours de l’application.|  
|[IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)|Retourne le débogueur actif est connecté à l’application.|  
|[IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)|Fournit un mécanisme pour que le débogueur IDE, en cours d’exécution out-of-process à l’application, pour créer des objets dans le processus d’application.|  
|[IRemoteDebugApplication::QueryAlive](../../winscript/reference/iremotedebugapplication-queryalive.md)|Indique si l’application est réactive.|  
|[IRemoteDebugApplication::EnumThreads](../../winscript/reference/iremotedebugapplication-enumthreads.md)|Énumère tous les threads connus à associer à l’application.|  
|[IRemoteDebugApplication::GetName](../../winscript/reference/iremotedebugapplication-getname.md)|Retourne le nom de ce nœud de l’application.|  
|[IRemoteDebugApplication::GetRootNode](../../winscript/reference/iremotedebugapplication-getrootnode.md)|Retourne le nœud de l’application sous lequel tous les nœuds associés à l’application sont ajoutés.|  
|[IRemoteDebugApplication::EnumGlobalExpressionContexts](../../winscript/reference/iremotedebugapplication-enumglobalexpressioncontexts.md)|Énumère les contextes d’expression globale pour tous les langages s’exécutant dans cette application.|