---
title: '@ifInstruction (JavaScript) | Documents Microsoft'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '@if_JavaScriptKeyword'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- elif statement
- conditional statements, if
- if statement, @if
- else statement
- '@if statement'
ms.assetid: ff11b29d-c06a-4276-b11d-db73e2da98ac
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87cfc157ab16b183ccf687fa221393be4ab74757
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634049"
---
# <a name="if-statement-javascript"></a>@ifInstruction (JavaScript)
Exécute un groupe d'instructions soumises à une condition, en fonction de la valeur d'une expression.  
  
> [!WARNING]
>  La compilation conditionnelle n'est prise en charge ni par le mode standard d'Internet Explorer 11, ni par les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. La compilation conditionnelle est prise en charge par le mode standard d'Internet Explorer 10 et toutes les versions antérieures.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      @if (  
   condition1  
)  
   text1  
[@elif (  
   condition2  
)  
   text2]  
[@else  
   text3]  
@end   
```  
  
## <a name="parameters"></a>Paramètres  
 *Condition1, condition2*  
 Facultatif. Expression pouvant être convertie en expression booléenne.  
  
 `text1`  
 Facultatif. Texte à analyser si `condition1` est **true**.  
  
 `text2`  
 Facultatif. Texte à analyser si `condition1` est **false** et `condition2` est **true**.  
  
 `text3`  
 Facultatif. Texte à analyser si les deux `condition1` et `condition2` sont **false**.  
  
## <a name="remarks"></a>Remarques  
 Lorsque vous écrivez une instruction `@if`, vous ne devez pas placer chaque clause sur une ligne distincte. Vous pouvez utiliser plusieurs  **@elif**  clauses. Toutefois, tous les  **@elif**  clauses doivent précéder une  **@else**  clause.  
  
 L'instruction `@if` sert généralement à déterminer le texte à utiliser en sortie parmi plusieurs options.  
  
 Il n'est pas fréquent d'utiliser des variables de compilation conditionnelle dans les scripts écrits pour les programmes de ligne de commande ou les pages ASP ou ASP.NET. Cela est dû au fait que les fonctions des compilateurs peuvent être déterminées à l'aide d'autres méthodes.  
  
 Lorsque vous écrivez un script pour une page Web, ajoutez toujours le code de compilation conditionnelle dans des commentaires. Dès lors, les hôtes qui ne prennent pas en charge la compilation conditionnelle peuvent l'ignorer.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la  **@if...@elif... @else... @end**  instruction.  
  
```JavaScript  
/*@cc_on @*/  
/*@  
    document.write("JavaScript version: " + @_jscript_version + ".");  
    document.write("<br />");  
    @if (@_win32)  
        document.write("Running on a 32-bit version of Windows.");  
    @elif (@_win16)  
        document.write("Running on a 16-bit version of Windows.");  
    @else  
        document.write("Running on a different operating system.");  
    @end  
@*/  
```  
  
## <a name="requirements"></a>Spécifications  
 Prise en charge dans toutes les versions d'Internet Explorer, mais pas dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Compilation conditionnelle](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variables de Compilation conditionnelle](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_onInstruction](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@set Instruction](../../javascript/reference/at-set-statement-javascript.md)