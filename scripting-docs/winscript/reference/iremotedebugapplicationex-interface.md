---
title: "IRemoteDebugApplicationEx (interface) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplicationEx (interface)"
ms.assetid: 8e16164d-dbb2-4488-9507-25ae34f343dc
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplicationEx (interface)
Représente une application active.  Elle n'a pas besoin de correspondre à un processus de système d'exploitation.  En général, un débogueur cible une demande de débogage.  Process Debug Manager implémente généralement l'objet application.  
  
 Outre les méthodes héritées de `IUnknown`, l'interface `IRemoteDebugApplicationEx` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|Retourne l'ID de processus pour l'application hôte.|  
|GetHostMachineName|Retourne le nom de l'ordinateur sur lequel l'application hôte s'exécute.|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|Définit le langage pour la localisation du débogueur.|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|Force le débogueur en mode en pas \- à \- pas.|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|Révoque une commande utilisable sur interruption.|  
|SetProxyBlanketAndAddRef|Les informations de sécurité COM de mises à jour sur un proxy pour un objet de débogueur garantisse la compatibilité avec le débogage distant Windows 95 est basé sur les systèmes d'exploitation.|  
|ReleaseFromSetProxyBlanket|Versions AddRef de SetProxyBlanketAndAddRef.|