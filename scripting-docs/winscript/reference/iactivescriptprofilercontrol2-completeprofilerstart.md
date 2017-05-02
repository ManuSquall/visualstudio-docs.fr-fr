---
title: "IActiveScriptProfilerControl2::CompleteProfilerStart | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerControl2::CompleteProfilerStart"
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerControl2::CompleteProfilerStart
Informe le profileur que vous avez commencé à profiler sur tous les moteurs de script applicables.  En utilisant cette méthode, vous pouvez obtenir la pile des appels complète si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] exécute lorsque vous commencez à profiler.  
  
## Syntaxe  
  
```  
HRESULT CompleteProfilerStart();  
```  
  
#### Paramètres  
 La méthode n'accepte pas de paramètre.  
  
## Valeur de retour  
 Retourne un HRESULT.  Les valeurs possibles sont les suivantes :  
  
|Valeur de retour|Signification|  
|----------------------|-------------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|Le profilage ne peut pas être démarré.|  
|`S_FALSE`|Le profilage a été démarré lorsqu'un script ne s'exécutait pas.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Le profilage n'est pas activé.  Aucun rappel n'a été définie.|  
|`E_OUTOFMEMORY`|La pile des appels ne peut pas être obtenue en raison d'une condition de mémoire insuffisante.|  
  
## Notes  
 Appelant `IActiveScriptProfilerControl2::CompleteProfilerStart` garantit que des événements pour les fonctions déjà dans la pile des appels sont envoyés.  Cette méthode doit être appelée après profiler démarre sur tout moteur de script basé sur l'onglet actuel.  La méthode peut être appelée pour tout moteur de script.  
  
## Voir aussi  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [IActiveScriptProfilerControl2, interface](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)