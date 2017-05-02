---
title: "IScriptEntry::SetItemName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetItemName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::SetItemName"
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptEntry::SetItemName
Définit le nom de l'élément qui identifie un objet d' `IScriptEntry` .  
  
## Syntaxe  
  
```  
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### Paramètres  
 `psz`  
 \[in\]  L'adresse d'une mémoire tampon qui contient le nom de l'élément.  Le nom d'élément est utilisé par l'hôte pour identifier l'entrée.  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|La méthode a échoué.|  
  
## Notes  
 Pour les objets d' `IScriptEntry` , cette méthode retourne `S_OK`.  
  
 Pour les objets d' `IScriptScriptlet` \(qui dérivent d' `IScriptEntry`\), cette méthode retourne `E_FAIL`.  Pour les objets d' `IScriptScriptlet` , le nom d'élément est défini par [IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md) et ne peut pas être modifié.  
  
## Voir aussi  
 [IScriptEntry, interface](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)