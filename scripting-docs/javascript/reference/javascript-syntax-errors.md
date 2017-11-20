---
title: Erreurs de syntaxe JavaScript | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- errors [JavaScript]
- syntax errors, JavaScript
ms.assetid: 0343dc19-5f5e-4a4c-83da-630b4fbcb3b6
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3bc3398d6a90ef308fd2b4b367bc1006ad95f5b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="javascript-syntax-errors"></a>Erreurs de syntaxe JavaScript
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]erreurs de syntaxe se produisent lorsque la structure de l’un de vos [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] instructions enfreint une ou plusieurs des règles syntaxiques.  
  
## <a name="errors"></a>Erreurs  
  
|Numéro d'erreur|Description|  
|------------------|-----------------|  
|1019|[Impossible d’utiliser une instruction 'break' en dehors d’une boucle](../../javascript/misc/can-t-have-break-outside-of-loop.md)|  
|1020|[Impossible d’utiliser une instruction 'continue' en dehors d’une boucle](../../javascript/misc/can-t-have-continue-outside-of-loop.md)|  
|1030|[La compilation conditionnelle est désactivée](../../javascript/misc/conditional-compilation-is-turned-off.md)|  
|1027|['default' ne peut apparaître qu’une fois dans une instruction 'switch'](../../javascript/misc/default-can-only-appear-once-in-a-switch-statement.md)|  
|1005|[Attendu ' ('](../../javascript/misc/expected-left-parenthesis-javascript.md)|  
|1006|[Attendu ')'](../../javascript/misc/expected-right-parenthesis-javascript.md)|  
|1012|[Attendu '/'](../../javascript/misc/expected-minus.md)|  
|1003|[':' attendu](../../javascript/misc/expected-colon.md)|  
|1004|[';' attendu](../../javascript/misc/expected-semicolon.md)|  
|1032|['@' attendu](../../javascript/misc/expected-at.md)|  
|1029|['@end' attendu](../../javascript/misc/expected-at-end.md)|  
|1007|[Attendu ' &#93;'](../../javascript/misc/expected-right-square-bracket.md)|  
|1008|['{' attendu](../../javascript/misc/expected-left-curly-brace.md)|  
|1009|['}' attendu](../../javascript/misc/expected-right-curly-brace.md)|  
|1011|['=' Attendu](../../javascript/misc/expected-equal-javascript.md)|  
|1033|['catch' attendu](../../javascript/misc/expected-catch.md)|  
|1031|[Constante attendue](../../javascript/misc/expected-constant.md)|  
|1023|[Chiffre hexadécimal attendu](../../javascript/misc/expected-hexadecimal-digit.md)|  
|1010|[Identificateur attendu](../../javascript/misc/expected-identifier-javascript.md)|  
|1028|[Identificateur, chaîne ou nombre attendu(e)](../../javascript/misc/expected-identifier-string-or-number.md)|  
|1024|['while' attendu](../../javascript/misc/expected-while.md)|  
|1014|[Caractère non valide](../../javascript/misc/invalid-character-javascript.md)|  
|1026|[Étiquette introuvable](../../javascript/misc/label-not-found.md)|  
|1025|[Étiquette redéfinie](../../javascript/misc/label-redefined.md)|  
|1018|[Instruction 'return' en dehors de la fonction](../../javascript/misc/return-statement-outside-of-function.md)|  
|1002|[Erreur de syntaxe](../../javascript/misc/syntax-error-javascript.md)|  
|1035|['Throw' doit être suivi d’une expression sur la même ligne source](../../javascript/misc/throw-must-be-followed-by-an-expression-on-the-same-source-line.md)|  
|1016|[Commentaire inachevé](../../javascript/misc/unterminated-comment.md)|  
|1015|[Constante de chaîne inachevée](../../javascript/misc/unterminated-string-constant-javascript.md)|  
  
### <a name="script-host-errors"></a>Erreurs d’hôte de script  
 Les erreurs suivantes sont correctement est élevé, les erreurs relatives à l’hôte de script, mais vous pouvez les voir occasionnellement.  
  
|Erreur|HRESULT|Description|  
|-----------|-------------|-----------------|  
|SCRIPT_E_RECORDED|0x86664004|Une erreur a été enregistrée pour être transmises entre l’hôte et le moteur de script. L’ordinateur hôte doit passer le code d’erreur à l’appelant.|  
|SCRIPT_E_REPORTED|0 x 80020101|Moteur de script a signalé une exception non gérée à l’hôte via IActiveScriptSite::OnScriptError. Hôte peut ignorer cette erreur.|  
|SCRIPT_E_PROPAGATE|0x8002010|Une erreur de script est propagée à l’appelant qui peut être dans un autre thread. L’ordinateur hôte doit passer le code d’erreur à l’appelant.|  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs d’exécution JavaScript](../../javascript/reference/javascript-run-time-errors.md)