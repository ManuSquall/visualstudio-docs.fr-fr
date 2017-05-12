---
title: "IActiveScriptError | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptError (interface)"
ms.assetid: c8e0288d-38ff-4145-a7e3-f8cdfb72eefe
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError
Un objet qui implémente cette interface est passé à la méthode d' [IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md) chaque fois que le moteur de script rencontre une erreur non gérée.  L'hôte appelle ensuite des méthodes sur cet objet pour obtenir des informations sur l'erreur qui s'est produite.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IActiveScriptError::GetExceptionInfo](../../winscript/reference/iactivescripterror-getexceptioninfo.md)|Récupère des informations sur une erreur.|  
|[IActiveScriptError::GetSourcePosition](../../winscript/reference/iactivescripterror-getsourceposition.md)|Récupère l'emplacement dans le code source où une erreur s'est produite.|  
|[IActiveScriptError::GetSourceLineText](../../winscript/reference/iactivescripterror-getsourcelinetext.md)|Extrait la ligne du fichier source où une erreur s'est produite.|  
  
## Voir aussi  
 [Script actif, interfaces](../../winscript/reference/active-script-interfaces.md)