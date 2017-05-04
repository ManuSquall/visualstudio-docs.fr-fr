---
title: "normalize, m&#233;thode (String) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: d50077c1-b5fa-4e7a-9c9d-dc66cfc423ac
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# normalize, m&#233;thode (String) (JavaScript)
Retourne le formulaire de normalisation Unicode d'une chaîne spécifiée.  
  
## Syntaxe  
  
```  
stringObj.normalize([form]);  
```  
  
#### Paramètres  
 `stringObj`  
 Obligatoire.  Objet de chaîne pour le test.  
  
 `form`  
 Facultatif.  Valeur du formulaire de normalisation Unicode.  
  
## Valeur de retour  
 Formulaire de normalisation Unicode d'une chaîne spécifiée.  
  
## Exceptions  
 Si `form` est une valeur non prise en charge, une `RangeError` est levée.  
  
## Notes  
 Si `stringObj` n'est pas une chaîne, il sera converti en chaîne avant que la méthode ne tente de retourner le formulaire de normalisation Unicode de la chaîne.  
  
 `form` doit être une valeur du formulaire de normalisation Unicode, « NFC », « NFD », « NFKC » ou « NFKD », correspondant aux valeurs spécifiées pour [Annexe standard Unicode N° 15](http://www.unicode.org/reports/tr15/).  La valeur par défaut de `form` est « NFC ».  
  
## Exemple  
 Les exemples de code suivants illustrent l'utilisation de la méthode `normalize`.  
  
```javascript  
// ANGSTORM SIGN and LATIN CAPITAL A WITH RING ABOVE is canonically equivalent  
"\u212b".normalize("NFC") === "\u00c5";  
  
// Decomposed, ANGSTOM SIGN is LATIN CAPITAL A followed by COMBINING RING ABOVE  
"\u212b".normalize("NFD") === "\u0041\u030a"  
  
// Normalization Form C will combine the result back into the precombined character  
"\u0041\u030a".normalize("NFC") === "\u00c5"  
  
// LATIN SMALL LIGATURE FI is compatibility equivalent with LATIN SMALL LETTER F followed by  
// LATIN SMALL LETTER I.  
"\ufb01".normalize("NFKD") === "fi";  
  
// Same mapping in NFKC  
"\ufb01".normalize("NFKC") === "fi";  
  
// NFKC will not recombine compatibility characters.  
"fi".normalize("NFKC") === "fi";  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]