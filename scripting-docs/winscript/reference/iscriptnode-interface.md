---
title: Interface IScriptNode | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 38ab73ddb1bd924035cb6ba61d26e65f16f53eed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577514"
---
# <a name="iscriptnode-interface"></a>IScriptNode, interface
Un objet qui implémente l’interface `IScriptNode` représente une page Web.  
  
 En plus des méthodes héritées de `IUnknown`, l’interface `IScriptNode` expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|Indique si un objet est toujours actif.|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|Ajoute une instance enfant de `IScriptEntry`.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|Ajoute un scriptlet comme une instance enfant d’un `IScriptNode`.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|Supprime l’arborescence d’objets.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|Retourne l’enfant qui se trouve à l’index spécifié dans le nœud.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|Retourne une valeur définie par l’application qui est utilisée pour associer un scriptlet à l’objet hôte.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|Retourne l’index d’un objet dans la liste des enfants du parent.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|Retourne le langage de script utilisé par le nœud de script actuel.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|Retourne le nombre de nœuds enfants de l’objet `IScriptNode`.|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|Retourne l’objet `IScriptNode` qui est le parent d’un objet.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de création de scripts actifs](../../winscript/reference/active-script-authoring-interfaces.md)