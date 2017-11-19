---
title: IActiveScriptProfilerControl2::CompleteProfilerStart | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptProfilerControl2::CompleteProfilerStart
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5abd4ee4237991714bfe3d8ba21b083f1a1920cd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
Notifie le profileur que vous avez démarré le profilage sur tous les moteurs de script applicables. À l’aide de cette méthode, vous pouvez obtenir la pile des appels complète si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] est en cours d’exécution lorsque vous démarrez le profilage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CompleteProfilerStart();  
```  
  
#### <a name="parameters"></a>Paramètres  
 La méthode n’accepte aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une valeur HRESULT. Les valeurs possibles sont les suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|Impossible de démarrer le profilage.|  
|`S_FALSE`|Le profilage a été démarré quand un script n’était pas en cours d’exécution.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilage n’est pas activé. Aucun rappel n’a été défini.|  
|`E_OUTOFMEMORY`|La pile des appels ne peut pas être obtenue en raison d’une condition de mémoire insuffisante.|  
  
## <a name="remarks"></a>Remarques  
 Appel de `IActiveScriptProfilerControl2::CompleteProfilerStart` permet de s’assurer que les événements pour les fonctions déjà dans la pile des appels sont envoyés. Cette méthode doit être appelée après le profilage démarre sur n’importe quel moteur de script qui se trouve sur l’onglet actuel. La méthode peut être appelée pour les moteurs de script.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [Interface IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)