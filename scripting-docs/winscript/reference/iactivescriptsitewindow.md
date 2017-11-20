---
title: IActiveScriptSiteWindow | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptSiteWindow interface
ms.assetid: 96d5c493-2c0b-47e2-848b-4a8dacdcd65c
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3043a3c36b2f1ebdf439f22b1de19dd559e50cfa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
Cette interface est implémentée par les hôtes qui prennent en charge une interface utilisateur sur le même objet en tant que [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) . Les hôtes qui ne prennent pas en charge une interface utilisateur, tels que les serveurs, n’implémentent pas le `IActiveScriptSiteWindow` interface. Le moteur de script accède à cette interface en appelant `QueryInterface` de `IActiveScriptSite`.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Récupère le handle de fenêtre qui peut agir comme le propriétaire d’une fenêtre contextuelle que le moteur de script doit afficher.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|Force l’hôte activer ou désactiver la fenêtre principale, ainsi que toutes les boîtes de dialogue non modale.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de script actives](../../winscript/reference/active-script-interfaces.md)