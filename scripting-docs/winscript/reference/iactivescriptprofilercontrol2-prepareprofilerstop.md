---
title: IActiveScriptProfilerControl2::PrepareProfilerStop | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::PrepareProfilerStop
ms.assetid: e43a63bc-c44f-44a8-9db4-29062b9e6a16
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78078cd874be1d7d3d169be2d3d70e65866be3fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724519"
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
Notifie le profileur que vous vous apprêtez à arrêter le profilage sur tous les moteurs de script applicables. À l’aide de cette méthode, vous pouvez obtenir la pile des appels complète si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] est en cours d’exécution lorsque vous arrêtez le profilage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT PrepareProfilerStop();  
```  
  
#### <a name="parameters"></a>Paramètres  
 La méthode n’accepte aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une valeur HRESULT. Les valeurs possibles sont les suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|Le profilage n’a pas pu être démarré.|  
|`S_FALSE`|Le profilage a été arrêté lorsqu’un script n’était pas en cours d’exécution.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilage n’est pas activé.|  
  
## <a name="remarks"></a>Remarques  
 Appel de `IActiveScriptProfilerControl2::PrepareProfilerStop` permet de s’assurer que les événements pour les fonctions dans la pile des appels sont envoyés. Cette méthode doit être appelée avant d’arrêter le profilage sur n’importe quel moteur de script qui se trouve sur l’onglet actuel. La méthode peut être appelée pour les moteurs de script.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [Interface IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)