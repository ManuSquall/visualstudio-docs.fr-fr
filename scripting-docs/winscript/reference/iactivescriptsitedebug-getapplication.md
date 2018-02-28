---
title: IActiveScriptSiteDebug::GetApplication | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetApplication
ms.assetid: 4400f1b1-3108-4a71-b1f1-43586fe1227c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e33bf254d2e688451f1b69a3b3eb1b676a9e9b1a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebuggetapplication"></a>IActiveScriptSiteDebug::GetApplication
Retourne l’objet d’application de débogage associé à ce site de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppda`  
 [out] Pointeur vers l’objet d’application de débogage associé au site de script.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_NOTIMPL`|L’ordinateur hôte ne prend pas directement en charge le débogage.|  
  
## <a name="remarks"></a>Remarques  
 Le `GetApplication` méthode offre un moyen pour un hôte actif définir l’objet d’application auquel appartient chaque script. Moteurs de script doivent tenter d’appeler cette méthode pour obtenir leur application conteneur et le recours au `IProcessDebugManager::GetDefaultApplication` en cas d’échec.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSiteDebug (Interface)](../../winscript/reference/iactivescriptsitedebug-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)