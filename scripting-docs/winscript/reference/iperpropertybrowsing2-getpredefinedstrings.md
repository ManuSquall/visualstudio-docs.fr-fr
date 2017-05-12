---
title: "IPerPropertyBrowsing2::GetPredefinedStrings | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.GetPredefinedStrings
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::GetPredefinedStrings"
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::GetPredefinedStrings
Permet à l'appelant de remplir une zone de liste numérotée de tableau de pointeurs de chaîne qui représentent des valeurs potentielles pour cette propriété.  
  
## Syntaxe  
  
```  
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### Paramètres  
 `dispid`  
 \[in\]  Acheminez l'identificateur de la propriété pour laquelle l'appelant demande la liste de chaîne.  
  
 `pCaStrings`  
 \[out\]  Pointeur vers une structure allouée par l'appelant et numérotée de tableau qui contient le nombre d'éléments et l'adresse d'un tableau au allouée de pointeurs de chaîne.  Si la méthode échoue, aucune mémoire est allouée, et le contenu de la structure est pas défini.  
  
 `pCaCookies`  
 \[out\]  Pointeur vers une structure allouée par l'appelant et numérotée de tableau qui contient le nombre d'éléments et l'adresse d'un tableau au allouée DWORD.  Si la méthode échoue, aucune mémoire est allouée, et le contenu de la structure est pas défini.  
  
## Valeur de retour  
 Retourne `HRESULT`valide, en général `S_OK`.  
  
## Voir aussi  
 [IPerPropertyBrowsing2, interface](../../winscript/reference/iperpropertybrowsing2-interface-1.md)