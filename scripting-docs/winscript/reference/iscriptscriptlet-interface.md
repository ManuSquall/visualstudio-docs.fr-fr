---
title: Interface IScriptScriptlet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptScriptlet interface
ms.assetid: b9981908-a337-4228-864c-c741f111ab2d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a3b7c4af7769a1a2851e9be4e2639a324a3c06fb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345914"
---
# <a name="iscriptscriptlet-interface"></a>IScriptScriptlet, interface
Un objet qui implémente le `IScriptScriptlet` interface représente un script du Gestionnaire d’événements.  
  
 Outre les méthodes héritées de `IScriptEntry`, le `IScriptScriptlet` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|Retourne le nom de l’événement qui est associé avec le scriptlet.|  
|[IScriptScriptlet:: GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|Retourne le nom d’événement simple qui est associé à un scriptlet. Il s’agit d’un nom de mot unique qui ne contient-elle pas de n’importe quel espace blanc.|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|Retourne le dernier identificateur dans le nom qualifié complet de l’hôte de l’objet d’un scriptlet.|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|Définit le nom de l’événement qui est associé avec le scriptlet.|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|Définit le nom d’événement simple qui est associé à un scriptlet. Il s’agit d’un nom de mot unique qui ne contient-elle pas de n’importe quel espace blanc.|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|Définit le dernier identificateur dans le nom qualifié complet de l’hôte de l’objet d’un scriptlet.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de création de scripts actifs](../../winscript/reference/active-script-authoring-interfaces.md)