---
title: "toLocaleLowerCase, m&#233;thode (String) (JavaScript) | Microsoft Docs"
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
  - "toLocaleLowerCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleLowerCase (méthode)"
ms.assetid: add894d3-d14a-4dbc-a9b9-7ad1d3a2e581
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# toLocaleLowerCase, m&#233;thode (String) (JavaScript)
Convertit tous les caractères alphabétiques en minuscules, en fonction des paramètres régionaux définis pour l'environnement hôte.  
  
## Syntaxe  
  
```  
  
stringVar.toLocaleLowerCase( )  
```  
  
## Notes  
 La référence `stringVar` requise est un objet `String` ou un littéral de chaîne.  
  
 La méthode `toLocaleLowerCase` convertit les caractères sous forme de chaîne, en fonction des paramètres régionaux de l'environnement hôte.  Dans la plupart des cas, le résultat est le même que le résultat la méthode `toLowerCase`.  Ils diffèrent si les règles d'une langue sont en contradiction avec les mappages de casse Unicode habituels.  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S'applique à** : [String, objet](../../javascript/reference/string-object-javascript.md)  
  
## Voir aussi  
 [toLocaleUpperCase, méthode \(String\)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [Méthode toLowerCase](../../javascript/reference/tolowercase-method-javascript.md)