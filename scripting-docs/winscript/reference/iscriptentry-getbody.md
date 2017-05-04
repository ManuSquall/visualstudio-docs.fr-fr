---
title: "IScriptEntry::GetBody | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetBody
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetBody"
ms.assetid: 419c8c11-a1f8-4b97-ab00-e8af2b2f9bfc
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetBody
Retourne le texte qui correspond au corps d'un bloc de script d' `IScriptEntry` , d'un bloc de fonction, ou d'un scriptlet.  
  
## Syntaxe  
  
```  
HRESULT GetBody(  
   BSTR               *pbstr  
);  
```  
  
#### Paramètres  
 `pbstr`  
 \[out\]  Le texte situé au corps d'un des éléments suivants :  
  
-   Un bloc de script d' `IScriptEntry`  
  
-   Une fonction d' `IScriptEntry` dans un bloc de fonction  
  
-   Un gestionnaire d'événements de scriptlet d' `IScriptEntry`  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
  
## Voir aussi  
 [IScriptEntry, interface](../../winscript/reference/iscriptentry-interface.md)