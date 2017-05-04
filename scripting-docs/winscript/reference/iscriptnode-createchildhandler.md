---
title: "IScriptNode::CreateChildHandler | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.CreateChildHandler
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::CreateChildHandler"
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# IScriptNode::CreateChildHandler
Ajoute un scriptlet instance comme enfant d' `IScriptNode`.  
  
## Syntaxe  
  
```  
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### Paramètres  
 `pszDefaultName`  
 \[in\]  L'adresse du nom par défaut à associer au scriptlet.  
  
 `prgpszNames`  
 \[dans, size\_is \(`cpszNames`\)\] Une liste des identificateurs de nom qualifié complet sur l'hôte.  
  
 `cpszNames`  
 \[in\]  Le nombre d'identificateurs dans le paramètre d' `prgpszNames` .  
  
 `pszEvent`  
 \[in\]  L'adresse de mémoire tampon qui identifie le nom de l'événement associé avec le scriptlet.  
  
 `pszDelimiter`  
 \[in\]  l'adresse du séparateur d'END\-de\-script\-bloc.  Pour analyser, l'hôte utilise généralement un séparateur \(par exemple deux guillemets simples\), pour détecter la fin du bloc de script.  
  
 Le séparateur active le prétraitement par le moteur de création de script.  Par exemple, le moteur peut remplacer un guillemet simple avec deux guillemets simples à utiliser comme délimiteur.  Le moteur détermine comment le séparateur est utilisé.  
  
 Définissez POUR ANNULER si aucun separator n'est utilisé pour identifier la fin du bloc de script.  
  
 `ptiSignature`  
 \[in\]  Les informations de type d'un objet de fonction.  
  
 `iMethodSignature`  
 \[in\]  L'index de la fonction dans le paramètre d' `ITypeInfo``ptiSignature` .  
  
 `isn`  
 \[in\]  L'index de l'enfant dans le parent.  
  
 `dwCookie`  
 \[in\]  une valeur définie par l'application qui est utilisée pour associer l'entrée avec l'objet hôte.  
  
 `ppse`  
 \[out\]  L'adresse d'une variable qui reçoit un pointeur vers l'interface d' `IScriptEntry` de l'instance enfant.  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Un scriptlet spécifie un gestionnaire d'événements.  Cette méthode crée un scriptlet si elle est appelée par un objet d' `IScriptNode` qui représente une page Web.  Cette méthode ne réussit pas si elle est appelée par d'autres interfaces.  
  
## Voir aussi  
 [IScriptNode, interface](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry, interface](../../winscript/reference/iscriptentry-interface.md)