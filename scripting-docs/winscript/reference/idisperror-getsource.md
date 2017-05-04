---
title: "IDispError::GetSource | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetSource
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetSource"
ms.assetid: 20def54c-a67c-4102-babf-6f0704e5fc5c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetSource
Retourne l'identificateur programmatique dépendant du langage pour la classe ou l'application qui a déclenché l'erreur.  
  
## Syntaxe  
  
```  
HRESULT GetSource(  
   BSTR*  pbstrSource  
);  
```  
  
#### Paramètres  
 `pbstrSource`  
 \[out\]  Chaîne qui contient un identificateur programmatique, dans le formulaire `progname.objectname`.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode est utilisée pour déterminer la classe ou l'application où l'exception s'est produite.  L'identificateur programmatique peut être retourné dans le langage spécifié par l'ID de paramètres régionaux \(LCID\) fourni au moment de l'appel.  
  
> [!NOTE]
>  Cette méthode n'est pas implémentée.  
  
## Voir aussi  
 [IDispError, interface](../../winscript/reference/idisperror-interface.md)