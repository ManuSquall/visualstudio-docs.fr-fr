---
title: IActiveScriptSiteWindow::GetWindow | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.GetWindow
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_GetWindow
ms.assetid: 6284e38c-9dfb-4d69-903d-f243f78c0331
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3257ac5632a2f3d713b6329a9a1eeebc4415851
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724899"
---
# <a name="iactivescriptsitewindowgetwindow"></a>IActiveScriptSiteWindow::GetWindow
Récupère le handle de fenêtre qui peut agir comme le propriétaire d’une fenêtre contextuelle que le moteur de script doit afficher.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetWindow(  
    HWND *phwnd  // address of variable for window handle  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `phwnd`  
 [out] Adresse d’une variable qui reçoit le handle de fenêtre.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_FAIL` si une erreur s’est produite.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode est similaire à la `IOleWindow::GetWindow` (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)