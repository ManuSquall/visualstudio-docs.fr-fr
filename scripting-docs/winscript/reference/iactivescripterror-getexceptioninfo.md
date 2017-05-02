---
title: "IActiveScriptError::GetExceptionInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptError.GetExceptionInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptError_GetExceptionInfo"
ms.assetid: 528416cc-8468-4ad7-a6c2-fa1daf6ecf33
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError::GetExceptionInfo
Récupère des informations sur une erreur qui s'est produite pendant que le moteur de script s'exécutait un script.  
  
## Syntaxe  
  
```  
HRESULT GetExceptionInfo(  
    EXCEPINFO *pexcepinfo  // structure for exception information  
);  
```  
  
#### Paramètres  
 `pexcepinfo`  
 \[out\]  Adresse d'une structure d' `EXCEPINFO` qui accepte les informations d'erreur.  
  
## Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_FAIL` si une erreur se produit.  
  
## Voir aussi  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)