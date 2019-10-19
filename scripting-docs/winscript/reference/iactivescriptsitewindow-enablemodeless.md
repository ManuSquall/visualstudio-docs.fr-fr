---
title: 'IActiveScriptSiteWindow :: EnableModeless | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.EnableModeless
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_EnableModeless
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 756bda6209b6209ff14f6d67fef18faaed0b5618
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574136"
---
# <a name="iactivescriptsitewindowenablemodeless"></a>IActiveScriptSiteWindow::EnableModeless
Fait en sorte que l’hôte active ou désactive sa fenêtre principale, ainsi que toutes les boîtes de dialogue non modales.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `fEnable`  
 dans Indicateur qui, si `TRUE`, active la fenêtre principale et les boîtes de dialogue non modales ou, si `FALSE`, les désactive.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_FAIL` si une erreur s’est produite.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est identique à la méthode `IOleInPlaceFrame::EnableModeless`.  
  
 Les appels à cette méthode peuvent être imbriqués.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)