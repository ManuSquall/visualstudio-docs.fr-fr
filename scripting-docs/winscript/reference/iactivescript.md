---
title: "IActiveScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScript (interface)"
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript
Fournit des méthodes nécessaires pour initialiser le moteur de script.  Le moteur de script doit implémenter l'interface d' `IActiveScript` .  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Informe le moteur de script du site d' [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) fourni par l'hôte.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Récupère l'objet de site associé avec le moteur de Script Windows.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Définit le moteur de script dans l'état spécifié.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Récupère l'état actuel du moteur de script.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Fait pour abandonner tout script actuellement chargé, pour détruire son état, et pour libérer le moteur de script tous les pointeurs d'interface qu'elle doit d'autres objets, ainsi entrant un état fermé.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Ajoute le nom d'un élément racine à l'espace de noms du moteur de script.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Ajoute une bibliothèque de types dans l'espace de noms pour le script.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Récupère l'interface d' `IDispatch` pour le script en cours de exécution.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Récupère un identificateur script\-engine\- défini pour le thread en cours.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Récupère un identificateur script\-engine\- défini pour le thread associé au thread donné Microsoft Win32.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Récupère l'état actuel d'un thread de script.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Interrompt l'exécution d'un thread en cours de exécution du script.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Clone le moteur de script actuel \(moins un état en cours de exécution\), en retournant un moteur de script chargé sans site dans le thread actuel.|  
  
## Voir aussi  
 [Interfaces Windows Script, référence](../../winscript/reference/windows-script-interfaces-reference.md)