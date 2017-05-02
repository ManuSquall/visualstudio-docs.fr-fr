---
title: "IDispatchEx::InvokeEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.InvokeEx
apilocation: scrobj.dll
helpviewer_keywords: 
  - "InvokeEx (méthode)"
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDispatchEx::InvokeEx
Permet d'accéder aux propriétés et aux méthodes exposées par un objet d' `IDispatchEx` .  
  
## Syntaxe  
  
```  
HRESULT InvokeEx(  
   DISPID id,  
   LCID lcid,  
   WORD wFlags,  
   DISPARAMS *pdp,  
   VARIANT *pVarRes,   
   EXCEPINFO *pei,   
   IServiceProvider *pspCaller   
);  
```  
  
#### Paramètres  
 `id`  
 Identifie le membre.  Utilise `GetDispID` ou `GetNextDispID` d'obtenir l'identificateur de dispatch.  
  
 `lcid`  
 Contexte des paramètres régionaux dans lequel interpréter les arguments.  `lcid` est passé à `InvokeEx` pour permettre à l'objet pour interpréter ses arguments spécifiques aux paramètres régionaux.  
  
 `wFlags`  
 Les valeurs autorisée pour `wFlags` sont :  
  
 DISPATCH\_PROPERTYGET &#124; DISPATCH\_METHOD &#124; DISPATCH\_PROPERTYPUT &#124; DISPATCH\_PROPERTYPUTREF &#124; DISPATCH\_CONSTRUCT  
  
 Balises décrivant le contexte de l'appel d' `InvokeEx` :  
  
|Valeur|Signification|  
|------------|-------------------|  
|DISPATCH\_METHOD|Le membre est appelé comme méthode.  Si une propriété porte le même nom, cela et la balise de DISPATCH\_PROPERTYGET peut être définie \(défini par `IDispatch`\).|  
|DISPATCH\_PROPERTYGET|Le membre est extrait en tant que propriété ou membre \(définie par `IDispatch`\).|  
|DISPATCH\_PROPERTYPUT|Le membre est modifié comme une propriété ou membre \(définie par `IDispatch`\).|  
|DISPATCH\_PROPERTYPUTREF|Le membre est modifié par une assignation de référence plutôt qu'une assignation des valeurs.  Cette balise est valide uniquement lorsque la propriété accepte une référence à un objet \(défini par `IDispatch`\).|  
|DISPATCH\_CONSTRUCT|Le membre est utilisé comme constructeur.  \(Il s'agit d'une nouvelle valeur définie par `IDispatchEx`\).  Les valeurs autorisée pour `wFlags` sont :<br /><br /> DISPATCH\_PROPERTYGET DISPATCH\_METHOD DISPATCH\_PROPERTYPUT DISPATCH\_PROPERTYPUTREF DISPATCH\_CONSTRUCT|  
  
 `pdp`  
 Pointeur vers une structure qui contient un tableau d'arguments, un tableau d'arguments DISPID pour les arguments nommés et le nombre d'éléments de chaque tableau.  Consultez la documentation d' `IDispatch` pour une description complète de la structure de DISPPARAMS.  
  
 `pVarRes`  
 Pointeur vers l'emplacement où le résultat doit être stocké ou null si l'appelant n'attend pas de résultats.  Cet argument est ignoré si DISPATCH\_PROPERTYPUT ou DISPATCH\_PROPERTYPUTREF est spécifié.  
  
 `pei`  
 Pointeur vers une structure qui contient les informations sur les exceptions.  Cette structure doit être remplie si `DISP_E_EXCEPTION` est retourné.  Peut être null.  Consultez la documentation d' `IDispatch` pour une description complète de la structure d' `EXCEPINFO` .  
  
 `pspCaller`  
 Pointeur vers un objet fournisseur de services fournis par l'appelant, qui permet à l'objet pour obtenir des services de l'appelant.  Peut être null.  
  
 `IDispatchEx::InvokeEx` fournit toutes les fonctionnalités qu' `IDispatch::Invoke` et ajoute des extensions :  
  
|||  
|-|-|  
|DISPATCH\_CONSTRUCT|Indique que l'élément est utilisé comme constructeur.|  
|`pspCaller`|`pspCaller` autorise l'accès d'objet des services fournis par l'appelant.  Les services spécifiques peuvent être gérés par l'appelant elle\-même ou être délégués aux appelants davantage en haut de la chaîne d'appels.  Par exemple, si un moteur de script dans un navigateur effectue un appel d' `InvokeEx` à un objet externe, l'objet peut suivre la chaîne d' `pspCaller` pour obtenir des services du moteur de script ou du navigateur.  \(Notez que la chaîne d'appels n'est pas identique à la chaîne \(également appelé création de la chaîne de conteneur ou une chaîne de site.  La chaîne de création peut être disponible via un autre mécanisme tel qu' `IObjectWithSite`.\)|  
|Pointeur d'`this`|Lorsque DISPATCH\_METHOD est placé dans `wFlags`, il peut y avoir « un paramètre nommé » de «  » cette valeur.  Le DISPID sera DISPID\_THIS et il doit être le premier paramètre nommé.|  
  
 Le paramètre non utilisé d' `riid` dans `IDispatch::Invoke` a été supprimé.  
  
 Le paramètre d' `puArgArr` dans `IDispatch::Invoke` a été supprimé.  
  
 Consultez la documentation d' `IDispatch::Invoke` pour les exemples suivants :  
  
 « Appelant une méthode sans argument »  
  
 « Obtention et définition des propriétés »  
  
 « Passage de paramètres »  
  
 « A des propriétés indexées »  
  
 « En levant des exceptions pendant appelez »  
  
 « Retournant des erreurs »  
  
## Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|||  
|-|-|  
|`S_OK`|Succès.|  
|DISP\_E\_BADPARAMCOUNT|Le nombre d'éléments fournis à DISPPARAMS est différent du nombre d'arguments acceptés par la méthode ou la propriété.|  
|DISP\_E\_BADVARTYPE|L'un des arguments dans `rgvarg` n'est pas un type variant valide.|  
|DISP\_E\_EXCEPTION|L'application doit lever une exception.  Dans ce cas, la structure passée dans `pei` doit être complétée.|  
|DISP\_E\_MEMBERNOTFOUND|Le membre demandé n'existe pas, ou l'appel à `InvokeEx` a tenté de définir la valeur d'une propriété en lecture seule.|  
|DISP\_E\_NONAMEDARGS|Cette implémentation d' `IDispatch` ne prend pas d'arguments nommés.|  
|DISP\_E\_OVERFLOW|L'un des arguments dans `rgvarg` n'a pas pu être converti en type spécifié.|  
|DISP\_E\_PARAMNOTFOUND|Un Dispid du paramètre ne correspond pas à un paramètre dans la méthode.|  
|DISP\_E\_TYPEMISMATCH|Un ou plusieurs arguments n'ont pas pu être convertis.|  
|DISP\_E\_UNKNOWNLCID|Le membre appelé interprète les arguments de chaîne en fonction de le LCID, et LCID n'est pas reconnu.  Si le LCID n'est pas nécessaire pour interpréter les arguments, cette erreur ne doit pas être retournée.|  
|DISP\_E\_PARAMNOTOPTIONAL|Un paramètre obligatoire a été omis.|  
  
## Exemple  
  
```  
VARIANT var;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
   DISPPARAMS dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
   {  
      pdex->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
   }  
```  
  
## Voir aussi  
 [IDispatchEx, interface](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)