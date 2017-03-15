---
title: "Une r&#233;f&#233;rence indirecte est &#233;tablie &#224; l’assembly &lt;nom_assembly&gt; version &lt;num&#233;ro_version_ult&#233;rieure&gt;, qui contient &#39;&lt;nom_type&gt;&#39; | Microsoft Docs"
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
  - "vbc32207"
  - "bc32207"
helpviewer_keywords: 
  - "BC32207"
ms.assetid: a3de74b5-bedd-4e36-b379-485e4b3903f7
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une r&#233;f&#233;rence indirecte est &#233;tablie &#224; l’assembly &lt;nom_assembly&gt; version &lt;num&#233;ro_version_ult&#233;rieure&gt;, qui contient &#39;&lt;nom_type&gt;&#39;
Une référence indirecte est établie à l’assembly \<nom\_assembly\> version \<numéro\_version\_ultérieure\>, qui contient '\<nom\_type\>'. Ce projet fait référence à une version antérieure de \<nom\_assembly\> version \<numéro\_version\_antérieure\>. Pour utiliser '\<nom\_type\>', vous devez remplacer la référence à \<nom\_assembly\> version \<numéro\_version\_ultérieure\> ou version ultérieure.  
  
 Une expression fait une référence indirecte à un autre projet, qui fait référence à une version antérieure du même assembly.  
  
 En règle générale, vous devez utiliser uniquement la version la plus récente d’un assembly.  
  
 **ID d’erreur :** BC32207  
  
### Pour corriger cette erreur  
  
1.  Utilisez le nom de type cité pour identifier le projet qui fait également référence au même assembly.  
  
2.  Identifiez la version de l’assembly à laquelle l’autre projet fait référence et modifiez votre projet pour qu’il fasse référence à la même version.  
  
## Voir aussi  
 [Gestion des références dans un projet](../ide/managing-references-in-a-project.md)   
 [NIB Procédure : ajout ou suppression de références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Dépannage de références rompues](../ide/troubleshooting-broken-references.md)