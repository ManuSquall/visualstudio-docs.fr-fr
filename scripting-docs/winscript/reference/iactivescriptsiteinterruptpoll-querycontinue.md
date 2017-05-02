---
title: "IActiveScriptSiteInterruptPoll::QueryContinue | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteInterruptPoll.QueryContinue
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteInterruptPoll::QueryContinue"
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteInterruptPoll::QueryContinue
Permet à un hôte de spécifier qu'un script se termine.  
  
## Syntaxe  
  
```  
HRESULT QueryContinue();  
```  
  
#### Paramètres  
 Cette méthode n'accepte pas de paramètres.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|L'appel a réussi et l'hôte permet au script de continuer à s'exécuter.|  
|`S_FALSE`|L'appel a réussi et les demandes d'hôte que le script se terminent.|  
  
## Notes  
 Le script hébergé doit se terminer à moins que la valeur de retour de la méthode d' `QueryContinue` soit `S_OK`.  Une valeur de retour d' `S_FALSE` indique que les demandes d'hôte explicitement que le script se terminent.  
  
 Un hôte multithread peut utiliser la méthode d' `IActiveScript::InterruptScriptThread` pour exécuter un script.  
  
## Voir aussi  
 [IActiveScriptSiteInterruptPoll, interface](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)