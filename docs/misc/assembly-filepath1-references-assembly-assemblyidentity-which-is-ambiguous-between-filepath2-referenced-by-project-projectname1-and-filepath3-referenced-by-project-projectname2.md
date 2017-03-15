---
title: "L’assembly &#39;&lt;chemin_fichier1&gt;&#39; r&#233;f&#233;rence l’assembly &#39;&lt;identit&#233;_assembly&gt;&#39;, ce qui cr&#233;e une ambigu&#239;t&#233; entre &#39;&lt;chemin_fichier2&gt;&#39; (r&#233;f&#233;renc&#233; par le projet &#39;&lt;nom_projet1&gt;&#39;) et &#39;&lt;chemin_fichier3&gt;&#39; (r&#233;f&#233;renc&#233; par le projet &#39;&lt;nom_projet2&gt;&#39;) | Microsoft Docs"
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
  - "bc42204"
  - "vbc42204"
helpviewer_keywords: 
  - "BC42204"
ms.assetid: b0c3d2b6-2776-4981-b79e-2e36f03d4123
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’assembly &#39;&lt;chemin_fichier1&gt;&#39; r&#233;f&#233;rence l’assembly &#39;&lt;identit&#233;_assembly&gt;&#39;, ce qui cr&#233;e une ambigu&#239;t&#233; entre &#39;&lt;chemin_fichier2&gt;&#39; (r&#233;f&#233;renc&#233; par le projet &#39;&lt;nom_projet1&gt;&#39;) et &#39;&lt;chemin_fichier3&gt;&#39; (r&#233;f&#233;renc&#233; par le projet &#39;&lt;nom_projet2&gt;&#39;)
L’assembly '\<chemin\_fichier1\>' référence l’assembly '\<identité\_assembly\>', ce qui crée une ambiguïté entre '\<chemin\_fichier2\>' \(référencé par le projet '\<nom\_projet1\>'\) et '\<chemin\_fichier3\>' \(référencé par le projet '\<nom\_projet2\>'\). '\<chemin\_fichier2\>' sera utilisé. Si les deux assemblys sont identiques, remplacez les références au même emplacement.  
  
 Un assembly accède à un type dans un autre assembly auquel il a plusieurs références de fichier.  
  
 Le compilateur ne peut pas garantir que les fichiers aux différents emplacements contiennent la même version du même assembly. Par conséquent, les références de fichier sont ambiguës et le compilateur doit en sélectionner une.  
  
 L’*identité de l’assembly* inclut son nom, sa version, sa clé publique, si elle existe, et sa culture. Ces informations identifient l’assembly de manière unique.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC42204  
  
### Pour corriger cette erreur  
  
1.  Identifiez le fichier qui convient le mieux à l’assembly. Vous pouvez utiliser des critères tels que la version la plus récente, l’accessibilité du fichier et la probabilité de mise à jour selon les besoins.  
  
2.  Modifiez toutes les références de fichier à cet assembly afin qu’elles utilisent le même chemin du fichier sélectionné.  
  
## Voir aussi  
 [NOT IN BUILD : Assemblys](http://msdn.microsoft.com/fr-fr/6c5c7b30-fa78-4f40-b908-120d0743b0e6)   
 [Assemblys dans le Common Language Runtime](../Topic/Assemblies%20in%20the%20Common%20Language%20Runtime.md)   
 [Avantages des assemblys](../Topic/Assembly%20Benefits.md)   
 [Gestion des références dans un projet](../ide/managing-references-in-a-project.md)   
 [NIB : Gestion des références](http://msdn.microsoft.com/fr-fr/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)