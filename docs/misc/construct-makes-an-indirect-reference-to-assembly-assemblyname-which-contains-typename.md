---
title: "La construction fait indirectement r&#233;f&#233;rence &#224; l’assembly &#39;&lt;nom_assembly&gt;&#39;, qui contient &#39;&lt;nom_type&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31528"
  - "vbc31528"
helpviewer_keywords: 
  - "BC31528"
ms.assetid: 33459c3f-8615-492e-b6ae-531ed597999e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La construction fait indirectement r&#233;f&#233;rence &#224; l’assembly &#39;&lt;nom_assembly&gt;&#39;, qui contient &#39;&lt;nom_type&gt;&#39;
La construction fait indirectement référence à l’assembly '\<nom\_assembly\>', qui contient \<nom\_type\>. Ajoutez une référence de fichier à \<nom\_fichier\> à votre projet.  
  
 Une expression utilise un type, comme une classe, une structure, une interface, une énumération ou un délégué, mais votre assembly n’a pas de référence de projet à l’assembly qui définit le type.  
  
 **ID d’erreur :** BC31528  
  
### Pour corriger cette erreur  
  
-   Dans vos propriétés de projet, ajoutez une référence au fichier qui contient l’assembly qui définit le type que vous utilisez.  
  
## Voir aussi  
 [NOTINBUILD : Résolution d’une référence quand plusieurs variables portent le même nom](http://msdn.microsoft.com/fr-fr/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [NIB Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)