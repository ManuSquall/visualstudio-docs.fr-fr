---
title: "Le fichier &#171;&#160;nomfichier&#160;&#187; ne peut pas &#234;tre copi&#233; dans le r&#233;pertoire d’ex&#233;cution. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cant_copy_to_run_dir"
ms.assetid: 80474e62-7cef-48e9-a7c0-820345d5b591
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Le fichier &#171;&#160;nomfichier&#160;&#187; ne peut pas &#234;tre copi&#233; dans le r&#233;pertoire d’ex&#233;cution. &lt;reason&gt;
Cette erreur s’affiche dans les situations suivantes :  
  
-   Une référence dont la propriété `CopyLocal` \(voir la fenêtre Propriétés quand la référence est sélectionnée dans l’Explorateur de solutions\) a la valeur `true` n’a pas pu être copiée dans le répertoire à partir duquel le projet est exécuté.  
  
-   Une dépendance de référence dont la propriété `CopyLocal` a la valeur `true` n’a pas pu être copiée dans le répertoire à partir duquel le projet est exécuté.  
  
-   Aucun autre fichier devant être copié localement n’a pu être copié dans le répertoire à partir duquel le projet est exécuté.  
  
 En règle générale, la `reason` citée à la fin du message d’erreur signale que le fichier est utilisé par un autre processus. Le fichier est probablement verrouillé par un autre processus dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Il existe peut\-être un problème lié à la génération des projets dans le même répertoire de sortie. Dans ce cas, générez les deux projets dans des répertoires différents. Quand vous générez des projets dans des répertoires différents, le système de projet copie tous les assemblys dépendants dans le répertoire de sortie d’un projet.  
  
 L’ajout de la sortie d’un projet sur lequel vous travaillez en tant qu’élément de boîte à outils entraîne le verrouillage de la référence par les concepteurs gérés.  
  
 Le système de projet n’est pas en mesure de mettre à jour le répertoire de sortie si la sortie est en cours d’exécution.  
  
 **Pour corriger cette erreur**  
  
-   Vérifiez l’espace disque disponible de l’ordinateur  
  
-   Vérifiez si vous atteignez la limite MAX\_PATH imposée par le système de fichiers  
  
     L’erreur n’empêche pas la génération du projet. Toutefois, elle peut l’empêcher de s’exécuter correctement, car cet avertissement indique qu’une copie privée d’un assembly référencé n’a pas pu être correctement mise à jour. Même si le projet peut sembler s’exécuter, vous pouvez obtenir des exceptions de chargement de type ou tout autre comportement inattendu pendant l’exécution de certains chemins de code.  
  
## Voir aussi  
 [NIB : Comment : définir la propriété Copie locale d’une référence](http://msdn.microsoft.com/fr-fr/dfe2ba13-f27f-4356-a481-ea67d5acacbd)