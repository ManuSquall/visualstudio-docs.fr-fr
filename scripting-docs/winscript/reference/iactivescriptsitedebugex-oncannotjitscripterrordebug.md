---
title: IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: e428f12b3d199603ac341a5e069fcc5ce5d36f93
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725109"
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Informe l’hôte sur une erreur d’exécution de script lorsque le processus de débogage Manager ne trouve pas un débogueur de script juste à temps.  
  
 Pour implémenter un débogueur dans votre hôte, vous devez gérer [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md). En fonction de l’action de l’utilisateur, l’ordinateur hôte pouvez attacher le débogueur et de retour ou retourner le démarrage du débogueur dans le OnScriptErrorDebug `pfEnterDebugger` paramètre. Vous devez également implémenter cette interface pour recevoir la notification sur l’erreur d’exécution même si il n’y a aucune débogueurs externes qui peuvent être interprétés par le Gestionnaire de processus de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Vous devez également implémenter cette interface pour obtenir une notification.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptSiteDebugEx](../../winscript/reference/iactivescriptsitedebugex-interface.md)