---
title: "IDispatchEx::DeleteMemberByDispID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.DeleteMemberByDispID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DeleteMemberByDispID (méthode)"
ms.assetid: f61231e5-ba93-4ac3-bde8-d363548356b3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::DeleteMemberByDispID
Supprime un membre par DISPID.  
  
## Syntaxe  
  
```  
HRESULT DeleteMemberByDispID(  
    DISPID id  
);  
```  
  
#### Paramètres  
 `id`  
 Identificateur membre.  Utilise `GetDispID` ou `GetNextDispID` d'obtenir l'identificateur de dispatch.  
  
## Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|||  
|-|-|  
|`S_OK`|Succès.|  
|`S_FALSE`|Le membre existe mais ne peut pas être supprimé.|  
  
## Notes  
 Si le membre est supprimé, le DISPID doit rester valide pour `GetNextDispID`.  
  
 Si un membre portant un nom spécifié est supprimé et ultérieurement un membre portant le même nom est recréé, le DISPID doit être identique.  \(Si les noms des membres qui diffèrent uniquement par leur casse sont « y » est objet dépendant.\)  
  
## Exemple  
  
```  
BSTR bstrName;  
DISPID dispid;  
IDispatchEx *pdex;   
  
// Assign to pdex and bstrName  
if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
    pdex->DeleteMemberByDispID(dispid);  
```  
  
## Voir aussi  
 [IDispatchEx, interface](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)