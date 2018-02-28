---
title: '@setInstruction (JavaScript) | Documents Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@set_JavaScriptKeyword'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '@set statement'
- conditional compilation, variables
ms.assetid: 36f15926-3e69-422d-82a2-d186dc088203
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10f74a1d57a61d78897b660812a6fd8078244b6b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="set-statement-javascript"></a>@setInstruction (JavaScript)
Crée des variables utilisées avec les instructions de compilation conditionnelle.  
  
> [!WARNING]
>  La compilation conditionnelle n'est prise en charge ni par le mode standard d'Internet Explorer 11, ni par les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. La compilation conditionnelle est prise en charge par le mode standard d'Internet Explorer 10 et toutes les versions antérieures.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
@set @varname = term   
```  
  
## <a name="parameters"></a>Paramètres  
 *nom de variable*  
 Obligatoire. Nom de variable [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] valide. Doit toujours être précédé d'un caractère « @ ».  
  
 `term`  
 Obligatoire. Aucun ou plusieurs opérateurs unaires suivis d'une constante, d'une variable de compilation conditionnelle ou d'une expression entre parenthèses.  
  
## <a name="remarks"></a>Remarques  
 Les variables numériques et booléennes sont prises en charge pour la compilation conditionnelle. Ce n'est pas le cas des chaînes. Les variables créées à l'aide de `@set` sont généralement utilisées dans des instructions de compilation conditionnelle, même si elles peuvent être employées partout ailleurs dans le code [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
 Voici des exemples de déclarations de variables :  
  
```JavaScript  
  
      @set @myvar1 = 12  
  
@set @myvar2 = (@myvar1 * 20)  
  
@set @myvar3 = @_jscript_version  
```  
  
 Les opérateurs suivants sont pris en charge dans les expressions entre parenthèses :  
  
-   `! ~`  
  
-   `* / %`  
  
-   `+ -`  
  
-   `<< >> >>>`  
  
-   `< <= > >=`  
  
-   `== != === !==`  
  
-   `& ^ |`  
  
-   `&& | |`  
  
 Si une variable est utilisée avant d'être définie, sa valeur est `NaN`. `NaN` peut être vérifié pour l'utilisation de l'instruction `@if` :  
  
```JavaScript  
@if (@newVar != @newVar)  
   ...  
```  
  
 Cela est possible parce que `NaN` est la seule valeur qui n'est pas égale à elle-même.  
  
## <a name="requirements"></a>Spécifications  
 Prise en charge dans toutes les versions d'Internet Explorer, mais pas dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Compilation conditionnelle](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variables de Compilation conditionnelle](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_onInstruction](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if Instruction](../../javascript/reference/at-if-statement-javascript.md)