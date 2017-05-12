---
title: "IDispatchEx::GetDispID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetDispID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetDispID (méthode)"
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetDispID
Mappe un nom de membre unique à son DISPID correspondant, qui peut ensuite être utilisé sur les appels suivants à `IDispatchEx::InvokeEx`.  
  
## Syntaxe  
  
```  
 HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### Paramètres  
 `bstrName`  
 Passé dans le nom à mapper.  
  
 `grfdex`  
 Détermine les options pour obtenir l'identificateur membre.  Cela peut être une combinaison des valeurs suivantes :  
  
|Valeur|Signification|  
|------------|-------------------|  
|fdexNameCaseSensitive|Les demandes ces la recherche de nom effectuées de façon respecte pas la casse.  Peut être ignorée par l'objet qui ne prend pas en charge la recherche ne respecte pas la casse.|  
|fdexNameEnsure|Demandes que le membre est créé s'il n'existe pas.  Le nouveau membre doit être créé avec la valeur `VT_EMPTY`.|  
|fdexNameImplicit|Indique que l'appelant recherche des objets pour un membre d'un nom particulier lorsque l'objet de base n'est pas spécifié explicitement.|  
|fdexNameCaseInsensitive|Les demandes ces la recherche de nom effectuées de façon respecte pas la casse.  Peut être ignorée par l'objet qui ne prend pas en charge la recherche ne respecte pas la casse.|  
  
 `pid`  
 Pointeur vers l'emplacement allouée par l'appelant reçoive le résultat de DISPID.  Si une erreur se produit, `pid` contient DISPID\_UNKNOWN.  
  
## Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|||  
|-|-|  
|`S_OK`|Succès.|  
|`E_OUTOFMEMORY`|Mémoire insuffisante.|  
|`DISP_E_UNKNOWNNAME`|Le nom n'a pas été connu.|  
  
## Notes  
 `GetDispID` peut être utilisé au lieu d' `GetIDsOfNames` pour obtenir le DISPID pour un membre donné.  
  
 Étant donné qu' `IDispatchEx` permet l'ajout et la suppression des membres, l'ensemble de Dispid ne restent pas constante pour la durée de vie d'un objet.  
  
 Le paramètre non utilisé d' `riid` dans `IDispatch::GetIDsOfNames` a été supprimé.  
  
## Exemple  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## Voir aussi  
 [IDispatchEx, interface](../../winscript/reference/idispatchex-interface.md)