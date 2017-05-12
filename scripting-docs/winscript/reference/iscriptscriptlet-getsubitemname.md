---
title: "IScriptScriptlet::GetSubItemName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptScriptlet.GetSubItemName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptScriptlet::GetSubItemName"
ms.assetid: 9ad963fc-9ce8-4b77-92c1-fb90d6307801
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptScriptlet::GetSubItemName
Retourne le dernier identificateur dans le nom qualifié complet de l'hôte de l'objet d'un scriptlet.  
  
## Syntaxe  
  
```  
HRESULT GetSubItemName(  
   BSTR               *pbstr  
);  
```  
  
#### Paramètres  
 `pbstr`  
 \[out\]  Si le nom qualifié complet du scriptlet de l'hôte possède plusieurs niveau, `pbstr` retourne l'adresse de la mémoire tampon de l'identificateur au deuxième niveau.  
  
 Si le nom qualifié complet du scriptlet de l'hôte possède un niveau, `pbstr` retourne l'adresse de la mémoire tampon de l'identificateur au premier niveau.  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
  
## Voir aussi  
 [IScriptScriptlet, interface](../../winscript/reference/iscriptscriptlet-interface.md)