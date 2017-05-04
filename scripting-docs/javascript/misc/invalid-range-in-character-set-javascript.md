---
title: "Plage non valide dans le jeu de caract&#232;res (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5021"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Plage non valide dans le jeu de caract&#232;res (JavaScript)
Vous avez essayé de créer une expression régulière avec une plage de jeu de caractères non valide.  Les jeux de caractères n'acceptent que les plages de caractères uniques, telles que a\-z ou 0\-9 ; vous ne pouvez pas inclure de classes de caractères, telles que \\w dans un jeu de caractères.  De plus, le premier caractère de la plage doit précéder le second caractère de la plage.  Par exemple :  
  
```javascript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### Pour corriger cette erreur  
  
-   Utilisez seulement des caractères uniques pour composer votre jeu de caractères d'expression régulière, et vérifiez qu'ils sont dans l'ordre approprié.  
  
## Voir aussi  
 [Objet Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/fr-fr/ab0766e1-7037-45ed-aa23-706f58358c0e)