---
title: "IActiveScriptErrorDebug, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptErrorDebug (interface)"
ms.assetid: e5d50427-c033-4138-ac6e-3b2dfb3b750a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptErrorDebug, interface
Fournit des informations de contexte de le document pour les erreurs de compilation et des exceptions runtime.  La méthode d' `IActiveScriptError::QueryInterface` prend en charge l'interface d' `IActiveScriptErrorDebug` .  
  
 Outre les méthodes héritées de `IActiveScriptError`, l'interface `IActiveScriptErrorDebug` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IActiveScriptErrorDebug::GetDocumentContext](../../winscript/reference/iactivescripterrordebug-getdocumentcontext.md)|Fournit le contexte de le document pour cette erreur.|  
|[IActiveScriptErrorDebug::GetStackFrame](../../winscript/reference/iactivescripterrordebug-getstackframe.md)|Fournit le frame de pile appliqué pour les erreurs d'exécution.|