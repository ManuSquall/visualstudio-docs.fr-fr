---
title: "IScriptScriptlet, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IScriptScriptlet (interface)"
ms.assetid: b9981908-a337-4228-864c-c741f111ab2d
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptScriptlet, interface
Un objet qui implémente l'interface d' `IScriptScriptlet` représente un script de gestionnaire d'événements.  
  
 Outre les méthodes héritées de `IScriptEntry`, l'interface `IScriptScriptlet` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|Retourne le nom de l'événement associé au scriptlet.|  
|[IScriptScriptlet:: GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|Retourne le nom de l'événement simple qui est associé à un scriptlet.  Il s'agit d'un nom uniterme qui ne contient pas d'espaces blancs.|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|Retourne le dernier identificateur dans le nom qualifié complet de l'hôte de l'objet d'un scriptlet.|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|Définit le nom de l'événement associé au scriptlet.|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|Définit le nom de l'événement simple qui est associé à un scriptlet.  Il s'agit d'un nom uniterme qui ne contient pas d'espaces blancs.|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|Définit le dernier identificateur dans le nom qualifié complet de l'hôte de l'objet d'un scriptlet.|  
  
## Voir aussi  
 [Création de script actif, interfaces](../../winscript/reference/active-script-authoring-interfaces.md)