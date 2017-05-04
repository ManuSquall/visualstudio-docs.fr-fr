---
title: "IActiveScriptSiteWindow::GetWindow | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteWindow.GetWindow
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteWindow_GetWindow"
ms.assetid: 6284e38c-9dfb-4d69-903d-f243f78c0331
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteWindow::GetWindow
Récupère le handle vers une fenêtre qui peut agir comme propriétaire d'une fenêtre indépendante que le moteur de script doit afficher.  
  
## Syntaxe  
  
```  
HRESULT GetWindow(  
    HWND *phwnd  // address of variable for window handle  
);  
```  
  
#### Paramètres  
 `phwnd`  
 \[out\]  Adresse d'une variable qui accepte le handle de fenêtre.  
  
## Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_FAIL` si une erreur se produit.  
  
## Notes  
 Cette méthode est similaire à la méthode `IOleWindow::GetWindow`.  
  
## Voir aussi  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)