---
title: "IDispatchEx::GetNextDispID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetNextDispID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetNextDispID (méthode)"
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetNextDispID
Énumère les membres de l'objet.  
  
## Syntaxe  
  
```  
HRESULT GetNextDispID(  
   DWORD grfdex,  
   DISPID id,  
   DISPID *pid  
);  
```  
  
#### Paramètres  
 `grfdex`  
 Détermine ce qui a pour valeur des éléments doit être énuméré.  Cela peut être une combinaison des valeurs suivantes :  
  
|Valeur|Signification|  
|------------|-------------------|  
|fdexEnumDefault|Demande que l'objet énumère les éléments par défaut.  Il permet à l'objet pour énumérer défini des éléments.|  
|fdexEnumAll|Demande que l'objet énumère tous les éléments.  Il permet à l'objet pour énumérer défini des éléments.|  
  
 `id`  
 Identifie le membre actuel.  GetNextDispID extrait l'élément dans l'énumération après celui\-ci.  Utilise GetDispID ou un appel précédent à GetNextDispID d'obtenir cet identificateur.  Utilise la valeur de DISPID\_STARTENUM pour obtenir le premier identificateur du premier élément.  
  
 `pid`  
 Adresse d'une variable de DISPID qui accepte l'identificateur de l'élément dans l'énumération.  
  
 Si un membre est supprimé par `DeleteMemberByName` ou `DeleteMemberByDispID`, doit d' `DISPID` de rester valide pour `GetNextDispID`.  
  
## Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|||  
|-|-|  
|`S_OK`|Succès.|  
|`S_FALSE`|L'énumération est effectuée.|  
  
## Exemple  
  
```  
HRESULT hr;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
  
   // Assign to pdex  
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
   while (hr == NOERROR)  
   {  
      hr = pdex->GetMemberName(dispid, &bstrName);  
      if (!wcscmp(bstrName, OLESTR("Bar")))  
      {  
         SysFreeString(bstrName);  
         return TRUE;  
      }  
      SysFreeString(bstrName);  
      hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);  
   }  
```  
  
## Voir aussi  
 [IDispatchEx, interface](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](#lrfidispatchexgetnextdispid)   
 [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)   
 [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)