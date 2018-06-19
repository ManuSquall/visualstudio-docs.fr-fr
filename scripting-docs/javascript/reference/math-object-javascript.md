---
title: Math (objet) (JavaScript) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Math object
ms.assetid: 607b94cb-921c-43cd-b514-fdbc13aeced6
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f16fe4edf6a2a49db15d74abc8ebe6e53f955710
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24642159"
---
# <a name="math-object-javascript"></a>Math, objet (JavaScript)
Objet intrinsèque qui fournit des fonctionnalités et des constantes mathématiques de base.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Math.[{property | method}]  
```  
  
## <a name="parameters"></a>Paramètres  
 *propriété*  
 Obligatoire. Nom de l’une des propriétés de la **mathématiques**. .  
  
 *(méthode)*  
 Obligatoire. Nom de l’une des méthodes de la **mathématiques**. .  
  
## <a name="remarks"></a>Remarques  
 Le **mathématiques** objet ne peut pas être créé à l’aide de la **nouveau** (opérateur) et génère une erreur si vous tentez de le faire. Le moteur de script crée l'objet quand le moteur est chargé. Toutes ses méthodes et propriétés sont disponibles pour votre script en permanence.  
  
## <a name="requirements"></a>Spécifications  
 L'objet `Math` était une nouveauté d'[!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)].  
  
<a name="js56jsobjmathprop"></a>   
## <a name="constants"></a>Constantes  
 Le tableau suivant répertorie les constantes de l'objet `Math`.  
  
|Constante|Description|  
|--------------|-----------------|  
|[Math.E (constante)](../../javascript/reference/math-constants-javascript.md)|Constante mathématique e. Il s'agit du nombre d'Euler, la base du logarithme népérien.|  
|[Math.LN2 (constante)](../../javascript/reference/math-constants-javascript.md)|Logarithme népérien de 2.|  
|[Math.LN10 (constante)](../../javascript/reference/math-constants-javascript.md)|Logarithme népérien de 2.|  
|[Math.LOG2E (constante)](../../javascript/reference/math-constants-javascript.md)|Logarithme de base 2 de e.|  
|[Math.LOG10E (constante)](../../javascript/reference/math-constants-javascript.md)|Logarithme de base 10 de e.|  
|[Constante Math.PI](../../javascript/reference/math-constants-javascript.md)|Pi. Rapport de la circonférence d'un cercle à son diamètre.|  
|[Math.SQRT1_2 (constante)](../../javascript/reference/math-constants-javascript.md)|Racine carrée de 0,5, ou, de façon équivalente, un divisé par la racine carrée de 2.|  
|[Math.SQRT2 (constante)](../../javascript/reference/math-constants-javascript.md)|Racine carrée de 2.|  
  
<a name="js56jsobjmathmeth"></a>   
## <a name="functions"></a>Fonctions  
 Le tableau suivant répertorie les fonctions de l'objet `Math`.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[Fonction Math.abs](../../javascript/reference/math-abs-function-javascript.md)|Retourne la valeur absolue d'un nombre.|  
|[Fonction Math.acos](../../javascript/reference/math-acos-function-javascript.md)|Retourne l'arc cosinus d'un nombre.|  
|[Fonction Math.acosh](../../javascript/reference/math-acosh-function-javascript.md)|Retourne l'arc cosinus hyperbolique (ou cosinus hyperbolique inverse) d'un nombre.|  
|[Fonction Math.asin](../../javascript/reference/math-asin-function-javascript.md)|Retourne l'arc sinus d'un nombre.|  
|[Fonction Math.asinh](../../javascript/reference/math-asinh-function-javascript.md)|Retourne le sinus hyperbolique inverse d'un nombre.|  
|[Fonction Math.atan](../../javascript/reference/math-atan-function-javascript.md)|Retourne l'arc tangente d'un nombre.|  
|[Fonction Math.atan2](../../javascript/reference/math-atan2-function-javascript.md)|Retourne l'angle (en radians) de l'axe X à un point représenté par les coordonnées y et x indiquées.|  
|[Fonction Math.atanh](../../javascript/reference/math-atanh-function-javascript.md)|Retourne la tangente hyperbolique inverse d'un nombre.|  
|[Fonction Math.ceil](../../javascript/reference/math-ceil-function-javascript.md)|Retourne le plus petit entier qui est supérieur ou égal à l'expression numérique fournie.|  
|[Fonction Math.Cos](../../javascript/reference/math-cos-function-javascript.md)|Retourne le cosinus d'un nombre.|  
|[Fonction Math.cosh](../../javascript/reference/math-cosh-function-javascript.md)|Retourne le cosinus hyperbolique d'un nombre.|  
|[Fonction Math.exp](../../javascript/reference/math-exp-function-javascript.md)|Retourne *e* (la base des logarithmes naturels) élevé à une puissance.|  
|[Fonction Math.expm1](../../javascript/reference/math-expm1-function-javascript.md)|Retourne le résultat de la soustraction de 1 de e (la base des logarithmes naturels) élevé à une puissance.|  
|[Fonction Math.floor](../../javascript/reference/math-floor-function-javascript.md)|Retourne le plus grand entier qui est inférieur ou égal à l'expression numérique fournie.|  
|[Fonction Math.hypot](../../javascript/reference/math-hypot-function-javascript.md)|Retourne la racine carrée de la somme des carrés des arguments.|  
|[Fonction Math.imul](../../javascript/reference/math-imul-function-javascript.md)|Retourne le produit de deux nombres traités comme des entiers signés 32 bits.|  
|[Fonction Math.log](../../javascript/reference/math-log-function-javascript.md)|Retourne le logarithme népérien d'un nombre.|  
|[Fonction Math.log1p](../../javascript/reference/math-log1p-function-javascript.md)|Retourne le logarithme naturel de 1 + un nombre.|  
|[Fonction Math.log10](../../javascript/reference/math-log10-function-javascript.md)|Retourne le logarithme de base 10 d'un nombre.|  
|[Fonction Math.log2](../../javascript/reference/math-log2-function-javascript.md)|Retourne le logarithme de base 2 d'un nombre.|  
|[Fonction Math.max](../../javascript/reference/math-max-function-javascript.md)|Retourne la plus grande de deux expressions numériques fournies.|  
|[Fonction Math.min](../../javascript/reference/math-min-function-javascript.md)|Retourne le plus petit de deux nombres fournis.|  
|[Fonction Math.pow](../../javascript/reference/math-pow-function-javascript.md)|Retourne la valeur d'un expression de base élevée à une puissance donnée.|  
|[Fonction Math.random](../../javascript/reference/math-random-function-javascript.md)|Retourne un nombre pseudo-aléatoire entre 0 et 1.|  
|[Fonction Math.round](../../javascript/reference/math-round-function-javascript.md)|Retourne une expression numérique donnée arrondie à l'entier le plus proche.|  
|[Fonction Math.sign](../../javascript/reference/math-sign-function-javascript.md)|Retourne le signe d'un nombre indiquant si celui-ci est positif, négatif ou égal à 0.|  
|[Fonction Math.sin](../../javascript/reference/math-sin-function-javascript.md)|Retourne le sinus d'un nombre.|  
|[Fonction Math.sinh](../../javascript/reference/math-sinh-function-javascript.md)|Retourne le sinus hyperbolique inverse d'un nombre.|  
|[Fonction Math.sqrt](../../javascript/reference/math-sqrt-function-javascript.md)|Retourne la racine carrée d'un nombre.|  
|[Fonction Math.tan](../../javascript/reference/math-tan-function-javascript.md)|Retourne la tangente d'un nombre.|  
|[Fonction Math.tanh](../../javascript/reference/math-tanh-function-javascript.md)|Retourne la tangente hyperbolique d'un nombre.|  
|[Fonction Math.trunc](../../javascript/reference/math-trunc-function-javascript.md)|Retourne la partie entière d'un nombre en retirant la partie décimale.|  
  
## <a name="see-also"></a>Voir aussi  
 [Objets JavaScript](../../javascript/reference/javascript-objects.md)   
 [Objet Number](../../javascript/reference/number-object-javascript.md)