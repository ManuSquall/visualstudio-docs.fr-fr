---
title: "IActiveScriptSiteDebug, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSiteDebug (interface)"
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug, interface
Les hôtes intelligents implémentent l'interface d' `IActiveScriptSiteDebug` pour effectuer la gestion de documents et pour participer au débogage.  L'objet d' `IActiveScriptSite` fournit généralement une implémentation de l'interface d' `IActiveScriptSiteDebug` .  Si cela est fait, appelez la méthode d' `IActiveScriptSite::QueryInterface` pour obtenir l'interface d' `IActiveScriptSiteDebug` .  
  
 Outre les méthodes héritées de `IUnknown`, l'interface `IActiveScriptSiteDebug` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|Utilisé par le moteur de langue à déléguer `IDebugCodeContext::GetSourceContext`.|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|Retourne l'objet application de débogage associé à ce site de script.|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|Obtient le nœud d'application dans lequel les documents de script doivent être ajoutés.|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|Permet à un hôte intelligent pour déterminer comment gérer les erreurs d'exécution.|