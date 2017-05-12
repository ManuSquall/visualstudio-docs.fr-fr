---
title: "IScriptEntry::SetName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::SetName"
ms.assetid: dfa33450-87d7-4c8e-bfd8-0cc2d6542a0e
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IScriptEntry::SetName
Pour les entrées qui représentent un objet unique \(tel qu'une fonction\), définit le nom de l'objet.  
  
## Syntaxe  
  
```  
HRESULT SetName(  
   LPCOLESTR          psz  
);  
```  
  
#### Paramètres  
 `psz`  
 \[in\]  le nouveau nom de l'objet d' `IScriptEntry` .  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
  
## Voir aussi  
 [IScriptEntry, interface](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)