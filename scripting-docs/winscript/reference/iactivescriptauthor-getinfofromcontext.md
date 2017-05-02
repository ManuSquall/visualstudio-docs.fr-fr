---
title: "IActiveScriptAuthor::GetInfoFromContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetInfoFromContext
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetInfoFromContext"
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthor::GetInfoFromContext
Retourne les informations de type et positions d'ancrage d'un caractère donné dans un bloc de code.  Cela fournit des informations pour le membre Intellisense, des listes globales, et les conseils de paramètre.  
  
## Syntaxe  
  
```  
HRESULT GetInfoFromContext(  
   LPCOLESTR  pszCode,  
   ULONG      cchCode,  
   ULONG      ichCurrentPosition,  
   DWORD      dwListTypesRequested,  
   DWORD      *pdwListTypesProvided,  
   ULONG      *pichListAnchorPosition,  
   ULONG      *pichFuncAnchorPosition,  
   MEMBERID   *pmemid,  
   LONG       *piCurrentParameter,  
   IUnknown   **ppunk  
);  
```  
  
#### Paramètres  
 `pszCode`  
 \[in\]  L'adresse de la chaîne de bloc de code utilisée pour générer les informations résultats.  
  
 `cchCode`  
 \[in\]  la longueur du bloc de code.  
  
 `ichCurrentPosition`  
 \[in\]  La position de l'impression relative au début du bloc.  
  
 `dwListTypesRequested`  
 \[in\]  Les types de listes demandés.  Peut être une combinaison des valeurs suivantes :  
  
|Constante|Valeur|Description|  
|---------------|------------|-----------------|  
|SCRIPT\_CMPL\_NOLIST|0x0000|Aucune liste.|  
|SCRIPT\_CMPL\_MEMBERLIST|0x0001|Liste des membres.|  
|SCRIPT\_CMPL\_ENUMLIST|0x0002|Liste d'enum.|  
|SCRIPT\_CMPL\_PARAMLIST|0x0004|Liste de paramètres de méthode d'appel.|  
|SCRIPT\_CMPL\_GLOBALLIST|0x0008|Liste globale.|  
  
 Le type de SCRIPT\_CMPL\_GLOBALLIST est traité comme un élément par défaut d'achèvement qui peut être combinés à l'aide de l'opérateur OR avec d'autres éléments de saisie semi\-automatique.  Les tests du moteur de création de script d'abord pour remplir informations de type pour d'autres éléments de la liste de saisie semi\-automatique.  En cas de échec, le moteur les exécute pour SCRIPT\_CMPL\_GLOBALLIST.  
  
 `pdwListTypesProvided`  
 \[out\]  Le type de liste fournie.  
  
 `pichListAnchorPosition`  
 \[out\]  Index de début du contexte qui contient la position actuelle.  Index de début est relative au début du bloc.  
  
 Cela est rempli uniquement lorsque `dwListTypesRequested` inclut SCRIPT\_CMPL\_MEMBERLIST, SCRIPT\_CMPL\_ENUMLIST, ou SCRIPT\_CMPL\_GLOBALLIST.  Pour d'autres types demandés de liste, le résultat n'est pas défini.  
  
 `pichFuncAnchorPosition`  
 \[out\]  Index de début de l'appel de fonction qui contient la position actuelle.  Index de début est relative au début du bloc.  
  
 Cela est rempli uniquement lorsque le contexte qui contient la position actuelle est un appel de fonction, et lorsque `dwListTypesRequested` inclut SCRIPT\_CMPL\_PARAMLIST.  Sinon, le résultat n'est pas défini.  
  
 `pmemid`  
 \[out\]  Le MEMBERID de la fonction, comme défini par un type dans le paramètre de sortie d' `IProvideMultipleClassInfo``ppunk` .  
  
 Cela est rempli uniquement lorsque `dwListTypesRequested` inclut SCRIPT\_CMPL\_PARAMLIST.  
  
 `piCurrentParameter`  
 \[out\]  Index du paramètre qui contient la position actuelle.  Si la position actuelle est sur le nom de la fonction, \-1 est retourné.  
  
 La valeur d' `piCurrentParameter` est rempli uniquement lorsque `dwListTypesRequested` inclut SCRIPT\_CMPL\_PARAMLIST.  
  
 `ppunk`  
 Les informations de type, qui sont fournis sous la forme d'un objet d' `IProvideMultipleClassInfo` .  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideMultipleClassInfo>   
 [IActiveScriptAuthor, interface](../../winscript/reference/iactivescriptauthor-interface.md)