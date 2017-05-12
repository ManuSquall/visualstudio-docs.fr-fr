---
title: "IScriptScriptlet::SetSubItemName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptScriptlet.SetSubItemName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptScriptlet::SetSubItemName"
ms.assetid: 619f222f-b4c3-4c7b-9d19-e4e7037343a6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IScriptScriptlet::SetSubItemName
Définit le dernier identificateur dans le nom qualifié complet de l'hôte de l'objet d'un scriptlet.  
  
## Syntaxe  
  
```  
HRESULT SetSubItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### Paramètres  
 `psz`  
 Si le nom qualifié complet du scriptlet de l'hôte possède plusieurs niveau, `psz` est l'adresse de mémoire tampon de l'identificateur au deuxième niveau.  
  
 Si le nom qualifié complet du scriptlet de l'hôte possède un niveau, `psz` est l'adresse de mémoire tampon de l'identificateur au premier niveau.  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
  
## Voir aussi  
 [IScriptScriptlet, interface](../../winscript/reference/iscriptscriptlet-interface.md)