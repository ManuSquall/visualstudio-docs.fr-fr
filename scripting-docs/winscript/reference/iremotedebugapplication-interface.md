---
title: IRemoteDebugApplication (Interface) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: ea91afdc44b70a91846d7b1a3dc4c017c0c4c80e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729599"
---
# <a name="iremotedebugapplication-interface"></a>IRemoteDebugApplication, interface
Représente une application en cours d’exécution. Il n’a pas besoin de correspondre à un processus de système d’exploitation. En règle générale, un débogueur cible une application pour le débogage. En général, le Gestionnaire de déboguer des processus implémente l’objet d’application.  
  
 Outre les méthodes héritées de `IUnknown`, le `IRemoteDebugApplication` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)|Continue une application en cours d’un point d’arrêt.|  
|[IRemoteDebugApplication::CauseBreak](../../winscript/reference/iremotedebugapplication-causebreak.md)|Entraîne l’application à s’arrêter dans le débogueur dès que possible.|  
|[IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)|Se connecte à un débogueur à cette application.|  
|[IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md)|Déconnecte le débogueur actif de l’application.|  
|[IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)|Retourne le débogueur actif est connecté à l’application.|  
|[IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)|Fournit un mécanisme pour que le débogueur IDE, en cours d’exécution out-of-process à l’application, pour créer des objets dans le processus d’application.|  
|[IRemoteDebugApplication::QueryAlive](../../winscript/reference/iremotedebugapplication-queryalive.md)|Indique si l’application ne répond.|  
|[IRemoteDebugApplication::EnumThreads](../../winscript/reference/iremotedebugapplication-enumthreads.md)|Énumère tous les threads connus pour être associé à l’application.|  
|[IRemoteDebugApplication::GetName](../../winscript/reference/iremotedebugapplication-getname.md)|Retourne le nom de ce nœud de l’application.|  
|[IRemoteDebugApplication::GetRootNode](../../winscript/reference/iremotedebugapplication-getrootnode.md)|Retourne le nœud d’application sous lequel tous les nœuds associés à l’application sont ajoutés.|  
|[IRemoteDebugApplication::EnumGlobalExpressionContexts](../../winscript/reference/iremotedebugapplication-enumglobalexpressioncontexts.md)|Énumère les contextes d’expression globale pour toutes les langues en cours d’exécution dans cette application.|