---
title: "IActiveScriptTraceInfo::StartScriptTracing, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 90fac5ed-ce15-49b7-a6f1-605ede6f34e2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptTraceInfo::StartScriptTracing, m&#233;thode
Suivi de script de démarrage.  
  
## Syntaxe  
  
```  
HRESULT StartScriptTracing(   
    [in] IActiveScriptSiteTraceInfo * pSiteTraceInfo,   
    [in] GUID guidContextID   
);  
  
```  
  
#### Paramètres  
 `pSiteTraceInfo`  
 Un pointeur vers IActiveScriptSiteTraceInfo de l'hôte.  
  
 `guidContextId`  
 GUID du contexte.  
  
## Valeur de retour  
 Les valeurs de retour possibles de cette méthode sont les suivantes :  
  
1.  S\_OK : succès.  
  
2.  E\_POINTER : `pSiteTraceInfo` est un pointeur null.  
  
3.  E\_NOTIMPL : non implémenté.