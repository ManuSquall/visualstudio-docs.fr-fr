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
ms.openlocfilehash: 67e16e2825f03c9ae452e639d6a086bee584ac95
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992564"
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Implémenté par l’hôte pour créer un site pour le moteur de Script de Windows. En règle générale, ce site sera associé avec le conteneur de tous les objets qui sont visibles pour le script (par exemple, les contrôles ActiveX). En règle générale, ce conteneur correspond au document ou à la page affichée. Microsoft Internet Explorer, par exemple, créerait un conteneur de ce type pour chaque page HTML s’affiche. Chaque ActiveX contrôle (ou un autre objet automation) sur la page et le moteur de script lui-même, serait énumérable dans ce conteneur.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|||  
|-|-|  
|Méthode|Description|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Récupère l’identificateur de paramètres régionaux que l’hôte utilise pour l’affichage des éléments d’interface utilisateur.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Obtient des informations sur un élément qui a été ajouté à un moteur via un appel à la [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) (méthode).|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Récupère une chaîne définie par l’hôte qui identifie de façon unique la version actuelle de document à partir du point de vue de l’hôte.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Appelé lorsque le script a terminé son exécution.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Informe l’hôte que le moteur de script a modifié les États.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Informe l’hôte qu’une erreur d’exécution s’est produite pendant que le moteur a été exécute le script.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Informe l’hôte que le moteur de script a commencé l’exécution du code de script.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Informe l’hôte que le moteur de script a retourné de l’exécution de code de script.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de script actives](../../winscript/reference/active-script-interfaces.md)