---
title: "IDebugFormatter::GetStringForVarType | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugFormatter.GetStringForVarType
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugFormatter::GetStringForVarType"
ms.assetid: 1c1a0499-ca57-47e0-8367-fdb4c902bca3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugFormatter::GetStringForVarType
Retourne une chaîne qui représente la valeur donnée de VARTYPE.  
  
## Syntaxe  
  
```  
HRESULT GetStringForVarType(  
   VARTYPE    vt,  
   TYPEDESC*  ptdescArrayType,  
   BSTR*      pbstr  
);  
```  
  
#### Paramètres  
 `vt`  
 \[in\]  VARTYPE à représenter en tant que chaîne.  
  
 `ptdescArrayType`  
 \[in\]  Tableau de structures qui décrit les types.  
  
 `pbstr`  
 \[out\]  chaîne représentant `vt`.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 La méthode retourne une chaîne qui représente la valeur donnée de VARTYPE.  
  
## Voir aussi  
 [IDebugFormatter, interface](../../winscript/reference/idebugformatter-interface.md)