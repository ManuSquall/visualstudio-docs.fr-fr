---
title: "IRemoteDebugApplicationEx:SetLocale | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEx:SetLocale
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEx:SetLocale"
ms.assetid: cd19f725-f4cd-453a-95e1-0bad676451da
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplicationEx:SetLocale
Définit le langage pour la localisation du débogueur.  
  
## Syntaxe  
  
```  
HRESULT SetLocale(  
   DWORD  dwLangID  
);  
```  
  
#### Paramètres  
 `dwLangID`  
 \[in\]  L'ID de langue  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
  
## Voir aussi  
 [ISetNextStatement, interface](../../winscript/reference/isetnextstatement-interface.md)