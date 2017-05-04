---
title: "La longueur de tableau doit &#234;tre un entier positif fini | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5029"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# La longueur de tableau doit &#234;tre un entier positif fini
Vous appelez le constructeur **Array** avec un argument qui n'est pas un nombre entier \(les nombres entiers comprennent zéro ainsi que l'ensemble des entiers positifs\).  
  
### Pour corriger cette erreur  
  
-   Utilisez des entiers positifs uniquement lors de la création d'un objet `Array`.  Si vous souhaitez créer un tableau avec un seul élément qui n'est pas un entier, vous devez respecter un processus en deux étapes.  Commencez par créer un tableau à un élément, puis placez la valeur dans le premier élément \(array \[0\]\).  L'exemple de code suivant génère cette erreur.  
  
    ```javascript  
    var piArray = new Array(3.14159);  
    ```  
  
     L'exemple suivant montre comment spécifier correctement un tableau avec un élément numérique unique.  
  
    ```javascript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     Il n'existe aucune limite supérieure quant à la taille d'un tableau autre que la valeur entière maximale \(environ 4 milliards\).  
  
## Voir aussi  
 [Utilisation de tableaux](../../javascript/advanced/using-arrays-javascript.md)