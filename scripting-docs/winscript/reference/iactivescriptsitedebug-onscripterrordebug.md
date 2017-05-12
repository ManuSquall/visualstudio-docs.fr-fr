---
title: "IActiveScriptSiteDebug::OnScriptErrorDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::OnScriptErrorDebug"
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::OnScriptErrorDebug
Permet à un hôte intelligent pour déterminer comment gérer les erreurs d'exécution.  
  
## Syntaxe  
  
```  
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### Paramètres  
 `pErrorDebug`  
 \[in\]  l'erreur d'exécution qui s'est produite  
  
 `pfEnterDebugger`  
 \[out\]  Marquez d'un indicateur indiquer si passer l'erreur au débogueur pour effectuer un débogage JIT.  
  
 `pfCallOnScriptErrorWhenContinuing`  
 \[out\]  Marquez d'un indicateur indiquer si `IActiveScriptSite::OnScriptError` appeler lorsque l'utilisateur décide de continuer sans débogage.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à la valeur dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Intelligent un hôte peut utiliser cette méthode pour déterminer comment gérer les erreurs d'exécution.  
  
## Voir aussi  
 [IActiveScriptSiteDebug, interface](../../winscript/reference/iactivescriptsitedebug-interface.md)