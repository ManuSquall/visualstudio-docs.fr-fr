---
title: "IDebugFormatter::GetStringForVariant | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugFormatter.GetStringForVariant
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugFormatter::GetStringForVariant"
ms.assetid: 95189d03-1126-433e-8513-659107b3df16
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugFormatter::GetStringForVariant
Retourne une chaîne qui représente la valeur VARIANT donnée.  
  
## Syntaxe  
  
```  
HRESULT GetStringForVariant(  
   VARIANT*  pvar,  
   ULONG     nRadix,  
   BSTR*     pbstrValue  
);  
```  
  
#### Paramètres  
 `pvar`  
 \[in\]  VARIANT à représenter en tant que chaîne.  
  
 `nRadix`  
 \[in\]  Radis à utiliser pour les valeurs numériques.  
  
 `pbstrValue`  
 \[out\]  chaîne représentant `pvar`.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode retourne une chaîne qui représente la valeur variant donnée.  
  
## Voir aussi  
 [IDebugFormatter, interface](../../winscript/reference/idebugformatter-interface.md)