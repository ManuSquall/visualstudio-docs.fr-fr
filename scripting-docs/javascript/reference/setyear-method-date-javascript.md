---
title: "setYear, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "setYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "setYear (méthode)"
  - "Year (méthode)"
ms.assetid: 36431050-e0ec-45ee-830d-0d7c20e207ea
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# setYear, m&#233;thode (Date) (JavaScript)
Définit l'année représentée dans l'objet `Date`.  
  
## Syntaxe  
  
```  
  
dateObj.setYear(numYear)   
```  
  
## Paramètres  
 `dateObj`  
 Obligatoire.  Tout objet `Date`.  
  
 `numYear`  
 Obligatoire.  Pour les années 1900 à 1999, il s'agit d'une valeur numérique égale à l'année moins 1900.  Pour les dates situées hors de cette plage, il s'agit d'une valeur numérique à 4 chiffres.  
  
## Notes  
 Cette méthode n'est plus utilisée qu'à des fins de compatibilité descendante.  Employez plutôt la méthode `setFullYear`.  
  
 Pour attribuer la valeur 1997 à l'année d'un objet `Date`, appelez la méthode **setYear\(97\)**.  Pour attribuer la valeur 2010 à l'année, appelez la méthode **setYear\(2010\)**.  Enfin, pour définir une année comprise dans la plage 0\-99, employez la méthode `setFullYear`.  
  
> [!NOTE]
>  Dans la version 1.0 de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], la méthode `setYear` utilise une valeur correspondant au résultat de l'addition de 1900 et de la valeur de l'année spécifiée par l'argument `numYear`, quelle que soit la valeur de l'année.  Par exemple, pour définir l'année 1899, attribuez la valeur \-1 à `numYear` ; pour définir l'année 2000, attribuez la valeur 100 à `numYear`.  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getFullYear, méthode \(Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear, méthode \(Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [getYear, méthode \(Date\)](../../javascript/reference/getyear-method-date-javascript.md)   
 [setFullYear, méthode \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear, méthode \(Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)