---
title: "IActiveScript::AddTypeLib | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.AddTypeLib
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_AddTypeLib"
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::AddTypeLib
Ajoute une bibliothèque de types dans l'espace de noms pour le script.  Cela revient à la directive d' `#include` en C\/C\+\+.  Il permet un jeu d'éléments prédéfinis tels que les définitions de classe, `typedefs`, et les constantes nommées à ajouter à l'environnement d'exécution disponible pour un script.  
  
## Syntaxe  
  
```  
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### Paramètres  
 `guidTypeLib`  
 \[in\]  Le CLSID de la bibliothèque de types à ajouter.  
  
 `dwMaj`  
 \[in\]  Numéro de version principale.  
  
 `dwMin`  
 \[in\]  numéro de version secondaire.  
  
 `dwFlags`  
 \[in\]  balises d'option.  Peut être ce qui suit :  
  
|Valeur|Signification|  
|------------|-------------------|  
|SCRIPTTYPELIB\_ISCONTROL|La bibliothèque de types décrit un contrôle ActiveX utilisé par l'hôte.|  
  
## Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|----------------------|-------------------|  
|`S_OK`|Succès.|  
|`E_INVALIDARG`|Un argument n'était pas valide.|  
|`E_UNEXPECTED`|L'appel à n'a pas été conçu \(par exemple, le moteur de script n'a pas encore été chargé ou n'a pas été initialisé.\)|  
|`TYPE_E_CANTLOADLIBRARY`|La bibliothèque de types spécifiée n'a pas pu être chargé.|  
  
## Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)