---
title: IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c643478da37b5a66c22b201ef8f8248df02e4ec
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992344"
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Informe l’hôte sur une erreur d’exécution de script lorsque le processus de débogage Manager ne trouve pas un débogueur de script juste à temps.  
  
 Pour implémenter un débogueur dans votre hôte, vous devez gérer [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md). Selon une action de l’utilisateur, l’hôte est possible d’associer le débogueur et retourner, ou retourner le démarrage du débogueur dans le OnScriptErrorDebug `pfEnterDebugger` paramètre. Vous devez également implémenter cette interface pour obtenir la notification sur l’erreur d’exécution, même s’il en existe aucun débogueurs externes qui peuvent être interprétées par le Gestionnaire de débogage de processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pErrorDebug`  
 [in] Erreur d’exécution qui s’est produite.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 [out] S’il faut appeler [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) si l’utilisateur décide de continuer sans le débogage.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Vous devez également implémenter cette interface pour recevoir une notification.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptSiteDebugEx](../../winscript/reference/iactivescriptsitedebugex-interface.md)