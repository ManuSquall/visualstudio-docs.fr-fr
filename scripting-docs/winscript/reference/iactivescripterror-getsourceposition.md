---
title: "IActiveScriptError::GetSourcePosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptError.GetSourcePosition
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptError_GetSourcePosition"
ms.assetid: ae9b26b1-82a7-4645-9686-3261d8248664
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError::GetSourcePosition
Récupère l'emplacement dans le code source où une erreur s'est produite pendant que le moteur de script s'exécutait un script.  
  
## Syntaxe  
  
```  
HRESULT GetSourcePosition(  
    DWORD *pdwSourceContext,  // context cookie  
    ULONG *pulLineNumber,     // line number of error  
    LONG *pichCharPosition    // character position of error  
);  
```  
  
#### Paramètres  
 `pdwSourceContext`  
 \[out\]  Adresse d'une variable qui accepte un cookie qui identifie le contexte.  La traduction de ce paramètre dépend de l'application hôte.  
  
 `pulLineNumber`  
 \[out\]  Adresse d'une variable qui accepte le numéro de ligne dans le fichier source où l'erreur s'est produite.  
  
 `pichCharPosition`  
 \[out\]  Adresse d'une variable qui accepte la position du caractère de la ligne où l'erreur s'est produite.  
  
## Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_FAIL` si l'emplacement n'a pas été extrait.  
  
## Voir aussi  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)