---
title: IActiveScriptProfilerControl2::CompleteProfilerStart | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::CompleteProfilerStart
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0230ecb480792b5b24b7375f5b95926735d0a61
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571553"
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
Notifie le profileur que vous avez commencé à profiler sur tous les moteurs de script applicables. À l’aide de cette méthode, vous pouvez obtenir la pile des appels complète si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] est en cours d’exécution lorsque vous démarrez le profilage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CompleteProfilerStart();  
```  
  
#### <a name="parameters"></a>Paramètres  
 La méthode ne prend pas de paramètres.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un HRESULT. Les valeurs possibles sont les suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|Impossible de démarrer le profilage.|  
|`S_FALSE`|Le profilage a démarré lorsqu’un script n’était pas en cours d’exécution.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Le profilage n’est pas activé. Aucun rappel n’a été défini.|  
|`E_OUTOFMEMORY`|La pile des appels ne peut pas être obtenue en raison d’une condition de mémoire insuffisante.|  
  
## <a name="remarks"></a>Notes  
 L’appel de `IActiveScriptProfilerControl2::CompleteProfilerStart` garantit que les événements des fonctions qui se trouvent déjà dans la pile des appels sont envoyés. Cette méthode doit être appelée après le démarrage du profilage sur tout moteur de script qui se trouve sous l’onglet actuel. La méthode peut être appelée pour tout moteur de script.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [Interface IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)