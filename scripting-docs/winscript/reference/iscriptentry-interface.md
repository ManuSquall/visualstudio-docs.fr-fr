---
title: Interface IScriptEntry | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptEntry interface
ms.assetid: 86da3bc1-58b7-4d73-87ab-bc3ce34e3f41
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dc50a6aa5cf032827feac6b483b141b79f60e77
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787722"
---
# <a name="iscriptentry-interface"></a>IScriptEntry, interface
Un objet qui implémente le `IScriptEntry` interface représente un bloc de script ou un objet de fonction.  
  
 Outre les méthodes héritées de `IScriptNode`, le `IScriptEntry` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|Retourne le texte qui correspond au corps d’un `IScriptEntry` bloc de script, un bloc de fonction ou scriptlet.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|Retourne le nom de l’élément qui identifie un `IScriptEntry` objet.|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|Pour les entrées qui représentent un seul objet (par exemple, une fonction), retourne le nom de l’objet.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|Retourne la position de début et la longueur d’une entrée.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|Retourne informations de type pour un `IScriptEntry` objet de fonction.|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|Retourne le texte qui correspond à un `IScriptEntry` bloc de script ou le code source qui est contenu dans un `IScriptScriptlet` Gestionnaire d’événements.|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|Définit le texte qui se trouve dans le corps d’un `IScriptEntry` bloc de script ou un `IScriptScriptlet` scriptlet.|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|Définit le nom de l’élément qui identifie un `IScriptEntry` objet.|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|Pour les entrées qui représentent un seul objet (par exemple, une fonction), définit le nom de l’objet.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|Jeux d’informations de type pour un `IScriptEntry` objet de fonction.|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|Définit le texte qui correspond à un `IScriptEntry` bloc de script ou le code source qui est contenu dans un `IScriptScriptlet` Gestionnaire d’événements.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de création de scripts actifs](../../winscript/reference/active-script-authoring-interfaces.md)