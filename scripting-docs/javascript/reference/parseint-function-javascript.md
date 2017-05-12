---
title: "parseInt, fonction (JavaScript) | Microsoft Docs"
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
  - "parseInt"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "parseInt (méthode)"
ms.assetid: e86471af-2a0e-4359-83af-f1ac81e51421
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# parseInt, fonction (JavaScript)
Convertit une chaîne en un entier.  
  
## Syntaxe  
  
```  
parseInt(numString, [radix])   
```  
  
## Paramètres  
 `numString`  
 Obligatoire.  Chaîne à convertir en nombre.  
  
 `radix`  
 Facultatif.  Valeur comprise entre 2 et 36 qui spécifie la base du nombre dans `numString`.  Si cet argument n'est pas fourni, les chaînes ayant le préfixe « 0x » sont considérées comme hexadécimales.  Toutes les autres chaînes sont considérées comme des chaînes décimales.  
  
## Notes  
 La fonction `parseInt` retourne une valeur entière égale au nombre contenu dans `numString`.  Si aucun préfixe de l'argument `numString` ne peut être interprété comme un entier, la valeur `NaN` \(Not a Number, pas un nombre\) est retournée.  
  
```javascript  
parseInt("abc");     // Returns NaN.  
parseInt("12abc");   // Returns 12.  
```  
  
 Effectuez un test avec `NaN` au moyen de la fonction `isNaN`.  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [Objet Global](../../javascript/reference/global-object-javascript.md)  
  
> [!NOTE]
>  À partir de [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)], la fonction `parseInt` ne traite pas une chaîne ayant le préfixe « 0 » comme une chaîne octale.  Lorsque la fonction `parseInt` n'est pas utilisée, les chaînes ayant comme préfixe « 0 » peuvent toutefois être interprétées comme des chaînes octales.  Pour plus d'informations sur les entiers octaux, consultez [Types de données](../../javascript/data-types-javascript.md).  
  
## Voir aussi  
 [Fonction isNaN](../../javascript/reference/isnan-function-javascript.md)   
 [Fonction parseFloat](../../javascript/reference/parsefloat-function-javascript.md)   
 [String, objet](../../javascript/reference/string-object-javascript.md)   
 [valueOf, méthode \(Object\)](../../javascript/reference/valueof-method-object-javascript.md)