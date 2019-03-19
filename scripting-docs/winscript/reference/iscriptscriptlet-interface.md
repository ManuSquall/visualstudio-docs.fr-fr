---
title: Interface IScriptScriptlet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: c11aada6b8c39c7dd5f0b2a6b30cdd837aa0edda
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151256"
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