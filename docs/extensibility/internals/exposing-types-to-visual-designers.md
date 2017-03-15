---
title: "Exposer des Types pour les concepteurs visuels | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "types (Visual Studio SDK), exposant ainsi à des concepteurs visuels"
  - "concepteurs (Visual Studio SDK), d'exposer des types"
  - "outils personnalisés, exposer des types pour les concepteurs visuels"
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Exposer des Types pour les concepteurs visuels
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] doit avoir accès à la classe et les définitions de type au moment de le design pour afficher un concepteur visuel.  Les classes sont chargées d'un jeu prédéfini d'assemblys qui incluent la dépendance complète définie du projet en cours \(références ainsi que leurs dépendances\).  Il peut également être que les concepteurs visuels accèdent aux classes et aux types définis dans les fichiers générés par les outils personnalisés.  
  
 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] et les systèmes de projet csprcs fournissent la prise en charge pour accéder aux classes et aux types générés à l'aide de les fichiers exécutables portables temporaires \(PE temporaires\).  Tout fichier généré par un outil personnalisé peut être compilé dans un assembly temporaire afin que les types soient chargés à partir de ces assemblys et être exposés aux concepteurs.  La sortie de chaque outil personnalisé est compilée dans un PE temporaire distinct, et la réussite ou l'échec de la compilation temporaire dépend uniquement en fonction si le fichier généré peut être compilé.  Bien qu'un projet peut ne pas être dans son ensemble, le PE temporaires individuel peut encore être disponibles aux concepteurs.  
  
 Le système de projet fournit la prise en charge complète pour le suivi des modifications au fichier de sortie d'un outil personnalisé, à condition que ces modifications soient le résultat d'exécuter l'outil personnalisé.  Chaque fois que l'outil personnalisé est exécuté, un nouveau PE temporaire est généré, et les notifications appropriées sont envoyées aux concepteurs.  
  
> [!NOTE]
>  Étant donné que le fichier exécutable de génération de programme temporaire se produit en arrière\-plan, aucune erreur n'est enregistrée à l'utilisateur si la compilation échoue.  
  
 Les outils personnalisés qui tirent parti de la prise en charge temporaire PE doivent respecter les règles suivantes :  
  
-   `GeneratesDesignTimeSource` doit avoir la valeur 1 dans le Registre.  
  
     Aucune compilation de fichier exécutable du programme n'est effectué sans ce paramètre.  
  
-   Le code généré doit se trouver dans le même langage que le paramètre du projet global.  
  
     Le PE temporaire est compilé indépendamment de ce que l'outil personnalisé qui enregistre en tant qu'extension demandée dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> à condition que `GeneratesDesignTimeSource` ait la valeur 1 dans le Registre.  l'extension n'a pas besoin d'être .vb, .cs, ou .jsl ; elle peut être une extension.  
  
-   Le code généré par l'outil personnalisé doit être valide, et il doit compiler seul seulement l'ensemble de références présentes dans le projet lorsque l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> termine d'exécuter.  
  
     Lorsqu'un PE temporaire est compilé, le seul fichier source fourni au compilateur représente la sortie de l'outil personnalisé.  Par conséquent, un outil personnalisé qui utilise un PE temporaire doit générer les fichiers de sortie qui peuvent être compilés indépendamment des autres fichiers du projet.  
  
## Voir aussi  
 [Introduction to the BuildManager Object](http://msdn.microsoft.com/fr-fr/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [L'implémentation de générateurs de fichier unique](../../extensibility/internals/implementing-single-file-generators.md)   
 [Détermination de l’espace de noms par défaut d’un projet](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Enregistrement de générateurs de fichier unique](../../extensibility/internals/registering-single-file-generators.md)