---
title: "toLocaleUpperCase, m&#233;thode (String) (JavaScript) | Microsoft Docs"
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
  - "toLocaleUpperCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleUpperCase (méthode)"
ms.assetid: e927adb6-475e-44b2-91f7-cedda10a39b0
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# toLocaleUpperCase, m&#233;thode (String) (JavaScript)
Retourne une chaîne où tous les caractères alphabétiques ont été convertis en majuscules, en fonction des paramètres régionaux définis pour l'environnement hôte.  
  
## Syntaxe  
  
```  
  
stringVar.toLocaleUpperCase( )  
```  
  
## Notes  
 La référence `stringVar` requise est un objet `String` ou un littéral de chaîne.  
  
 La méthode `toLocaleUpperCase` convertit les caractères sous forme de chaîne, en fonction des paramètres régionaux de l'environnement hôte.  Dans la plupart des cas, le résultat est le même que le résultat la méthode `toUpperCase`.  Ils diffèrent si les règles d'une langue sont en contradiction avec les mappages de casse Unicode habituels.  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S'applique à** : [String, objet](../../javascript/reference/string-object-javascript.md)  
  
## Voir aussi  
 [toLocaleLowerCase, méthode \(String\)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [toUpperCase, méthode \(String\)](../../javascript/reference/touppercase-method-string-javascript.md)