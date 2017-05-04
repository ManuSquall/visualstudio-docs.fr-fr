---
title: "Erreurs de syntaxe JavaScript | Microsoft Docs"
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
  - "JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "erreurs (JavaScript)"
  - "erreurs de syntaxe, JavaScript"
ms.assetid: 0343dc19-5f5e-4a4c-83da-630b4fbcb3b6
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Erreurs de syntaxe JavaScript
Des erreurs de syntaxe [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se produisent lorsque la structure de l'une de vos instructions [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] enfreint une ou plusieurs règles syntaxiques.  
  
## Erreurs  
  
|Numéro de l'erreur|Description|  
|------------------------|-----------------|  
|1019|[Présence de 'break' impossible à l'extérieur de la boucle](../../javascript/misc/can-t-have-break-outside-of-loop.md)|  
|1020|[Présence de 'continue' impossible à l'extérieur de la boucle](../../javascript/misc/can-t-have-continue-outside-of-loop.md)|  
|1030|[La compilation conditionnelle est désactivée.](../../javascript/misc/conditional-compilation-is-turned-off.md)|  
|1027|['default' ne peut figurer qu'une seule fois dans une instruction 'switch'.](../../javascript/misc/default-can-only-appear-once-in-a-switch-statement.md)|  
|1005|['\(' attendu](../../javascript/misc/expected-left-parenthesis-javascript.md)|  
|1006|['\)' attendu](../../javascript/misc/expected-right-parenthesis-javascript.md)|  
|1012|['\/' attendu](../../javascript/misc/expected-minus.md)|  
|1003|[':' attendu](../../javascript/misc/expected-colon.md)|  
|1004|[';' attendu](../../javascript/misc/expected-semicolon.md)|  
|1032|['@' attendu](../../javascript/misc/expected-at.md)|  
|1029|['@end' attendu](../../javascript/misc/expected-at-end.md)|  
|1007|['&#93;' attendu](../../javascript/misc/expected-right-square-bracket.md)|  
|1008|['{' attendu](../../javascript/misc/expected-left-curly-brace.md)|  
|1009|['}' attendu](../../javascript/misc/expected-right-curly-brace.md)|  
|1011|['\=' attendu](../../javascript/misc/expected-equal-javascript.md)|  
|1033|['catch' attendu](../../javascript/misc/expected-catch.md)|  
|1031|[Constante attendue](../../javascript/misc/expected-constant.md)|  
|1023|[Chiffre hexadécimal attendu](../../javascript/misc/expected-hexadecimal-digit.md)|  
|1010|[Identificateur attendu](../../javascript/misc/expected-identifier-javascript.md)|  
|1028|[Identificateur, chaîne ou numéro attendu](../../javascript/misc/expected-identifier-string-or-number.md)|  
|1024|['while ' attendu](../../javascript/misc/expected-while.md)|  
|1014|[Caractère non valide](../../javascript/misc/invalid-character-javascript.md)|  
|1026|[Étiquette introuvable](../../javascript/misc/label-not-found.md)|  
|1025|[Étiquette redéfinie](../../javascript/misc/label-redefined.md)|  
|1018|[Instruction 'return' en dehors de la fonction](../../javascript/misc/return-statement-outside-of-function.md)|  
|1002|[Erreur de syntaxe](../../javascript/misc/syntax-error-javascript.md)|  
|1035|[Throw doit être suivi d'une expression sur la même ligne source.](../../javascript/misc/throw-must-be-followed-by-an-expression-on-the-same-source-line.md)|  
|1016|[Commentaire inachevé](../../javascript/misc/unterminated-comment.md)|  
|1015|[Constante de chaîne inachevée](../../javascript/misc/unterminated-string-constant-javascript.md)|  
  
### Erreurs d'hôte de script  
 Les erreurs suivantes sont à proprement parler des erreurs relatives à l'hôte de script, mais vous pouvez parfois les rencontrer.  
  
|Erreur|HRESULT|Description|  
|------------|-------------|-----------------|  
|SCRIPT\_E\_RECORDED|0x86664004|Une erreur a été enregistrée pour être passée entre le moteur et l'hôte de script.  L'hôte doit passer le code de l'erreur à l'appelant.|  
|SCRIPT\_E\_REPORTED|0x80020101|Le moteur de script a signalé une exception non gérée à l'hôte via IActiveScriptSite::OnScriptError.  L'hôte peut ignorer cette erreur.|  
|SCRIPT\_E\_PROPAGATE|0x8002010|Une erreur de script est propagée à l'appelant qui peut être dans un autre thread.  L'hôte doit passer le code de l'erreur à l'appelant.|  
  
## Voir aussi  
 [Erreurs d'exécution JavaScript](../../javascript/reference/javascript-run-time-errors.md)