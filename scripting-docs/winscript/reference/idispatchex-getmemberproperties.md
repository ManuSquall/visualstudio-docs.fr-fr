---
title: "IDispatchEx::GetMemberProperties | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetMemberProperties
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetMemberProperties (méthode)"
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetMemberProperties
Récupère les propriétés d'un membre.  
  
## Syntaxe  
  
```  
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### Paramètres  
 `id`  
 Identifie le membre.  Utilise `GetDispID` ou `GetNextDispID` d'obtenir l'identificateur de dispatch.  
  
 `grfdexFetch`  
 Détermine les propriétés à récupérer.  Il peut s'agir d'une combinaison de valeurs répertoriées sous `pgrfdex` et\/ou une combinaison des valeurs suivantes :  
  
|Valeur|Signification|  
|------------|-------------------|  
|grfdexPropCanAll|Combine le fdexPropCanGet, le fdexPropCanPut, le fdexPropCanPutRef, le fdexPropCanCall, le fdexPropCanConstruct et les fdexPropCanSourceEvents.|  
|grfdexPropCannotAll|Combine le fdexPropCannotGet, le fdexPropCannotPut, le fdexPropCannotPutRef, le fdexPropCannotCall, le fdexPropCannotConstruct et les fdexPropCannotSourceEvents.|  
|grfdexPropExtraAll|FdexPropNoSideEffects et fdexPropDynamicType de combine.|  
|grfdexPropAll|Combine le grfdexPropCanAll, le grfdexPropCannotAll et le grfdexPropExtraAll.|  
  
 `pgrfdex`  
 Adresse d' `DWORD` qui accepte des propriétés demandées.  Cela peut être une combinaison des valeurs suivantes :  
  
|Valeur|Signification|  
|------------|-------------------|  
|fdexPropCanGet|Le membre peut être obtenu à DISPATCH\_PROPERTYGET.|  
|fdexPropCannotGet|Le membre ne peut pas être obtenu à DISPATCH\_PROPERTYGET.|  
|fdexPropCanPut|Le membre peut être défini à DISPATCH\_PROPERTYPUT.|  
|fdexPropCannotPut|Le membre ne peut pas être défini à DISPATCH\_PROPERTYPUT.|  
|fdexPropCanPutRef|Le membre peut être défini à DISPATCH\_PROPERTYPUTREF.|  
|fdexPropCannotPutRef|Le membre ne peut pas être défini à DISPATCH\_PROPERTYPUTREF.|  
|fdexPropNoSideEffects|Le membre n'a aucun effet secondaire.  Par exemple, un débogueur peut sans risque obtenir\/set\/appel ce membre sans modifier l'état du script en cours de débogage.|  
|fdexPropDynamicType|Le membre est dynamique et peut changer pendant la durée de vie de l'objet.|  
|fdexPropCanCall|Le membre peut être appelée comme une méthode à l'aide de DISPATCH\_METHOD.|  
|fdexPropCannotCall|Le membre ne peut pas être appelé comme méthode à l'aide de DISPATCH\_METHOD.|  
|fdexPropCanConstruct|Le membre peut être appelé comme constructeur de DISPATCH\_CONSTRUCT.|  
|fdexPropCannotConstruct|Le membre ne peut pas être appelé comme constructeur de DISPATCH\_CONSTRUCT.|  
|fdexPropCanSourceEvents|Le membre peut déclencher des événements.|  
|fdexPropCannotSourceEvents|Le membre ne peut pas déclencher d'événements.|  
  
## Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|||  
|-|-|  
|`S_OK`|Succès.|  
|`DISP_E_UNKNOWNNAME`|Le nom n'a pas été connu.|  
  
## Exemple  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
   DWORD dwProps;  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)) &&  
      SUCCEEDED(pdex->GetMemberProperties(dispid, grfdexPropAll, &dwProps)) &&  
         (dwProps & fdexPropCanPut))  
   {  
      // Assign to member  
   }  
```  
  
## Voir aussi  
 [IDispatchEx, interface](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)