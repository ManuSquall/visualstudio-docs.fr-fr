---
title: "L’assembly &#39;&lt;chemin_fichier1&gt;&#39; r&#233;f&#233;rence l’assembly &#39;&lt;identit&#233;_assembly&gt;&#39;, ce qui cr&#233;e une ambigu&#239;t&#233; entre &#39;&lt;chemin_fichier2&gt;&#39; et &#39;&lt;chemin_fichier3&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42205"
  - "bc42205"
helpviewer_keywords: 
  - "BC42205"
ms.assetid: c36feb10-dded-4073-9553-af278ae5560b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’assembly &#39;&lt;chemin_fichier1&gt;&#39; r&#233;f&#233;rence l’assembly &#39;&lt;identit&#233;_assembly&gt;&#39;, ce qui cr&#233;e une ambigu&#239;t&#233; entre &#39;&lt;chemin_fichier2&gt;&#39; et &#39;&lt;chemin_fichier3&gt;&#39;
L’assembly '\<chemin\_fichier1\>' référence l’assembly '\<identité\_assembly\>', ce qui crée une ambiguïté entre '\<chemin\_fichier2\>' et '\<chemin\_fichier3\>'. '\<chemin\_fichier2\>' sera utilisé.  
  
 Un assembly accède à un type dans un autre assembly auquel il a plusieurs références de fichier.  
  
 Le compilateur ne peut pas garantir que les fichiers aux différents emplacements contiennent la même version du même assembly. Les références de fichier sont donc ambiguës, et le compilateur doit en sélectionner une.  
  
 L’*identité de l’assembly* comprend le nom de l’assembly, sa version, sa clé publique \(le cas échéant\) et sa culture. Ces informations identifient de manière unique l’assembly.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC42205  
  
### Pour corriger cette erreur  
  
1.  Déterminez le fichier qui représente le meilleur choix pour l’assembly. Vous pouvez, en fonction des besoins, utiliser des critères tels que la version la plus récente, l’accessibilité du fichier et la probabilité de mise à jour.  
  
2.  Remplacez toutes les références de fichier à cet assembly pour qu’elles utilisent le même chemin au fichier choisi.  
  
## Voir aussi  
 [NOT IN BUILD : Assemblys](http://msdn.microsoft.com/fr-fr/6c5c7b30-fa78-4f40-b908-120d0743b0e6)   
 [Assemblys dans le Common Language Runtime](../Topic/Assemblies%20in%20the%20Common%20Language%20Runtime.md)   
 [Avantages des assemblys](../Topic/Assembly%20Benefits.md)   
 [Gestion des références dans un projet](../ide/managing-references-in-a-project.md)   
 [NIB : Gestion des références](http://msdn.microsoft.com/fr-fr/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)