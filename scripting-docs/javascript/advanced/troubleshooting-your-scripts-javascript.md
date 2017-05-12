---
title: "R&#233;solution des probl&#232;mes li&#233;s &#224; vos scripts (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "conversion de type automatique"
  - "dépannage de scripts"
ms.assetid: 0e0545d9-44e5-4179-befc-99a882c5c672
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# R&#233;solution des probl&#232;mes li&#233;s &#224; vos scripts (JavaScript)
Dans tous les langages de programmation, certains éléments peuvent réserver des surprises.  Par exemple, la valeur `null` dans [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ne se comporte pas de la même manière que la valeur `Null` dans les langages C ou C\+\+.  
  
 Voici quelques problèmes auxquels vous pouvez être confronté lorsque vous écrivez des scripts [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Erreurs de syntaxe  
 Il est important de prêter attention aux détails lorsque vous écrivez des scripts.  Par exemple, les chaînes doivent être placées entre guillemets.  
  
## Ordre d'interprétation du script  
 L'interprétation [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] fait partie du processus d'analyse du code HTML de votre navigateur Web.  Dans un document, si vous placez un script dans la balise \<HEAD\>, il est interprété avant toute partie de la balise \<BODY\>.  Si vous avez des objets créés dans la balise \<BODY\>, ils n'existent pas au moment de l'analyse de \<HEAD\> et ne peuvent pas être manipulés par le script.  
  
> [!NOTE]
>  Ce comportement est spécifique à Internet Explorer.  ASP et WSH ont des modèles d'exécution différents \(comme c'est le cas pour d'autres hôtes\).  
  
## Contrainte de type automatique  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] est un langage faiblement typé avec contrainte automatique.  Bien que les valeurs ayant des types différents ne soient pas égales, les expressions dans l'exemple suivant ont la valeur **True**.  
  
```javascript  
"100" == 100;  
false == 0;  
```  
  
 Pour vérifier si le type et la valeur sont identiques, utilisez l'opérateur d'égalité stricte \(\=\=\=\).  Les deux expressions suivantes renvoient toutes deux False :  
  
```javascript  
"100" === 100;  
false === 0;  
```  
  
## Priorité des opérateurs  
 La [priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md) détermine si une opération est effectuée pendant l'évaluation d'une expression.  Dans l'exemple suivant, la multiplication est effectuée avant la soustraction, même si la soustraction apparaît en premier dans l'expression.  
  
```javascript  
theRadius = aPerimeterPoint - theCenterpoint * theCorrectionFactor;  
```  
  
## Utilisation de boucles for...in avec des objets  
 Lorsque vous itérez au sein des propriétés d'un objet au moyen d'une boucle [for…in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md), vous ne pouvez pas toujours prédire ou contrôler l'ordre dans lequel les champs de l'objet sont assignés à la variable compteur de la boucle.  En outre, l'ordre peut différer en fonction des implémentations du langage.  
  
## Mot clé with  
 L'instruction [with](../../javascript/reference/with-statement-javascript.md) permet d'accéder aux propriétés qui existent déjà dans un objet spécifié, mais ne peut pas servir à ajouter des propriétés à un objet.  Pour créer des propriétés dans un objet, vous devez faire spécifiquement référence à cet objet.  
  
## Mot clé this  
 Même si le mot clé `this` existe à l'intérieur de la définition d'un objet pour faire référence à l'objet proprement dit, vous ne pouvez pas utiliser `this` ou des mots clés similaires pour faire référence à la fonction en cours d'exécution si cette dernière n'est pas une définition d'objet.  Si la fonction doit être assignée à un objet en tant que méthode, vous pouvez utiliser le mot clé `this` à l'intérieur de la fonction pour faire référence à l'objet.  
  
## Élaboration d'un script qui écrit un script dans Internet Explorer  
 La balise \<\/SCRIPT\> termine le script en cours si l'interpréteur la rencontre.  Pour afficher « \<\/SCRIPT\> » à proprement parler, réécrivez\-le en deux chaînes au minimum, par exemple « \<\/SCR » et « IPT\> », que vous pouvez ensuite concaténer dans l'instruction qui les écrit.  
  
## Références de fenêtre implicites dans Internet Explorer  
 Dans la mesure où plusieurs fenêtres peuvent être ouvertes simultanément, toute référence de fenêtre implicite désigne la fenêtre active.  Pour les autres fenêtres, vous devez utiliser une référence explicite.