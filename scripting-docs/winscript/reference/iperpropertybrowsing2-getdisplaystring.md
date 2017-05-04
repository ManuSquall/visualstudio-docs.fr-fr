---
title: "IPerPropertyBrowsing2::GetDisplayString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.GetDisplayString
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::GetDisplayString"
ms.assetid: 8f75c6a9-86a9-4e2d-8cb4-74e7b1c0a524
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::GetDisplayString
Obtient une chaîne aux types d'affichage qui ne sont pas fondamentalement affichables le texte retourné sont un nom décrivant la propriété et peuvent être affichés dans l'interface utilisateur de l'appelant.  
  
## Syntaxe  
  
```  
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### Paramètres  
 `dispid`  
 \[in\]  Acheminez l'identificateur de la propriété dont le nom complet est demandé.  
  
 `pBstr`  
 \[out\]  Pointeur vers `BSTR` contenant le nom complet de la propriété identifiée par `dispID`.  
  
## Valeur de retour  
 Retourne `HRESULT`valide, en général `S_OK`.  
  
## Notes  
 La chaîne retournée n'est pas une valeur autorisée de la propriété.  Il s'agit juste d'un affichage de chaîne de la propriété.  
  
## Voir aussi  
 [IPerPropertyBrowsing2, interface](../../winscript/reference/iperpropertybrowsing2-interface-1.md)