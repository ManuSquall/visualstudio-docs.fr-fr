---
title: "&lt;message&gt; Cette erreur peut aussi r&#233;sulter de la combinaison d’une r&#233;f&#233;rence de fichier &#224; &#39;&lt;nom_fichier1&gt;&#39; dans le projet &#39;&lt;nom_projet1&gt;&#39; avec une r&#233;f&#233;rence de fichier &#224; &#39;&lt;nom_fichier2&gt;&#39; dans le projet &#39;&lt;nom_projet2&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30970"
  - "vbc30970"
helpviewer_keywords: 
  - "BC30970"
ms.assetid: 81cc4f7b-cc16-46cc-9a49-74980300e158
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;message&gt; Cette erreur peut aussi r&#233;sulter de la combinaison d’une r&#233;f&#233;rence de fichier &#224; &#39;&lt;nom_fichier1&gt;&#39; dans le projet &#39;&lt;nom_projet1&gt;&#39; avec une r&#233;f&#233;rence de fichier &#224; &#39;&lt;nom_fichier2&gt;&#39; dans le projet &#39;&lt;nom_projet2&gt;&#39;
\<message\> Cette erreur peut aussi résulter de la combinaison d’une référence de fichier à '\<nom\_chemin\_fichier1\>' dans le projet '\<nom\_projet1\>' avec une référence de fichier à '\<nom\_chemin\_fichier2\>' dans le projet '\<nom\_projet2\>'.  Si les deux assemblys sont identiques, essayez de remplacer ces deux références pour qu’elles se situent au même emplacement.  
  
 Le code de votre projet permet d’accéder à un membre d’un autre projet, mais la configuration de votre solution n’autorise pas le compilateur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] à résoudre la référence.  
  
 Pour accéder à un type défini dans un autre assembly, le compilateur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] doit avoir une référence à cet assembly. Il doit s’agir d’une référence unique et non équivoque qui ne provoque pas de références circulaires parmi des projets.  
  
 **ID d’erreur :** BC30970  
  
### Pour corriger cette erreur  
  
1.  Identifiez le projet qui produit le meilleur assembly pour votre projet à référencer. Pour prendre cette décision, vous pouvez utiliser des critères, tels que la facilité d’accès au fichier et la fréquence des mises à jour.  
  
2.  Dans vos propriétés de projet, ajoutez une référence au fichier contenant l’assembly qui définit le type que vous utilisez.  
  
## Voir aussi  
 [Gestion des références dans un projet](../ide/managing-references-in-a-project.md)   
 [NIB : Référencement d’espaces de noms et de composants](http://msdn.microsoft.com/fr-fr/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [NOT IN BUILD : Résolution d’une référence quand plusieurs variables portent le même nom](http://msdn.microsoft.com/fr-fr/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [NIB Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Dépannage de références rompues](../ide/troubleshooting-broken-references.md)