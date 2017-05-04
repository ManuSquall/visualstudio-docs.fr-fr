---
title: "IScriptEntry, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IScriptEntry (interface)"
ms.assetid: 86da3bc1-58b7-4d73-87ab-bc3ce34e3f41
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IScriptEntry, interface
Un objet qui implémente l'interface d' `IScriptEntry` représente un bloc de script ou un objet de fonction.  
  
 Outre les méthodes héritées de `IScriptNode`, l'interface `IScriptEntry` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|Retourne le texte qui correspond au corps d'un bloc de script d' `IScriptEntry` , d'un bloc de fonction, ou d'un scriptlet.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|Retourne le nom d'élément qui identifie un objet d' `IScriptEntry` .|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|Pour les entrées qui représentent un objet unique \(tel qu'une fonction\), retourne le nom de l'objet.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|Retourne la position de départ et la longueur d'une entrée.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|Les informations de type de retour pour un objet de fonction d' `IScriptEntry` .|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|Retourne le texte qui correspond à un bloc de script d' `IScriptEntry` , ou le code source contenu dans un gestionnaire d'événements d' `IScriptScriptlet` .|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|Définit le texte situé au corps d'un bloc de script d' `IScriptEntry` ou d'un scriptlet d' `IScriptScriptlet` .|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|Définit le nom de l'élément qui identifie un objet d' `IScriptEntry` .|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|Pour les entrées qui représentent un objet unique \(tel qu'une fonction\), définit le nom de l'objet.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|Définit les informations de type d'un objet de fonction d' `IScriptEntry` .|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|Définit le texte qui correspond à un bloc de script d' `IScriptEntry` , ou le code source contenu dans un gestionnaire d'événements d' `IScriptScriptlet` .|  
  
## Voir aussi  
 [Création de script actif, interfaces](../../winscript/reference/active-script-authoring-interfaces.md)