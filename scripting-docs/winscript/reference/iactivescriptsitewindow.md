---
title: IActiveScriptSiteWindow | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteWindow interface
ms.assetid: 96d5c493-2c0b-47e2-848b-4a8dacdcd65c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ee680a3d00c6736549b03ce8fee5593a7a8c5af
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575894"
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
Cette interface est implémentée par les hôtes qui prennent en charge une interface utilisateur sur le même objet que [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) . Les ordinateurs hôtes qui ne prennent pas en charge une interface utilisateur, tels que les serveurs, n’implémentent pas l’interface `IActiveScriptSiteWindow`. Le moteur de script accède à cette interface en appelant `QueryInterface` à partir de `IActiveScriptSite`.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Récupère le handle de fenêtre qui peut agir en tant que propriétaire d’une fenêtre indépendante que le moteur de script doit afficher.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|Fait en sorte que l’hôte active ou désactive sa fenêtre principale, ainsi que toutes les boîtes de dialogue non modales.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de script actives](../../winscript/reference/active-script-interfaces.md)