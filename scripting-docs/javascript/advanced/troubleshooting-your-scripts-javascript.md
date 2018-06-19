---
title: Résolution des problèmes liés à vos scripts (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- automative type conversion
- troubleshooting scripts
ms.assetid: 0e0545d9-44e5-4179-befc-99a882c5c672
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7e0193e6dc0996d5e2d0d3df7103c7705d29477
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569279"
---
# <a name="troubleshooting-your-scripts-javascript"></a>Résolution des problèmes liés à vos scripts (JavaScript)
Tout langage de programmation réserve quelques surprises. Par exemple, la valeur `null` en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ne se comporte pas comme la valeur `Null` dans les langages C ou C++.  
  
 Voici quelques problèmes que vous risquez de rencontrer quand vous écrivez des scripts [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="syntax-errors"></a>Erreurs de syntaxe  
 Il est important de faire attention aux détails quand vous écrivez des scripts. Par exemple, les chaînes doivent être placées entre guillemets.  
  
## <a name="order-of-script-interpretation"></a>Ordre d’interprétation du script  
 L’interprétation [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] fait partie du processus d’analyse HTML de votre navigateur web. Si vous placez un script à l’intérieur de la balise \<HEAD> dans un document, il est interprété avant toute partie de la balise \<BODY>. Si vous avez des objets qui sont créés dans la balise \<BODY>, ils n’existent pas au moment où la balise \<HEAD> est en cours d’analyse, et ne peuvent pas être manipulés par le script.  
  
> [!NOTE]
>  Ce comportement est propre à Internet Explorer. ASP et WSH ont des modèles d’exécution différents (comme les autres hôtes).  
  
## <a name="automatic-type-coercion"></a>Forçage de type automatique  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] est un langage faiblement typé avec forçage automatique. Même si les valeurs ayant des types différents ne sont pas égales, les expressions dans l’exemple suivant sont évaluées comme **true**.  
  
```JavaScript  
"100" == 100;  
false == 0;  
```  
  
 Pour vérifier que le type et la valeur sont identiques, utilisez l’opérateur d’égalité stricte (===). Les deux expressions suivantes sont évaluées comme false :  
  
```JavaScript  
"100" === 100;  
false === 0;  
```  
  
## <a name="operator-precedence"></a>Priorité des opérateurs  
 La [priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md) détermine quand une opération est effectuée durant l’évaluation d’une expression. Dans l’exemple suivant, la multiplication est effectuée avant la soustraction, même si la soustraction apparaît en premier dans l’expression.  
  
```JavaScript  
theRadius = aPerimeterPoint - theCenterpoint * theCorrectionFactor;  
```  
  
## <a name="using-forin-loops-with-objects"></a>Utilisation de boucles for...in avec des objets  
 Quand vous itérez au sein des propriétés d’un objet avec une boucle [for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md), vous ne pouvez pas prédire ni contrôler l’ordre dans lequel les champs de l’objet sont assignés à la variable de compteur de boucle. De plus, l’ordre peut être différent dans différentes implémentations du langage.  
  
## <a name="with-keyword"></a>Mot clé with  
 L’instruction [with](../../javascript/reference/with-statement-javascript.md) est pratique pour accéder aux propriétés qui existent déjà dans un objet spécifié, mais vous ne pouvez pas l’utiliser pour ajouter des propriétés à un objet. Pour créer des propriétés dans un objet, vous devez faire référence à l’objet de manière spécifique.  
  
## <a name="this-keyword"></a>Mot clé this  
 Même si vous utilisez le mot clé `this` à l’intérieur de la définition d’un objet pour faire référence à l’objet lui-même, vous ne pouvez pas utiliser `this` ou des mots clés similaires pour faire référence à la fonction en cours d’exécution quand cette fonction n’est pas une définition d’objet. Si la fonction doit être assignée à un objet en tant que méthode, vous pouvez utiliser le mot clé `this` à l’intérieur de la fonction pour faire référence à l’objet.  
  
## <a name="writing-a-script-that-writes-a-script-in-internet-explorer"></a>Écriture d’un script qui écrit un script dans Internet Explorer  
 La balise \</SCRIPT> arrête le script en cours si l’interpréteur la rencontre. Pour afficher « \</SCRIPT> » lui-même, réécrivez-le sous la forme d’au moins deux chaînes, par exemple, «\</SCR » et « IPT> », que vous pouvez ensuite concaténer dans l’instruction qui les écrit.  
  
## <a name="implicit-window-references-in-internet-explorer"></a>Références de fenêtre implicites dans Internet Explorer  
 Étant donné que plusieurs fenêtres peuvent être ouvertes en même temps, toute référence de fenêtre implicite pointe vers la fenêtre active. Pour les autres fenêtres, vous devez utiliser une référence explicite.