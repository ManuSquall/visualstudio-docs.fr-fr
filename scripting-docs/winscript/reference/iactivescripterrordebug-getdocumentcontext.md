---
title: "IActiveScriptErrorDebug::GetDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptErrorDebug.GetDocumentContext
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptErrorDebug::GetDocumentContext"
ms.assetid: 567601a1-551a-4905-bda1-1f54610174f4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptErrorDebug::GetDocumentContext
Fournit le contexte de le document pour cette erreur.  
  
## Syntaxe  
  
```  
HRESULT GetDocumentContext(  
   IDebugDocumentContext**  ppssc  
);  
```  
  
#### Paramètres  
 `ppssc`  
 \[out\]  Le contexte de le document pour cette erreur.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 La plage de caractère\- position de contexte de document doit inclure tous les caractères correspondant à l'erreur.  
  
## Voir aussi  
 [IActiveScriptErrorDebug, interface](../../winscript/reference/iactivescripterrordebug-interface.md)