---
title: "IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug"
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Avertit l'hôte sur une erreur d'exécution du script lorsque Process Debug Manager ne recherche pas un débogueur juste\-à\-temps de script.  
  
 Pour implémenter un débogueur dans votre hôte, vous devez gérer [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md).  Selon une action utilisateur, l'hôte peut ou attacher le débogueur et retourner, ou retourne le démarrage du débogueur dans le paramètre d'OnScriptErrorDebug `pfEnterDebugger` .  Vous devez également implémenter cette interface pour obtenir des notifications sur l'erreur d'exécution même s'il n'existe aucun débogueur externe qui peut être interprète par Process Debug Manager.  
  
## Syntaxe  
  
```  
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### Paramètres  
 `pErrorDebug`  
 \[in\]  l'erreur d'exécution qui s'est produite.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 \[out\]  Si l'appel [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) si l'utilisateur décide de continuer sans débogage.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Vous devez également implémenter cette interface pour obtenir une notification.  
  
## Voir aussi  
 [IActiveScriptSiteDebugEx \(interface\)](../../winscript/reference/iactivescriptsitedebugex-interface.md)