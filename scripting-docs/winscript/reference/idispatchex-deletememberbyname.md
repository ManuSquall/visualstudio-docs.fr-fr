---
title: "IDispatchEx::DeleteMemberByName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.DeleteMemberByName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DeleteMemberByName (méthode)"
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::DeleteMemberByName
Supprime un membre de nom.  
  
## Syntaxe  
  
```  
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### Paramètres  
 `bstrName`  
 Nom du membre à supprimer.  
  
 `grfdex`  
 Détermine si le nom du membre respecte la casse.  Cela peut être l'une des valeurs suivantes :  
  
|Valeur|Signification|  
|------------|-------------------|  
|fdexNameCaseSensitive|Les demandes ces la recherche de nom effectuées de façon respecte pas la casse.  Peut être ignorée par l'objet qui ne prend pas en charge la recherche ne respecte pas la casse.|  
|fdexNameCaseInsensitive|Les demandes ces la recherche de nom effectuées de façon respecte pas la casse.  Peut être ignorée par l'objet qui ne prend pas en charge la recherche ne respecte pas la casse.|  
  
## Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|||  
|-|-|  
|`S_OK`|Succès.|  
|`S_FALSE`|Le membre existe mais ne peut pas être supprimé.|  
  
## Notes  
 Si le membre est supprimé, le DISPID doit rester valide pour `GetNextDispID`.  
  
 Si un membre portant un nom spécifié est supprimé et ultérieurement un membre portant le même nom est recréé, le DISPID doit être identique.  \(Si les membres qui diffèrent uniquement par leur casse sont « y » est objet dépendant.\)  
  
## Exemple  
  
```  
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## Voir aussi  
 [IDispatchEx, interface](../../winscript/reference/idispatchex-interface.md)