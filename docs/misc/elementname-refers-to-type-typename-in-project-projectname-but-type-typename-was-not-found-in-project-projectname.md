---
title: "&#39;&lt;nom_&#233;l&#233;ment&gt;&#39; fait r&#233;f&#233;rence au type &#39;&lt;nom_type&gt;&#39; dans le projet &#39;&lt;nom_projet&gt;&#39;, mais le type &#39;&lt;nom_type&gt;&#39; est introuvable dans le projet &#39;&lt;nom_projet&gt;&#39; | Microsoft Docs"
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
  - "vbc30960"
  - "bc30960"
helpviewer_keywords: 
  - "BC30960"
ms.assetid: 4ed4bff5-c670-46f6-8360-7287444d50e5
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_&#233;l&#233;ment&gt;&#39; fait r&#233;f&#233;rence au type &#39;&lt;nom_type&gt;&#39; dans le projet &#39;&lt;nom_projet&gt;&#39;, mais le type &#39;&lt;nom_type&gt;&#39; est introuvable dans le projet &#39;&lt;nom_projet&gt;&#39;
Une expression accède à une classe, une structure, un module ou une interface référencé\(e\) dans un autre projet, mais ce projet ne contient pas le type spécifié.  
  
 Cette erreur se produit quand votre projet fait référence indirectement à un autre projet de la même solution. En règle générale, votre projet fait référence à un assembly qui fait référence à l’autre projet. Si l’assembly accède au type spécifié dans l’autre projet, la référence indirecte au type est établie. Toutefois, si le type n’est pas présent dans l’autre projet, cette erreur est générée.  
  
 **ID d’erreur :** BC30960  
  
### Pour corriger cette erreur  
  
-   Si le type cité n’est plus défini nulle part, supprimez ou remplacez l’instruction qui tente d’y accéder. Vous devrez peut\-être également apporter la même modification dans l’assembly qui fournit la référence indirecte au type cité.  
  
-   Si le type cité est défini quelque part, référencez directement le projet ou l’assembly qui le définit.  
  
## Voir aussi  
 [NIB : Références aux espaces de noms et aux composants](http://msdn.microsoft.com/fr-fr/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Gestion des références dans un projet](../ide/managing-references-in-a-project.md)   
 [NIB : Gestion des références](http://msdn.microsoft.com/fr-fr/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)