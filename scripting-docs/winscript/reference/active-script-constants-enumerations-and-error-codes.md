---
title: "Script actif, constantes, &#233;num&#233;rations et codes d&#39;erreur | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Script actif, constantes, &#233;num&#233;rations et codes d&#39;erreur
Cette section décrit les énumérations et les codes d'erreur utilisés dans les moteurs de script windows.  
  
## Constantes  
  
|Constante|Description|  
|---------------|-----------------|  
|[SCRIPTTHREADID, constantes](../../winscript/reference/scriptthreadid-constants.md)|Spécifie le type de thread.|  
  
## Propriétés  
  
|Property|Description|  
|--------------|-----------------|  
|[SCRIPTPROP\_HOSTKEEPALIVE, propriété](../../winscript/reference/scriptprop-hostkeepalive-property.md)|Utilisé pour spécifier si le moteur de script doit être conservé entièrement fonctionnel \- si des références en cours.|  
  
## Énumérations  
  
|Énumération|Description|  
|-----------------|-----------------|  
|[SCRIPTGCTYPE, énumération](../../winscript/reference/scriptgctype-enumeration.md)|Le type de garbage collection à exécuter.|  
|[SCRIPTLANGUAGEVERSION, énumération](../../winscript/reference/scriptlanguageversion-enumeration.md)|Spécifie les versions possibles de script.|  
|[SCRIPTSTATE, énumération](../../winscript/reference/scriptstate-enumeration.md)|Spécifie l'état d'un moteur de script.|  
|||  
|[SCRIPTTHREADSTATE, énumération](../../winscript/reference/scriptthreadstate-enumeration.md)|Spécifie l'état d'un thread dans un moteur de script.|  
|[SCRIPTTRACEINFO, énumération](../../winscript/reference/scripttraceinfo-enumeration.md)|Représente l'événement de script qui est suivi.  Utilisé dans [IActiveScriptSiteTraceInfo::SendScriptTraceInfo, méthode](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).|  
|[SCRIPTUICHANDLING, énumération](../../winscript/reference/scriptuichandling-enumeration.md)|Représente la manière dont le contrôle d'IU doit être exécuté.|  
|[SCRIPTUICITEM, énumération](../../winscript/reference/scriptuicitem-enumeration.md)|Représente le type d'élément d'interface utilisateur.  Utilisé dans [IActiveScriptSiteUIControl::GetUIBehavior, méthode](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).|  
  
## Les codes d'erreur  
  
|Code d'erreur|Description|  
|-------------------|-----------------|  
|[SCRIPT\_E\_PROPAGATE, code d'erreur](../../winscript/reference/script-e-propagate-error-code.md)|Une erreur de script est propagée à l'appelant, qui peut être dans un thread différent.|  
|[SCRIPT\_E\_RECORDED, code d'erreur](../../winscript/reference/script-e-recorded-error-code.md)|Une erreur a été passée entre le moteur de script et l'hôte.|  
|[SCRIPT\_E\_REPORTED, code d'erreur](../../winscript/reference/script-e-reported-error-code.md)|Le moteur de script a signalé une exception non gérée à l'hôte.|  
  
## Voir aussi  
 [Script actif, interfaces](../../winscript/reference/active-script-interfaces.md)