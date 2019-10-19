---
title: IActiveScriptProfilerControl2 ::P repareProfilerStop | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 24d4d73e0263882ad028ea66d3fac5e24f3af9ba
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571446"
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
Indique au profileur que vous allez arrêter le profilage sur tous les moteurs de script applicables. À l’aide de cette méthode, vous pouvez obtenir la pile des appels complète si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] est en cours d’exécution lorsque vous arrêtez le profilage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT PrepareProfilerStop();  
```  
  
#### <a name="parameters"></a>Paramètres  
 La méthode ne prend pas de paramètres.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un HRESULT. Les valeurs possibles sont les suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|Impossible de démarrer le profilage.|  
|`S_FALSE`|Le profilage a été arrêté lorsqu’un script n’était pas en cours d’exécution.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Le profilage n’est pas activé.|  
  
## <a name="remarks"></a>Notes  
 L’appel de `IActiveScriptProfilerControl2::PrepareProfilerStop` garantit que les événements pour les fonctions de la pile des appels sont envoyés. Cette méthode doit être appelée avant d’arrêter le profilage sur un moteur de script qui se trouve sous l’onglet actuel. La méthode peut être appelée pour tout moteur de script.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptProfilerControl2 :: CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)    
 [Interface IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)