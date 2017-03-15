---
title: "An error has been encountered that prevents reference &#39;reference&#39; from loading. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.reference_load_error"
ms.assetid: 0e922611-197b-4607-bc31-03f80bd3e7e1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# An error has been encountered that prevents reference &#39;reference&#39; from loading. &lt;reason&gt;
Une erreur irrécupérable a été détectée lors de la suppression d'une référence du fichier projet.  Les causes de cette erreur sont identifiées dans \<raison\> et peuvent notamment être les suivantes :  
  
-   Un GUID incorrect pour une référence.  Ceci est applicable uniquement aux références COM.  
  
-   Un outil wrapper incorrect.  Actuellement, la propriété d'outil wrapper peut correspondre à tlbimp, aximp ou primary.  Ceci est applicable uniquement aux références COM.  
  
-   Chaîne de référence du projet incorrecte.  Ceci est applicable uniquement aux références entre projets.  
  
 **Pour corriger cette erreur**  
  
-   Pour corriger cette erreur, ajoutez la référence au projet.  
  
     Toute référence pour laquelle ce diagnostic est affiché ne sera pas chargée dans le projet.  
  
## Voir aussi  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/fr-fr/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)