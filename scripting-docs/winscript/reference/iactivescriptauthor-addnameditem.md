---
title: "IActiveScriptAuthor::AddNamedItem | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.AddNamedItem
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::AddNamedItem"
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# IActiveScriptAuthor::AddNamedItem
Ajoute le nom d'un élément racine à l'espace de noms du moteur de création de script.  *Un élément racine* est un objet qui peut contenir des propriétés et des méthodes, et qui peut également contenir une source d'événement.  
  
## Syntaxe  
  
```  
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### Paramètres  
 `pszName`  
 \[in\]  Le nom de l'élément comme affiché du script.  Le nom doit être unique et persistable.  
  
 `dwFlags`  
 \[in\]  Les balises associées à l'élément nommé.  Peut être une combinaison des valeurs suivantes :  
  
|Constante|Valeur|Description|  
|---------------|------------|-----------------|  
|SCRIPTITEM\_ISVISIBLE|0x00000002|Indique que le nom de l'élément est disponible dans l'espace de noms du script.  Cela permet l'accès aux propriétés, des méthodes, et événements de l'élément.<br /><br /> Par convention, les propriétés de l'élément incluent les membres enfants de l'élément.  Par conséquent, toutes les propriétés de l'objet enfant et méthodes \(et leurs membres enfants, de manière récursive\) sont accessibles.|  
|SCRIPTITEM\_ISSOURCE|0x00000004|Indique les événements de la source d'élément que le script peut avoir des gestionnaires d'événements de script.|  
|SCRIPTITEM\_GLOBALMEMBERS|0x00000008|Indique que l'élément est une collection de propriétés globales et des méthodes associées au script.  Ses membres sont créés en tant que variables globales et méthodes.|  
|SCRIPTITEM\_ISPERSISTENT|0x00000040|Indique que l'élément doit être enregistré si le moteur de création de script est enregistrée.|  
|SCRIPTITEM\_CODEONLY|0x00000200|Indique que l'élément nommé représente un objet code code, et il n'a pas un membre à créer.|  
|SCRIPTITEM\_NOCODE|0x00000400|Indique que l'élément nommé est simplement un nom ajouté, et il n'a rien à créer.|  
  
 `pdisp`  
 \[in\]  `IDispatch` de l'objet d' `NamedItem` qui est utilisé pour collecter des méthodes, des propriétés, ou la source d'événement.  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
  
## Voir aussi  
 [IActiveScriptAuthor, interface](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)