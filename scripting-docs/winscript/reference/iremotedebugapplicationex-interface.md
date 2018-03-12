---
title: IRemoteDebugApplicationEx (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplicationEx Interface
ms.assetid: 8e16164d-dbb2-4488-9507-25ae34f343dc
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3360cea0d1649348a795356ad827b32b6f8ebc19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationex-interface"></a>IRemoteDebugApplicationEx (interface)
Représente une application en cours d’exécution. Il n’a pas besoin de correspondre à un processus de système d’exploitation. En règle générale, un débogueur cible une application pour le débogage. En général, le Gestionnaire de déboguer des processus implémente l’objet d’application.  
  
 Outre les méthodes héritées de `IUnknown`, le `IRemoteDebugApplicationEx` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|Retourne l’ID de processus pour l’application hôte.|  
|GetHostMachineName|Retourne le nom de l’ordinateur que l’application hôte est en cours d’exécution.|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|Définit la langue pour la localisation du débogueur.|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|Force le débogueur en mode de pas à pas.|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|Révoque une commande d’arrêt.|  
|SetProxyBlanketAndAddRef|Met à jour les informations de sécurité de COM sur un proxy pour un objet de débogueur pour assurer la compatibilité avec le débogage distant à partir de systèmes d’exploitation basés sur Windows 95.|  
|ReleaseFromSetProxyBlanket|AddRef mises en production à partir de SetProxyBlanketAndAddRef.|