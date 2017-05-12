---
title: "substring, m&#233;thode (String) (JavaScript) | Microsoft Docs"
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
  - "substring"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "sous-chaînes"
  - "substring (méthode)"
ms.assetid: 9cf9a005-cbe3-42fd-828b-57a39f54224c
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# substring, m&#233;thode (String) (JavaScript)
Retourne la sous\-chaîne débutant à la position spécifiée dans un objet `String`.  
  
## Syntaxe  
  
```  
  
      strVariable. substring(start [, end])  
"String Literal".substring(start [, end])   
```  
  
## Paramètres  
 `start`  
 Obligatoire.  Entier d'index de base zéro indiquant le début de la sous\-chaîne.  
  
 `end`  
 Facultatif.  Entier d'index de base zéro indiquant la fin de la sous\-chaîne.  La sous\-chaîne inclut tous les caractères jusqu'à celui indiqué par `end` \(non compris\).  
  
 Si le paramètre `end` est omis, les caractères compris entre la position `start` et la fin de la chaîne d'origine sont retournés.  
  
## Notes  
 La méthode `substring` retourne une chaîne contenant la sous\-chaîne entre la position `start` et la position `end` \(non compris\).  
  
 La méthode **substring** utilise la plus petite valeur entre les paramètres `start` et `end` comme position de début de la sous\-chaîne.  Par exemple, strvar.substring\(0, 3**\)** et strvar.substring\(3, 0\) retournent la même sous\-chaîne.  
  
 Si la valeur `start` ou `end` est égale à `NaN` ou est négative, elle est remplacée par zéro.  
  
 La longueur de la sous\-chaîne est égale à la valeur absolue de la différence entre les valeurs `start` et `end`.  Par exemple, la longueur de la sous\-chaîne retournée dans strvar.substring\(0, 3\) et strvar.substring\(3, 0\) est trois \(3\) dans les deux cas.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode **substring**.  
  
```javascript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substring(10, 15);  
document.write(ss);  
  
// Output:  
// brown  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [substr, méthode \(String\)](../../javascript/reference/substr-method-string-javascript.md)