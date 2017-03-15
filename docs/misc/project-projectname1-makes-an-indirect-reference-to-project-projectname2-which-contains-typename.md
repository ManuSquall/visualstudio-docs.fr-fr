---
title: "Le projet &#39;&lt;nom_projet1&gt;&#39; &#233;tablit une r&#233;f&#233;rence indirecte au projet &#39;&lt;nom_projet2&gt;&#39;, qui contient &#39;&lt;nom_type&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31532"
  - "bc31532"
helpviewer_keywords: 
  - "BC31532"
ms.assetid: 9ef6574e-b049-4a2e-9b12-fea2dfe06cd1
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le projet &#39;&lt;nom_projet1&gt;&#39; &#233;tablit une r&#233;f&#233;rence indirecte au projet &#39;&lt;nom_projet2&gt;&#39;, qui contient &#39;&lt;nom_type&gt;&#39;
Le projet '\<nom\_projet1\>' établit une référence indirecte au projet '\<nom\_projet2\>', qui contient '\<nom\_type\>'. Ajoutez une référence de projet pour '\<nom\_projet2\>' dans votre projet.  
  
 Le code de votre projet accède à un type défini dans un autre projet, mais votre projet n’a pas de référence directe au projet de définition.  
  
 Le type peut être une classe, une structure, une interface, un module ou une énumération.  
  
 Le projet qui définit le type cité produit un assembly qui contient le type. Si votre projet ne référence pas directement le projet de définition, le compilateur ne peut pas garantir que l’assembly contenant le type se trouve dans la solution et qu’il est possible d’y accéder.  
  
 **ID d’erreur :** BC31532  
  
### Pour corriger cette erreur  
  
-   Déterminez quel projet définit le type cité, puis ajoutez\-lui une référence de projet.  
  
## Voir aussi  
 [NIB : Références aux espaces de noms et aux composants](http://msdn.microsoft.com/fr-fr/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Gestion des références dans un projet](../ide/managing-references-in-a-project.md)   
 [NIB : Gestion des références](http://msdn.microsoft.com/fr-fr/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)