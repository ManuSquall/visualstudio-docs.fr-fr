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
ms.openlocfilehash: 7b7973aee209695592f022d0e05a770caa1e694c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571885"
---
# <a name="iscriptscriptlet-interface"></a>IScriptScriptlet, interface
Un objet qui implémente l’interface `IScriptScriptlet` représente un script de gestionnaire d’événements.  
  
 En plus des méthodes héritées de `IScriptEntry`, l’interface `IScriptScriptlet` expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|Retourne le nom de l’événement associé au scriptlet.|  
|[IScriptScriptlet:: GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|Retourne le nom d’événement simple associé à un scriptlet. Il s’agit d’un nom de mot unique qui ne contient aucun espace blanc.|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|Retourne le dernier identificateur dans le nom qualifié complet de l’hôte d’objet d’un scriptlet.|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|Définit le nom de l’événement associé au scriptlet.|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|Définit le nom d’événement simple associé à un scriptlet. Il s’agit d’un nom de mot unique qui ne contient aucun espace blanc.|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|Définit le dernier identificateur dans le nom qualifié complet de l’hôte d’objet d’un scriptlet.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de création de scripts actifs](../../winscript/reference/active-script-authoring-interfaces.md)