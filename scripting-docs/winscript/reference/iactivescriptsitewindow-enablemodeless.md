---
title: "IActiveScriptSiteWindow::EnableModeless | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteWindow.EnableModeless
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteWindow_EnableModeless"
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSiteWindow::EnableModeless
Pour activer ou désactiver l'hôte sa fenêtre principale ainsi que toutes les boîtes de dialogue non modale.  
  
## Syntaxe  
  
```  
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### Paramètres  
 `fEnable`  
 \[in\]  Réduisez qui, si `TRUE`, active la fenêtre principale et les boîtes de dialogue non modales ou, si `FALSE`, les désactiver.  
  
## Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_FAIL`si une erreur se produit.  
  
## Notes  
 Cette méthode est identique à la méthode d' `IOleInPlaceFrame::EnableModeless` .  
  
 Les appels à cette méthode peuvent être imbriqués.  
  
## Voir aussi  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)