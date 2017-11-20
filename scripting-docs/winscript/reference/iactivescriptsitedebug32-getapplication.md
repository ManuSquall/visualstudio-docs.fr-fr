---
title: IActiveScriptSiteDebug32::GetApplication | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 533d770d-06a4-4693-873e-255c9c6f0df0
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: bb7fdf5a6d0b380a8024cfdfa70282bcf80ba16d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32::GetApplication
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
 [Interface de IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)