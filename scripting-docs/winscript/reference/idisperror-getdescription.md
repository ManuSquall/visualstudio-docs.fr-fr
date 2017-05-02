---
title: "IDispError::GetDescription | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetDescription
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetDescription"
ms.assetid: 04deaea6-0265-4e34-952e-634edba0e923
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetDescription
Retourne une description textuelle de l'erreur.  
  
## Syntaxe  
  
```  
HRESULT GetDescription(  
   BSTR*  pbstrDescription  
);  
```  
  
#### Paramètres  
 `pbstrDescription`  
 \[out\]  chaîne contenant une brève description de l'erreur.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Le texte est retourné dans le langage spécifié par l'ID de paramètres régionaux \(LCID\) qui a été passé à `IDispatchEx::InvokeEx` pour la méthode qui a rencontré une erreur.  
  
> [!NOTE]
>  Cette méthode n'est pas implémentée.  
  
## Voir aussi  
 [IDispError, interface](../../winscript/reference/idisperror-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)