---
title: "IScriptEntry::SetText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ISetEntry::SetText"
ms.assetid: 4605481b-7707-43d1-ab78-a9207d0cf6fe
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::SetText
Définit le texte qui correspond à un bloc de script d' `IScriptEntry` , ou le code source contenu dans un gestionnaire d'événements d' `IScriptScriptlet` .  
  
## Syntaxe  
  
```  
HRESULT SetText(  
   LPCOLESTR          psz  
);  
```  
  
#### Paramètres  
 `psz`  
 \[in\]  Le texte du bloc de script d' `IScriptEntry` , ou le code source du gestionnaire d'événements d' `IScriptScriptlet` .  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
  
## Voir aussi  
 [IScriptEntry, interface](../../winscript/reference/iscriptentry-interface.md)