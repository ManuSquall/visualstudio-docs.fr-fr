---
title: "La construction &#233;tablit une r&#233;f&#233;rence indirecte au projet &#39;&lt;nom_projet&gt;&#39;, qui contient &lt;nom_type&gt;. | Microsoft Docs"
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
  - "vbc31533"
  - "bc31533"
helpviewer_keywords: 
  - "BC31533"
ms.assetid: e3f55f9f-92be-4ecb-bc8f-9e57049a0805
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La construction &#233;tablit une r&#233;f&#233;rence indirecte au projet &#39;&lt;nom_projet&gt;&#39;, qui contient &lt;nom_type&gt;.
La construction établit une référence indirecte au projet '\<nom\_projet\>', qui contient '\<nom\_type\>'. Ajoutez une référence de projet à '\<nom\_projet\>' dans votre projet.  
  
 Une expression ou une instruction accède à un type défini dans un autre projet, mais votre projet n’a pas de référence directe au projet de définition.  
  
 Le type peut être une classe, une structure, une interface, un module ou une énumération.  
  
 Le projet qui définit le type cité produit un assembly qui contient le type. Si votre projet n’établit pas de référence directe au projet de définition, le compilateur ne peut pas garantir que l’assembly contenant le type se trouve dans la solution et qu’il est accessible.  
  
 **ID d’erreur :** BC31533  
  
### Pour corriger cette erreur  
  
-   Identifiez le projet qui définit le type cité, puis ajoutez\-y une référence de projet.  
  
## Voir aussi  
 [NIB : Référencement d’espaces de noms et de composants](http://msdn.microsoft.com/fr-fr/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Gestion des références dans un projet](../ide/managing-references-in-a-project.md)   
 [NIB : Gestion des références](http://msdn.microsoft.com/fr-fr/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)