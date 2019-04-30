---
title: IActiveScriptSiteWindow::EnableModeless | Microsoft Docs
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
ms.openlocfilehash: 4f15135273b98a65903a5d03de87c541fc032cce
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992924"
---
# <a name="iactivescriptsitewindowenablemodeless"></a>IActiveScriptSiteWindow::EnableModeless
Force l’hôte activer ou désactiver la fenêtre principale, ainsi que toutes les boîtes de dialogue non modale.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `fEnable`  
 [in] Indicateur qui, si `TRUE`, permet à la fenêtre principale et les boîtes de dialogue non modales ou, si `FALSE`, les désactive.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_FAIL` si une erreur s’est produite.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est identique à la `IOleInPlaceFrame::EnableModeless` (méthode).  
  
 Appels à cette méthode peuvent être imbriquées.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)