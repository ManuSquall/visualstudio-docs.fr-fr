---
title: "IActiveScript::GetScriptDispatch | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptDispatch
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptDispatch"
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::GetScriptDispatch
Récupère l'interface d' `IDispatch` pour les méthodes et les propriétés associées au script en cours de exécution.  
  
## Syntaxe  
  
```  
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### Paramètres  
 `pstrItemName`  
 \[in\]  adresse d'une mémoire tampon qui contient le nom de l'élément pour lequel l'appelant a besoin de l'objet associé d'expédition.  Si ce paramètre est `NULL`, l'objet de dispatch contient comme ses membres toutes les méthodes globales et les propriétés définie par le script.  Via l'interface d' `IDispatch` et l'interface associée d' `ITypeInfo` , l'hôte peut appeler des méthodes de script ou la vue et modifier des variables de script.  
  
 `ppdisp`  
 \[out\]  L'adresse d'une variable qui reçoit un pointeur vers l'objet associé à des méthodes globales et les propriétés du script.  Si le moteur de script ne prend pas en charge ce type d'objet, `NULL` est retourné.  
  
## Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|----------------------|-------------------|  
|`S_OK`|Succès.|  
|`E_INVALIDARG`|Un argument n'était pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L'appel à n'a pas été conçu \(par exemple, le moteur de script n'a pas encore été chargé ou n'a pas été initialisé.\)|  
|`S_FALSE`|Le moteur de script ne prend pas en charge un objet d'expédition ; le paramètre d' `ppdisp` a la valeur NULL.|  
  
## Notes  
 Étant donné que les méthodes et les propriétés peuvent être ajoutées en appelant l'interface d' [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) , l'interface d' `IDispatch` retournée par cette méthode peut dynamiquement en charge de nouvelles méthodes et propriétés.  De même, la méthode d' `IDispatch::GetTypeInfo` doit retourner une nouvelle, seule interface d' `ITypeInfo` lorsque les méthodes et les propriétés sont ajoutées.  La notez, cependant, que les moteurs de langage ne doivent pas modifier l'interface d' `IDispatch` d'une façon qui est incompatible avec toute interface précédente d' `ITypeInfo` retournée.  Cela implique, par exemple, que les dispid ne sera jamais réutilisé.  
  
## Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)