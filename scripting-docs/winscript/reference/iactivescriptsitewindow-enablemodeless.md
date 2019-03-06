---
title: IActiveScriptSiteWindow::EnableModeless | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4cea23890539ca80abf8e3e58b0f8c48b7ca1fc9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093013"
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