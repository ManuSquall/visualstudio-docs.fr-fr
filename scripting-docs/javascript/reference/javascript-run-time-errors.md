---
title: "Erreurs d&#39;ex&#233;cution JavaScript | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT-32725"
  - "VS.WebClient.Help.SCRIPT7002"
  - "VS.WebClient.Help.SCRIPT1001"
  - "VS.WebClient.Help.SCRIPT16389"
  - "VS.WebClient.HelpSCRIPT50"
  - "VS.WebClient.HelpSCRIPT70"
  - "VS.WebClient.HelpSCRIPT87"
  - "VS.WebClient.HelpSCRIPT65535"
  - "VS.WebClient.HelpSCRIPT445"
  - "VS.WebClient.HelpSCRIPT600"
  - "VS.WebClient.HelpSCRIPT2343"
  - "VS.WebClient.HelpSCRIPT122"
  - "VS.WebClient.HelpSCRIPT28"
  - "VS.WebClient.HelpSCRIPT16386"
  - "VS.WebClient.HelpSCRIPT7015"
  - "VS.WebClient.HelpSCRIPT3"
  - "VS.WebClient.HelpSCRIPT16388"
  - "VS.WebClient.HelpSCRIPT14"
  - "VS.WebClient.HelpSCRIPT12030"
  - "VS.WebClient.HelpSCRIPT12029"
  - "VS.WebClient.HelpSCRIPT1001"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "erreurs (JavaScript)"
  - "erreurs d'exécution, JavaScript"
ms.assetid: c111469d-8f31-4bde-9d46-16d58775db7d
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Erreurs d&#39;ex&#233;cution JavaScript
Les erreurs d'exécution [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] sont des erreurs qui se produisent quand votre script essaie d'effectuer une action que le système ne peut pas exécuter. Des erreurs d'exécution peuvent apparaître quand des expressions variables sont évaluées ou quand la mémoire est réallouée.  
  
## Erreurs Windows Runtime  
 Si vous utilisez les API Windows Runtime dans votre application du [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], des erreurs JavaScript peuvent s'afficher qui ont été converties de HRESULTs Windows Runtime. Les HRESULT Windows Runtime dans la plage au\-delà de 0x80070000 sont convertis en erreurs JavaScript en convertissant en décimale la valeur hexadécimale des bits faibles. Par exemple, le HRESULT 0x80070032 est converti en valeur décimale 50, et l'erreur JavaScript est SCRIPT50. Le HRESULT 0x80074005 est converti en valeur décimale 16389, et l'erreur JavaScript est SCRIPT16389.  
  
## Erreurs  
  
|Numéro d'erreur|Description|  
|---------------------|-----------------|  
|5|[Accès refusé](../../javascript/misc/access-is-denied.md)|  
|438|[Propriété ou méthode non prise en charge par cet objet](../../javascript/misc/object-doesn-t-support-this-property-or-method.md)|  
|1001|Mémoire insuffisante|  
|5029|[La longueur du tableau doit être un entier positif fini](../../javascript/misc/array-length-must-be-a-finite-positive-integer.md)|  
|5030|[Un entier positif fini doit être assigné la longueur du tableau](../../javascript/misc/array-length-must-be-assigned-a-finite-positive-number.md)|  
|5028|[Objet Array ou Arguments attendu](../../javascript/misc/array-or-arguments-object-expected.md)|  
|5010|[Booléen attendu](../../javascript/misc/boolean-expected.md)|  
|5003|[Impossible d'affecter à un résultat de fonction](../../javascript/misc/cannot-assign-to-a-function-result.md)|  
|5000|[Impossible d'affecter à 'this'](../../javascript/misc/cannot-assign-to-this.md)|  
|5034|[Référence circulaire dans l'argument de valeur non prise en charge](../../javascript/misc/circular-reference-in-value-argument-not-supported.md)|  
|5006|[Objet date attendu](../../javascript/misc/date-object-expected.md)|  
|5015|[Objet d'énumération attendu](../../javascript/misc/enumerator-object-expected.md)|  
|5022|[Exception levée mais non décelée](../../javascript/misc/exception-thrown-and-not-caught.md)|  
|5020|['\)' attendu dans l'expression régulière](../../javascript/misc/expected-right-parenthesis-in-regular-expression-javascript.md)|  
|5019|['&#93;' attendu dans l'expression régulière](../../javascript/misc/expected-right-square-bracket-in-regular-expression-javascript.md)|  
|5023|[La fonction ne possède pas d'objet prototype valide](../../javascript/misc/function-does-not-have-a-valid-prototype-object.md)|  
|5002|[Fonction attendue](../../javascript/misc/function-expected.md)|  
|5008|[Affectation non conforme](../../javascript/misc/illegal-assignment-javascript.md)|  
|5021|[Plage incorrecte dans le jeu de caractères](../../javascript/misc/invalid-range-in-character-set-javascript.md)|  
|5035|[Argument de remplacement incorrect](../../javascript/misc/invalid-replacer-argument.md)|  
|5014|[Objet JavaScript attendu](../../javascript/misc/javascript-object-expected.md)|  
|5001|[Nombre attendu](../../javascript/misc/number-expected.md)|  
|5007|[Objet attendu](../../javascript/misc/object-expected.md)|  
|5012|[Membre d'objet attendu](../../javascript/misc/object-member-expected.md)|  
|5016|[Objet d'expression régulière attendu](../../javascript/misc/regular-expression-object-expected.md)|  
|5005|[Chaîne attendue](../../javascript/misc/string-expected.md)|  
|5017|[Erreur de syntaxe dans l'expression régulière](../../javascript/misc/syntax-error-in-regular-expression-javascript.md)|  
|5026|[Le nombre de fractions est en dehors de la plage](../../javascript/misc/the-number-of-fractional-digits-is-out-of-range.md)|  
|5027|[La précision est en dehors de la plage](../../javascript/misc/the-precision-is-out-of-range.md)|  
|5025|[L'URI à décoder contient un caractère incorrect](../../javascript/misc/the-uri-to-be-decoded-is-not-a-valid-encoding.md)|  
|5024|[L'URI à coder contient un caractère incorrect](../../javascript/misc/the-uri-to-be-encoded-contains-an-invalid-character.md)|  
|5009|[Identificateur non défini](../../javascript/misc/undefined-identifier.md)|  
|5018|[Quantificateur inattendu](../../javascript/misc/unexpected-quantifier-javascript.md)|  
|5013|[VBArray attendu](../../javascript/misc/vbarray-expected.md)|  
  
## Voir aussi  
 [Erreurs de syntaxe JavaScript](../../javascript/reference/javascript-syntax-errors.md)