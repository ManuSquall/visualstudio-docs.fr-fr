---
title: Interface IRemoteDebugApplicationEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplicationEx Interface
ms.assetid: 8e16164d-dbb2-4488-9507-25ae34f343dc
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2fd51d5bdd076199167e52f685f16572756f9740
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346551"
---
# <a name="iremotedebugapplicationex-interface"></a>IRemoteDebugApplicationEx (interface)
Représente une application en cours d’exécution. Il n’a pas besoin de correspondre à un processus de système d’exploitation. En règle générale, un débogueur cible une application pour le débogage. Le Gestionnaire de débogage de processus implémente généralement l’objet d’application.  
  
 Outre les méthodes héritées de `IUnknown`, le `IRemoteDebugApplicationEx` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|Retourne l’ID de processus pour l’application hôte.|  
|GetHostMachineName|Retourne le nom de l’ordinateur de l’application hôte est en cours d’exécution.|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|Définit la langue pour la localisation du débogueur.|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|Force le débogueur en mode de pas à pas.|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|Révoque une commande break.|  
|SetProxyBlanketAndAddRef|Met à jour les informations de sécurité de COM sur un proxy pour un objet de débogueur pour assurer la compatibilité avec le débogage distant à partir de systèmes d’exploitation basés sur Windows 95.|  
|ReleaseFromSetProxyBlanket|AddRef mises en production à partir de SetProxyBlanketAndAddRef.|