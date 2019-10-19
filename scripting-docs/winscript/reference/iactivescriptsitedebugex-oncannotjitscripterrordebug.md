---
title: 'IActiveScriptSiteDebugEx :: OnCanNotJITScriptErrorDebug | Microsoft Docs'
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
ms.openlocfilehash: 7358d2b372f0801b8c45816e1fc36018b37799b2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572180"
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Informe l’hôte d’une erreur d’exécution de script lorsque le gestionnaire de débogage de processus ne trouve pas de débogueur de script juste-à-temps.  
  
 Pour implémenter un débogueur dans votre hôte, vous devez gérer [IActiveScriptSiteDebug :: OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md). En fonction d’une action de l’utilisateur, l’hôte peut attacher le débogueur et retourner, ou retourner le démarrage du débogueur dans le paramètre de `pfEnterDebugger` OnScriptErrorDebug. Vous devez également implémenter cette interface pour obtenir la notification concernant l’erreur d’exécution, même s’il n’existe aucun débogueur externe pouvant être interprété par le gestionnaire de débogage de processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pErrorDebug`  
 dans Erreur d’exécution qui s’est produite.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 à Indique s’il faut appeler [IActiveScriptSiteDebug :: OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) si l’utilisateur décide de continuer sans débogage.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Vous devez également implémenter cette interface pour recevoir une notification.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptSiteDebugEx](../../winscript/reference/iactivescriptsitedebugex-interface.md)