---
title: "@set, instruction (JavaScript) | Microsoft Docs"
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
  - "@set_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "@set (instruction)"
  - "compilation conditionnelle, variables"
ms.assetid: 36f15926-3e69-422d-82a2-d186dc088203
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# @set, instruction (JavaScript)
Crée des variables utilisées avec les instructions de compilation conditionnelle.  
  
> [!WARNING]
>  La compilation conditionnelle n'est prise en charge ni par le mode standard d'Internet Explorer 11, ni par les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  La compilation conditionnelle est prise en charge par le mode standard d'Internet Explorer 10 et toutes les versions antérieures.  
  
## Syntaxe  
  
```  
  
@set @varname = term   
```  
  
## Paramètres  
 *varname*  
 Obligatoire.  Nom de variable [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] valide.  Doit toujours être précédé d'un caractère « @ ».  
  
 `term`  
 Obligatoire.  Aucun ou plusieurs opérateurs unaires suivis d'une constante, d'une variable de compilation conditionnelle ou d'une expression entre parenthèses.  
  
## Notes  
 Les variables numériques et booléennes sont prises en charge pour la compilation conditionnelle.  Ce n'est pas le cas des chaînes.  Les variables créées à l'aide de `@set` sont généralement utilisées dans des instructions de compilation conditionnelle, même si elles peuvent être employées partout ailleurs dans le code [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
 Voici des exemples de déclarations de variables :  
  
```javascript  
  
        @set @myvar1 = 12  
  
@set @myvar2 = (@myvar1 * 20)  
  
@set @myvar3 = @_jscript_version  
```  
  
 Les opérateurs suivants sont pris en charge dans les expressions entre parenthèses :  
  
-   `!  ~`  
  
-   `* / %`  
  
-   `+ -`  
  
-   `<< >> >>>`  
  
-   `< <= > >=`  
  
-   `== != === !==`  
  
-   `& ^ |`  
  
-   `&& | |`  
  
 Si une variable est utilisée avant d'être définie, sa valeur est `NaN`.  `NaN` peut être vérifié pour l'utilisation de l'instruction `@if` :  
  
```javascript  
@if (@newVar != @newVar)  
   ...  
```  
  
 Cela est possible parce que `NaN` est la seule valeur qui n'est pas égale à elle\-même.  
  
## Configuration requise  
 Prise en charge dans toutes les versions d'Internet Explorer, mais pas dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## Voir aussi  
 [Compilation conditionnelle](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variables de compilation conditionnelle](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc\_on, instruction](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if, instruction](../../javascript/reference/at-if-statement-javascript.md)