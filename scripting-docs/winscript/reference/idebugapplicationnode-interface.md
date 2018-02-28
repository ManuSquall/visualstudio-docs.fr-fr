---
title: IDebugApplicationNode (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode interface
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 110e04d1c990f1b22f9740d8118a47f485dd041e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnode-interface"></a>IDebugApplicationNode, interface
Le `IDebugApplicationNode` interface étend les fonctionnalités de la `IDebugDocumentProvider` interface en fournissant un contexte dans une arborescence du projet.  
  
 Outre les méthodes héritées de `IDebugDocumentProvider`, le `IDebugApplicationNode` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugApplicationNode::EnumChildren](../../winscript/reference/idebugapplicationnode-enumchildren.md)|Énumère les nœuds enfants de ce nœud de l’application.|  
|[IDebugApplicationNode::GetParent](../../winscript/reference/idebugapplicationnode-getparent.md)|Retourne le nœud parent de ce nœud de l’application.|  
|[IDebugApplicationNode::SetDocumentProvider](../../winscript/reference/idebugapplicationnode-setdocumentprovider.md)|Définit le fournisseur de document pour ce nœud de l’application.|  
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|Provoque cette application pour libérer toutes les références et d’entrer dans un état inactif.|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|Ajoute ce nœud de l’application à l’arborescence du projet spécifié.|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|Supprime ce nœud de l’application à partir de l’arborescence du projet.|