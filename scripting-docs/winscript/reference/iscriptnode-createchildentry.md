---
title: "IScriptNode:: CreateChildEntry | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode. CreateChildEntry
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::CreateChildEntry"
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# IScriptNode:: CreateChildEntry
Ajoute une instance enfant d' `IScriptEntry`.  
  
## Syntaxe  
  
```  
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### Paramètres  
 `isn`  
 \[in\]  L'index de l'enfant dans le parent.  
  
 `dwCookie`  
 \[in\]  Une valeur définie par l'application utilisée pour associer l'entrée enfant à l'objet hôte.  
  
 `pszDelimiter`  
 \[in\]  l'adresse du séparateur d'END\-de\-script\-bloc.  Pour analyser, l'hôte utilise généralement un séparateur \(par exemple deux guillemets simples\), pour détecter la fin du bloc de script.  
  
 Le séparateur permet au moteur de création de script de fournir le prétraitement.  Par exemple, le moteur peut remplacer un guillemet simple avec deux guillemets simples à utiliser comme délimiteur.  Le moteur détermine comment le séparateur est utilisé.  
  
 Définissez POUR ANNULER si un séparateur ne marque pas la fin du bloc de script.  
  
 `ppse`  
 \[out\]  L'adresse d'une variable qui reçoit un pointeur vers l'interface d' `IScriptEntry` de l'instance enfant.  
  
 Pour les objets d' `IScriptNode` qui représentent une page Web, retourne la valeur de ce paramètre une instance d' `IScriptEntry` qui spécifie un bloc de script.  
  
 Pour les objets d' `IScriptEntry` qui représentent un bloc de script, retourne la valeur de ce paramètre une instance d' `IScriptEntry` qui spécifie un objet de fonction.  
  
 Pour les objets d' `IScriptEntry` qui représentent un objet de fonction, échec de cette méthode.  
  
 Pour les objets d' `IScriptScriptlet` , cette méthode échoue.  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 l'interface d' `IScriptNode` représente une page Web ou ses éléments.  l'interface d' `IScriptEntry` \(qui est dérivée d' `IScriptNode`\) représente un bloc de script ou un objet de fonction.  L'interface d' `IScriptScriptlet` \(qui est dérivée d' `IScriptEntry`\) représente un gestionnaire d'événements.  
  
## Voir aussi  
 [IScriptNode, interface](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry, interface](../../winscript/reference/iscriptentry-interface.md)