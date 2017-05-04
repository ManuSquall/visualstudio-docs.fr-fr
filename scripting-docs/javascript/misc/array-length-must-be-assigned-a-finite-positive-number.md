---
title: "Un nombre positif fini doit &#234;tre assign&#233; &#224; la longueur de tableau | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5030"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Un nombre positif fini doit &#234;tre assign&#233; &#224; la longueur de tableau
Lors de la définition de la propriété **length** d'un objet **Array** existant, la longueur du tableau spécifiée n'était pas un nombre positif, ni un zéro.  Cette erreur se produit lorsque vous assignez une valeur à la propriété **length** d'un objet `Array` qui est négatif ou qui n'est pas un nombre \(`NaN`\).  Notez que [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] convertit automatiquement les nombres fractionnaires en entiers.  
  
### Pour corriger cette erreur  
  
-   Assignez un nombre entier positif à la propriété length.  Il n'existe aucune limite supérieure quant à la taille d'un tableau autre que la valeur entière maximale \(environ 4 milliards\).  L'exemple suivant illustre comment définir correctement la propriété **length** d'un objet **Array** .  
  
    ```javascript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## Voir aussi  
 [Utilisation de tableaux](../../javascript/advanced/using-arrays-javascript.md)