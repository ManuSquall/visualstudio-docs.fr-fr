---
title: "IDispError::GetNext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetNext
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetNext"
ms.assetid: 3e5267f8-ba62-41c3-bd3e-eced2ad85e8e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetNext
Récupère l'objet d' `IDispError` .  
  
## Syntaxe  
  
```  
HRESULT GetNext(  
   IDispError**  ppde  
);  
```  
  
#### Paramètres  
 `ppde`  
 \[out\]  Spécifie l'objet d' `IDispError` .  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode récupère l'objet d' `IDispError` .  Si c'est le dernier objet d' `IDispError` , les cette méthode retourne ANNULENT.  
  
> [!NOTE]
>  Cette méthode n'est pas implémentée.  
  
## Voir aussi  
 [IDispError, interface](../../winscript/reference/idisperror-interface.md)