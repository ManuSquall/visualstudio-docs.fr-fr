---
title: "IDebugApplicationNode, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode (interface)"
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugApplicationNode, interface
L'interface d' `IDebugApplicationNode` étend les fonctionnalités de l'interface d' `IDebugDocumentProvider` en fournissant une zone dans une arborescence du projet.  
  
 Outre les méthodes héritées de `IDebugDocumentProvider`, l'interface `IDebugApplicationNode` expose les méthodes suivantes.  
  
## Méthodes de commande de Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugApplicationNode::EnumChildren](../../winscript/reference/idebugapplicationnode-enumchildren.md)|Énumère les nœuds enfants de ce nœud d'application.|  
|[IDebugApplicationNode::GetParent](../../winscript/reference/idebugapplicationnode-getparent.md)|Retourne le nœud parent de ce nœud d'application.|  
|[IDebugApplicationNode::SetDocumentProvider](../../winscript/reference/idebugapplicationnode-setdocumentprovider.md)|Définit le fournisseur de le document pour ce nœud d'application.|  
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|Provoque cette application de libérer toutes les références et d'entrer un état inactif.|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|Ajoute ce nœud d'application à l'arborescence du projet spécifiée.|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|Supprime le nœud d'application de l'arborescence du projet.|