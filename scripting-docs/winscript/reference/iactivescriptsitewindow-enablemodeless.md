---
title: IActiveScriptSiteWindow::EnableModeless | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.EnableModeless
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_EnableModeless
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7099fe7d13a1cb3231e67049104722af9373d7a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitewindowenablemodeless"></a>IActiveScriptSiteWindow::EnableModeless
Force l’hôte activer ou désactiver la fenêtre principale, ainsi que toutes les boîtes de dialogue non modale.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `fEnable`  
 [in] Indicateur qui, si `TRUE`, permet à la fenêtre principale et les boîtes de dialogue non modales ou, si `FALSE`, les désactive.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_FAIL` si une erreur s’est produite.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode est identique à la `IOleInPlaceFrame::EnableModeless` (méthode).  
  
 Les appels à cette méthode peuvent être imbriqués.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)