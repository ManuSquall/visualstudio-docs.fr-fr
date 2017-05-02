---
title: "IActiveScriptError::GetSourceLineText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptError.GetSourceLineText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptError_GetSourceLineText"
ms.assetid: 64f7f37f-7288-4dbe-b626-a35d90897f36
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError::GetSourceLineText
Extrait la ligne du fichier source où une erreur s'est produite pendant qu'un moteur de script s'exécutait un script.  
  
## Syntaxe  
  
```  
HRESULT GetSourceLineText(  
    BSTR *pbstrSourceLine  // address of buffer for source line  
);  
```  
  
## Paramètre  
 `pbstrSourceLine`  
 \[out\]  Adresse d'une mémoire tampon qui accepte la ligne de code source dans laquelle l'erreur s'est produite.  
  
## Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_FAIL` si la ligne dans le fichier source n'est pas récupérée.  
  
## Voir aussi  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)