---
title: "IActiveScriptSiteWindow | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSiteWindow (interface)"
ms.assetid: 96d5c493-2c0b-47e2-848b-4a8dacdcd65c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSiteWindow
Cette interface est implémentée par les hôtes qui prennent en charge une interface utilisateur sur le même objet qu' [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  Les hôtes qui ne prennent pas en charge une interface utilisateur, telles que les serveurs, n'implémenteraient pas l'interface d' `IActiveScriptSiteWindow` .  Le moteur de script accède à cette interface en appelant `QueryInterface` d' `IActiveScriptSite`.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Récupère le handle de fenêtre qui peut agir comme propriétaire d'une fenêtre indépendante que le moteur de script doit afficher.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|Pour activer ou désactiver l'hôte sa fenêtre principale ainsi que toutes les boîtes de dialogue non modale.|  
  
## Voir aussi  
 [Script actif, interfaces](../../winscript/reference/active-script-interfaces.md)