---
title: "IActiveScriptSite::OnScriptError | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnScriptError
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnScriptError"
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnScriptError
Signale à l'hôte qu'une erreur d'exécution s'est produite pendant que le moteur exécutait le script.  
  
## Syntaxe  
  
```  
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### Paramètres  
 `pase`  
 \[in\]  adresse de l'interface d' [IActiveScriptError](../../winscript/reference/iactivescripterror.md) de l'objet d'erreur.  Un hôte peut utiliser cette interface pour obtenir des informations sur l'erreur d'exécution.  
  
## Valeur de retour  
 Retourne `S_OK` si l'erreur a été correctement gérée, ou OLE code d'erreur défini sinon.  
  
## Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)