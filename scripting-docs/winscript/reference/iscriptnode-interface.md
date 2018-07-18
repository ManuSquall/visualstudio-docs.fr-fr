---
title: IScriptNode (Interface) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptNode interface
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 788be3fe9cb5ba529e3d1ca653d4f0f5c35b5932
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24733779"
---
# <a name="iscriptnode-interface"></a>IScriptNode, interface
Un objet qui implémente le `IScriptNode` interface représente une page Web.  
  
 Outre les méthodes héritées de `IUnknown`, le `IScriptNode` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|Indique si un objet est toujours actif.|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|Ajoute une instance enfant de `IScriptEntry`.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|Ajoute un scriptlet comme une instance de l’enfant d’un `IScriptNode`.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|Supprime l’arborescence d’objets.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|Retourne l’enfant qui est à l’index spécifié dans le nœud.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|Retourne une valeur définie par l’application qui est utilisée pour associer un scriptlet avec l’objet hôte.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|Retourne l’index d’un objet dans la liste des enfants du parent.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|Retourne le langage de script qui est utilisé par le nœud de script actuel.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|Retourne le nombre de nœuds enfants de la `IScriptNode` objet.|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|Retourne le `IScriptNode` objet qui est le parent d’un objet.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de création de scripts actifs](../../winscript/reference/active-script-authoring-interfaces.md)