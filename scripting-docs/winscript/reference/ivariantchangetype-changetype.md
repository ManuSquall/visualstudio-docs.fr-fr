---
title: "IVariantChangeType::ChangeType | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IVariantChangeType.ChangeType
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IVariantChangeType::ChangeType"
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IVariantChangeType::ChangeType
Prend une valeur variant et crée un nouveau variant avec un type spécifié.  
  
## Syntaxe  
  
```  
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### Paramètres  
 `pvarDst`  
 \[in, out\]  Un variant pour contenir la valeur représentée par `pvarSrc`, mais avec le type spécifié par `vtNew`.  
  
 `pvarSrc`  
 \[in\]  Une valeur variant à modifier en type.  
  
 `lcid`  
 \[in\]  Le contexte de paramètres régionaux à utiliser en convertissant les arguments vers des chaînes.  
  
 `vtNew`  
 \[in\]  Spécifie le type à `pvarDst` devienne.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Les arguments d' `pvarDst` et d' `pvarSrc` peuvent être identiques, auquel cas la valeur d'origine est remplacée.  Cette méthode passe `pvarDst` à la fonction d' `VariantClear` , et par conséquent `pvarDst` doit être initialisé avec une valeur valide.  
  
## Voir aussi  
 [IVariantChangeType, interface](../../winscript/reference/ivariantchangetype-interface.md)