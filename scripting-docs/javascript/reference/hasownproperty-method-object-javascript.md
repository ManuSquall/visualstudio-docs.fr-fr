---
title: "hasOwnProperty, m&#233;thode (Object) (JavaScript) | Microsoft Docs"
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
  - "hasOwnProperty"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "hasOwnProperty (méthode)"
ms.assetid: 3eb69d69-486f-4792-9518-4452aef369ca
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# hasOwnProperty, m&#233;thode (Object) (JavaScript)
Détermine si un objet possède une propriété portant le nom spécifié.  
  
## Syntaxe  
  
```  
  
object.hasOwnProperty(proName)  
```  
  
## Paramètres  
 `object`  
 Requis.  Instance d'un objet.  
  
 `proName`  
 Requis.  Valeur de chaîne du nom d'une propriété.  
  
## Notes  
 La méthode `hasOwnProperty` retourne `true` si `object` possède une propriété portant le nom spécifié ou `false` dans le cas contraire.  Cette méthode ne vérifie pas les propriétés dans la chaîne prototype de l'objet ; la propriété doit être membre de l'objet proprement dit.  
  
 Cette propriété n'est pas prise en charge sur les objets hôtes pour Internet Explorer 8 et version antérieure.  
  
## Exemple  
 Dans l'exemple suivant, tous les objets `String` utilisent une méthode de fractionnement commune.  Le code suivant affiche **false** et **true**.  
  
```javascript  
var s = new String("Sample");  
document.write(s.hasOwnProperty("split"));  
document.write("<br/>");  
document.write(String.prototype.hasOwnProperty("split"));  
  
// Output:  
// false  
// true  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Voir aussi  
 [in, opérateur](../../javascript/reference/in-operator-decrementjavascript.md)