---
title: "IActiveScriptSite | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSite (interface)"
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite
Implémenté par l'hôte pour créer un site pour le moteur de Script Windows.  Généralement, ce site est associé au conteneur de tous les objets qui sont visibles au script \(par exemple, les contrôles ActiveX\).  En général, ce conteneur correspondra au document ou à la page est affichée.  Microsoft Internet Explorer, par exemple, créerait un tel conteneur pour chaque page HTML affichée.  Chaque contrôle ActiveX \(ou tout autre objet Automation\) sur la page, et le moteur de script lui\-même, seraient énumérable dans ce conteneur.  
  
## Méthodes dans l'ordre Vtable  
  
|||  
|-|-|  
|Méthode|Description|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Récupère l'identificateur de paramètres régionaux que l'hôte utilise pour afficher des éléments de l'interface utilisateur.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Obtient des informations sur un élément ajouté à un moteur via un appel à la méthode d' [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Extrait une chaîne hôte définie qui identifie la version du document actuel du point de vue de l'hôte.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Appelé lorsque le script est terminé l'exécution.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Signale à l'hôte que le moteur de script a modifié des rapports.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Signale à l'hôte qu'une erreur d'exécution s'est produite pendant que le moteur exécutait le script.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Signale à l'hôte que le moteur de script a démarré l'exécution du code de script.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Signale à l'hôte que le moteur de script retournées d'exécuter le code de script.|  
  
## Voir aussi  
 [Script actif, interfaces](../../winscript/reference/active-script-interfaces.md)