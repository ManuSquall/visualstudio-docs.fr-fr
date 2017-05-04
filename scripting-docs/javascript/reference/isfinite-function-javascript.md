---
title: "isFinite, fonction (JavaScript) | Microsoft Docs"
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
  - "isFinite"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "nombres finis"
  - "isFinite (méthode)"
ms.assetid: ea9287d2-892f-496b-86b7-f9196868d5cf
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# isFinite, fonction (JavaScript)
Détermine si un nombre fourni est terminé.  
  
## Syntaxe  
  
```  
isFinite(number)   
```  
  
## Notes  
 L'argument `number` requis correspond à n'importe quelle valeur numérique.  
  
 La fonction `isFinite` retourne `true` si `number` n'est pas une valeur `NaN`, un nombre négatif infini ou un nombre positif infini.  Dans ces trois cas, la méthode retourne **false**.  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [Objet Global](../../javascript/reference/global-object-javascript.md)  
  
## Voir aussi  
 [Fonction isNaN](../../javascript/reference/isnan-function-javascript.md)