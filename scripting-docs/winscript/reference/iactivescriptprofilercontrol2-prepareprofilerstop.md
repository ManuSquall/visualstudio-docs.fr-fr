---
title: "IActiveScriptProfilerControl2::PrepareProfilerStop | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerControl2::PrepareProfilerStop"
ms.assetid: e43a63bc-c44f-44a8-9db4-29062b9e6a16
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerControl2::PrepareProfilerStop
Informe le profileur que vous souhaitez arrêter le profilage sur tous les moteurs de script applicables.  En utilisant cette méthode, vous pouvez obtenir la pile des appels complète si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] exécute lorsque vous arrêtez de profilage.  
  
## Syntaxe  
  
```  
HRESULT PrepareProfilerStop();  
```  
  
#### Paramètres  
 La méthode n'accepte pas de paramètre.  
  
## Valeur de retour  
 Retourne un HRESULT.  Les valeurs possibles sont les suivantes :  
  
|Valeur de retour|Signification|  
|----------------------|-------------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|Le profilage n'a pas pu être démarré.|  
|`S_FALSE`|Le profilage a été arrêté lorsqu'un script ne s'exécutait pas.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Le profilage n'est pas activé.|  
  
## Notes  
 Appelant `IActiveScriptProfilerControl2::PrepareProfilerStop` garantit que des événements pour les fonctions dans la pile des appels sont envoyés.  Cette méthode doit être appelée avant que vous cessiez de profiler sur n'importe quel moteur de script basé sur l'onglet actuel.  La méthode peut être appelée pour tout moteur de script.  
  
## Voir aussi  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [IActiveScriptProfilerControl2, interface](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)