---
title: "IScriptEntry::GetItemName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetItemName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetItemName"
ms.assetid: 8f2562f1-8231-4a39-ad79-074f9ec3d403
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IScriptEntry::GetItemName
Retourne le nom d'élément qui identifie un objet d' `IScriptEntry` .  
  
## Syntaxe  
  
```  
HRESULT GetItemName(  
   BSTR               *pbstr  
);  
```  
  
#### Paramètres  
 `pbstr`  
 \[out\]  L'adresse d'une mémoire tampon qui contient le nom de l'élément.  Le nom d'élément est utilisé par l'hôte pour identifier l'entrée.  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Pour les objets d' `IScriptScriptlet` , affectez le nom d'élément à l'aide de [IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md).  Pour d'autres interfaces, affectez le nom d'élément à l'aide de [IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md).  
  
## Voir aussi  
 [IScriptEntry, interface](../../winscript/reference/iscriptentry-interface.md)