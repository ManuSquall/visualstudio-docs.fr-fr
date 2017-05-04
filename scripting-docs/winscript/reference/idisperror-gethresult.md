---
title: "IDispError::GetHresult | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetHresult
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetHresult"
ms.assetid: a14d566e-473f-497b-a2f9-85331433e6c9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetHresult
Récupère le code d'erreur de l'objet d' `IDispError` .  
  
## Syntaxe  
  
```  
HRESULT GetHresult(  
   HRESULT*  phr  
);  
```  
  
#### Paramètres  
 `phr`  
 \[out\]  Spécifie un code d'erreur.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode extrait un code d'erreur de l'objet d' `IDispError` .  
  
> [!NOTE]
>  Cette méthode n'est pas implémentée.  
  
## Voir aussi  
 [IDispError, interface](../../winscript/reference/idisperror-interface.md)