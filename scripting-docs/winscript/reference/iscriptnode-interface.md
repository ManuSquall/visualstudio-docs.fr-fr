---
title: "IScriptNode, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IScriptNode (interface)"
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# IScriptNode, interface
Un objet qui implémente l'interface d' `IScriptNode` représente une page Web.  
  
 Outre les méthodes héritées de `IUnknown`, l'interface `IScriptNode` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|Indique si un objet est encore actifs.|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|Ajoute une instance enfant d' `IScriptEntry`.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|Ajoute un scriptlet instance comme enfant d' `IScriptNode`.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|Supprime l'arborescence d'objets.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|Retourne l'enfant qui est à l'index spécifié dans le nœud.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|Retourne une valeur définie par l'application qui est utilisée pour associer un scriptlet avec l'objet hôte.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|Retourne l'index d'un objet de la liste enfant du parent.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|Retourne le langage de script utilisé par le nœud courant de script.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|Retourne le nombre de nœuds enfants de l'objet d' `IScriptNode` .|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|Retourne l'objet d' `IScriptNode` qui est le parent d'un objet.|  
  
## Voir aussi  
 [Création de script actif, interfaces](../../winscript/reference/active-script-authoring-interfaces.md)