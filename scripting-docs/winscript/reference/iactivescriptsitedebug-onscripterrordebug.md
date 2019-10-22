---
title: 'IActiveScriptSiteDebug :: OnScriptErrorDebug | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::OnScriptErrorDebug
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 894767b3dae9db54e8bc438a82b27195308a4342
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572209"
---
# <a name="iactivescriptsitedebugonscripterrordebug"></a>IActiveScriptSiteDebug::OnScriptErrorDebug
Permet à un hôte intelligent de déterminer comment gérer les erreurs d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pErrorDebug`  
 dans Erreur d’exécution qui s’est produite  
  
 `pfEnterDebugger`  
 à Indicateur précisant s’il faut passer l’erreur au débogueur pour effectuer un débogage juste-à-temps.  
  
 `pfCallOnScriptErrorWhenContinuing`  
 à Indicateur précisant s’il faut appeler `IActiveScriptSite::OnScriptError` lorsque l’utilisateur décide de continuer sans débogage.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles incluent, mais ne sont pas limitées à la valeur dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Un hôte actif peut utiliser cette méthode pour déterminer comment gérer les erreurs d’exécution.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptSiteDebug](../../winscript/reference/iactivescriptsitedebug-interface.md)