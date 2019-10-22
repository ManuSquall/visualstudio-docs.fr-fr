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
ms.openlocfilehash: 868322358908a32c8f14b56846cf3237f8531b4c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575396"
---
# <a name="iscriptentry-interface"></a>IScriptEntry, interface
Un objet qui implémente l’interface `IScriptEntry` représente un bloc de script ou un objet de fonction.  
  
 En plus des méthodes héritées de `IScriptNode`, l’interface `IScriptEntry` expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|Retourne le texte qui correspond au corps d’un `IScriptEntry` bloc de script, d’un bloc de fonction ou d’un scriptlet.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|Retourne le nom de l’élément qui identifie un objet `IScriptEntry`.|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|Pour les entrées qui représentent un seul objet (comme une fonction), retourne le nom de l’objet.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|Retourne la position de départ et la longueur d’une entrée.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|Retourne des informations de type pour un objet de fonction `IScriptEntry`.|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|Retourne le texte qui correspond à un `IScriptEntry` bloc de script, ou le code source contenu dans un gestionnaire d’événements `IScriptScriptlet`.|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|Définit le texte qui se trouve dans le corps d’un `IScriptEntry` bloc de script ou d’un scriptlet `IScriptScriptlet`.|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|Définit le nom de l’élément qui identifie un objet `IScriptEntry`.|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|Pour les entrées qui représentent un seul objet (par exemple, une fonction), définit le nom de l’objet.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|Définit des informations de type pour un objet de fonction `IScriptEntry`.|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|Définit le texte qui correspond à un bloc de script `IScriptEntry`, ou le code source contenu dans un gestionnaire d’événements `IScriptScriptlet`.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de création de scripts actifs](../../winscript/reference/active-script-authoring-interfaces.md)