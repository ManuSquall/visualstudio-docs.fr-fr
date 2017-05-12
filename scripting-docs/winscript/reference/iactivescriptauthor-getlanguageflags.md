---
title: "IActiveScriptAuthor::GetLanguageFlags | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetLanguageFlags
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetLanguageFlags"
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# IActiveScriptAuthor::GetLanguageFlags
Retourne les informations de langage.  
  
## Syntaxe  
  
```  
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### Paramètres  
 `pgrfasa`  
 \[out\]  Les balises qui contiennent des informations de langage.  Peut être une combinaison des valeurs suivantes :  
  
|Constante|Valeur|Description|  
|---------------|------------|-----------------|  
|fasaPreferInternalHandler|0x0001|Le langage préfère la création de gestionnaires d'événements de script par le moteur de création de script au lieu de l'application.|  
|fasaSupportInternalHandler|0x0002|Prend en charge des scripts de gestionnaires d'événements créés par le moteur de création de script.|  
|fasaCaseSensitive|0x0004|Le langage de script respecte la casse.|  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Si le moteur de création de script gère des gestionnaires d'événements, votre application doit appeler `CreateChildHandler` d'un objet d' `IScriptEntry` .  Cela crée un objet d' `IScriptScriptlet` qui correspond au gestionnaire d'événements.  Le moteur ajoute également un gestionnaire d'événements à l'entrée de script.  Le gestionnaire d'événements est une fonction vide qui contient les informations spécifiées de signature.  
  
 Si votre application gère des gestionnaires d'événements, elle doit appeler `CreateChildHandler` d'un objet d' `IScriptNode` qui représente un scriptlet de gestionnaire d'événements.  Cela crée un objet d' `IScriptScriptlet` associé au scriptlet de gestionnaire d'événements.  L'application doit également ajouter une fonction vide en tant que gestionnaire d'événements à un nouveau ou existant objet d' `IScriptEntry` .  
  
## Voir aussi  
 [IActiveScriptAuthor, interface](../../winscript/reference/iactivescriptauthor-interface.md)