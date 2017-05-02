---
title: "toLocaleString, m&#233;thode (Object) (JavaScript) | Microsoft Docs"
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
  - "toLocaleString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleString (méthode)"
ms.assetid: 0901afcb-126b-4ed7-bd6a-2301d50e2326
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toLocaleString, m&#233;thode (Object) (JavaScript)
Retourne une date convertie en chaîne en utilisant les paramètres régionaux.  
  
## Syntaxe  
  
```  
  
dateObj.toLocaleString()   
```  
  
## Notes  
 Le `dateObj` requis est tout objet `Date`.  
  
 La méthode `toLocaleString` retourne un objet `String` qui contient la date écrite dans le format long par défaut spécifié dans les paramètres régionaux en cours.  
  
-   Pour les dates comprises entre 1601 et 1999 après J.\-C., la date est écrite dans le format correspondant aux paramètres régionaux définis par l'utilisateur dans le Panneau de configuration.  
  
-   Pour les dates en dehors de cette plage, c'est le format par défaut de la méthode **toString** qui est utilisé.  
  
 Par exemple, aux États\-Unis, `toLocaleString` retourne « 01\/05\/96 00:00:00 » pour le 5 janvier.  En Europe, elle retourne « 05\/01\/96 00:00:00 » pour la même date, étant donné que la convention européenne place le jour avant le mois.  
  
> [!NOTE]
>  Utilisez `toLocaleString` uniquement pour afficher les résultats à l'utilisateur ; ne vous en servez pas comme base d'un calcul dans un script, étant donné que le résultat retourné varie en fonction de chaque ordinateur.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `toLocaleString`.  
  
```javascript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [Objet Array](../../javascript/reference/array-object-javascript.md)&#124; [Date, objet](../../javascript/reference/date-object-javascript.md)&#124; [Number, objet](../../javascript/reference/number-object-javascript.md)&#124; [Object, objet](../../javascript/reference/object-object-javascript.md)  
  
## Voir aussi  
 [toLocaleDateString, méthode \(Date\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)