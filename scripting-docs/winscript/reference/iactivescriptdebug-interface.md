---
title: "IActiveScriptDebug, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptDebug (interface)"
ms.assetid: e3e28cba-ee08-4a52-973a-b74be488c348
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptDebug, interface
Implémentée par les moteurs de script qui prennent en charge le débogage.  En général, un objet qui implémente l'interface d' `IActiveScriptDebug` également implémente l'interface d' `IActiveScript` .  Si tel est le cas, appelez la méthode d' `IActiveScript::QueryInterface` pour obtenir l'interface d' `IActiveScriptDebug` .  
  
 L'interface d' `IActiveScriptDebug` fournit le moyen pour :  
  
-   Intelligents hôtes pour fournir la gestion de documents.  
  
-   Le processus de débogage le gestionnaire pour synchroniser le débogage de plusieurs moteurs de script.  
  
 Outre les méthodes héritées de `IUnknown`, l'interface `IActiveScriptDebug` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)|Retourne les attributs de texte pour un bloc de texte arbitraire de script.|  
|[IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)|Retourne les attributs de texte pour un scriptlet arbitraire.|  
|[IActiveScriptDebug::EnumCodeContextsOfPosition](../../winscript/reference/iactivescriptdebug-enumcodecontextsofposition.md)|Délégués à `IDebugDocumentContext::EnumCodeContexts`.|