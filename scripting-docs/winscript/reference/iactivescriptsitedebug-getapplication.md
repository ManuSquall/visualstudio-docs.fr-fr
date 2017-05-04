---
title: "IActiveScriptSiteDebug::GetApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.GetApplication
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::GetApplication"
ms.assetid: 4400f1b1-3108-4a71-b1f1-43586fe1227c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::GetApplication
Retourne l'objet application de débogage associé à ce site de script.  
  
## Syntaxe  
  
```  
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### Paramètres  
 `ppda`  
 \[out\]  Pointeur vers l'objet application de débogage associé au site de script.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_NOTIMPL`|L'hôte ne prend pas directement en charge le débogage.|  
  
## Notes  
 La méthode d' `GetApplication` offre un moyen pour qu'un hôte intelligent définisse l'objet d'application dans lequel chaque script appartient.  Les moteurs de script doivent tenter d'appeler cette méthode pour obtenir leur application et station de congé contenantes à `IProcessDebugManager::GetDefaultApplication` si cela échoue.  
  
## Voir aussi  
 [IActiveScriptSiteDebug, interface](../../winscript/reference/iactivescriptsitedebug-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)