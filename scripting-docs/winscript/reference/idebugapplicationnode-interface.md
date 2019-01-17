---
title: Interface IDebugApplicationNode | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode interface
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7bd38a0fbbdd596f6a1f6bb040190dddca78bf9
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348995"
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
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|Provoque cette application pour libérer toutes les références et entrer dans un état inactif.|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|Ajoute ce nœud de l’application à l’arborescence du projet spécifié.|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|Supprime ce nœud de l’application à partir de l’arborescence du projet.|