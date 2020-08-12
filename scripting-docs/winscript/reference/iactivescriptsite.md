---
title: IActiveScriptSite | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSite interface
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dcf95f74e05ebff6e1cc430c32b9fd7bdb3b005f
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144660"
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Implémenté par l’hôte pour créer un site pour le moteur de script Windows. En règle générale, ce site est associé au conteneur de tous les objets qui sont visibles par le script (par exemple, les contrôles ActiveX). En règle générale, ce conteneur correspond au document ou à la page affiché. Microsoft Internet Explorer, par exemple, crée un conteneur de ce type pour chaque page HTML affichée. Chaque contrôle ActiveX (ou autre objet Automation) sur la page et le moteur de script lui-même, seraient énumérables dans ce conteneur.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|
|-|-|
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Récupère l’identificateur de paramètres régionaux utilisé par l’hôte pour afficher les éléments de l’interface utilisateur.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Obtient des informations sur un élément qui a été ajouté à un moteur par un appel à la méthode [IActiveScript :: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Récupère une chaîne définie par l’hôte qui identifie de façon unique la version du document actuel à partir du point de vue de l’hôte.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Appelée lorsque l’exécution du script est terminée.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Informe l’hôte que le moteur de script a modifié les États.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Informe l’hôte qu’une erreur d’exécution s’est produite lors de l’exécution du script par le moteur.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Informe l’hôte que le moteur de script a commencé à exécuter le code de script.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Informe l’hôte que le moteur de script a retourné à partir de l’exécution du code de script.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de script actives](../../winscript/reference/active-script-interfaces.md)