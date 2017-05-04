---
title: "IScriptEntry::SetBody | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetBody
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::SetBody"
ms.assetid: 719062e4-98e4-4a7b-946d-6e5dbbcc5225
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IScriptEntry::SetBody
Définit le texte situé au corps d'un bloc de script d' `IScriptEntry` ou d'un scriptlet d' `IScriptScriptlet` .  
  
## Syntaxe  
  
```  
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### Paramètres  
 `psz`  
 \[in\]  Pour un bloc de script d' `IScriptEntry` , `psz` est le texte entre les balises de script.  
  
 Pour un bloc de fonction d' `IScriptEntry` , `psz` est le corps de la fonction.  
  
 Pour un objet d' `IScriptScriptlet` \(qui dérive d' `IScriptEntry`\), `psz` est le texte de script du scriptlet.  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
  
## Voir aussi  
 [IScriptEntry, interface](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)