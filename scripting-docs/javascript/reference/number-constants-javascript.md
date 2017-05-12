---
title: "Constantes num&#233;riques (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "constantes (JavaScript), number"
  - "MAX_VALUE (constante) (JavaScript)"
  - "MIN_VALUE (constante) (JavaScript)"
  - "NaN (constante) (JavaScript)"
  - "NEGATIVE_INFINITY (constante) (JavaScript)"
  - "constantes numériques (JavaScript)"
  - "Number.MAX_VALUE (constante) (JavaScript)"
  - "Number.MIN_VALUE (constante) (JavaScript)"
  - "Number.NaN (constante) (JavaScript)"
  - "Number.NEGATIVE_INFINITY (constante) (JavaScript)"
  - "Number.POSITIVE_INFINITY (constante) (JavaScript)"
  - "POSITIVE_INFINITY (constante) (JavaScript)"
ms.assetid: e0701b41-99ae-4916-9ec0-f79bb15386fb
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Constantes num&#233;riques (JavaScript)
Les constantes de nombre suivantes sont les propriétés de l'objet `Number`.  
  
## Constantes d'objet Number  
 Vous n'avez pas besoin de créer un objet `Number` pour accéder à ces constantes.  
  
|Constante|Valeur retournée|  
|---------------|----------------------|  
|`Number.EPSILON`|Le plus petit nombre pouvant être représenté en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Égal à environ 2.2204460492503130808472633361816E\-16.|  
|`Number.MAX_SAFE_INTEGER`|Plus grand nombre pouvant être représenté en toute sécurité en JavaScript.  Égal à 9007199254740991.|  
|`Number.MAX_VALUE`|Le plus grand nombre pouvant être représenté en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Égal à environ 1.79E\+308.|  
|`Number.MIN_SAFE_INTEGER`|Plus petit nombre pouvant être représenté en toute sécurité en JavaScript.  Égal à −9007199254740991.|  
|`Number.MIN_VALUE`|Le nombre le plus près de zéro pouvant être représenté en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Égal à environ 5.00E\-324.|  
|`Number.NaN`|Valeur qui n'est pas un nombre.<br /><br /> Dans les comparaisons d'égalité, `NaN` n'est égal à aucune valeur, y compris lui\-même.  Pour tester si une valeur est équivalente à `NaN`, utilisez la [fonction isNaN](../../javascript/reference/isnan-function-javascript.md).|  
|`Number.NEGATIVE_INFINITY`|Valeur inférieure au plus grand nombre négatif pouvant être représentée en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] affiche les valeurs `NEGATIVE_INFINITY` en tant que `-infinity`.|  
|`Number.POSITIVE_INFINITY`|Valeur supérieure au plus grand nombre pouvant être représenté en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] affiche les valeurs `POSITIVE_INFINITY` en tant que `infinity`.|  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 Pour `Number.EPSILON`, `Number.MAX_SAFE_INTEGER` et `Number.MIN_SAFE_INTEGER` :  
  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **S'applique à** : [Number, objet](../../javascript/reference/number-object-javascript.md)  
  
## Voir aussi  
 [Math, constantes](../../javascript/reference/math-constants-javascript.md)   
 [JavaScript, constantes](../../javascript/reference/javascript-constants.md)   
 [Constante Infinity](../../javascript/reference/infinity-constant-javascript.md)   
 [NaN, constante](../../javascript/reference/nan-constant-javascript.md)   
 [Fonction isNaN](../../javascript/reference/isnan-function-javascript.md)