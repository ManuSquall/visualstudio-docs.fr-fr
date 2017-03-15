---
title: "Comment&#160;: afficher, enregistrer et configurer des fichiers journaux de g&#233;n&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# Comment&#160;: afficher, enregistrer et configurer des fichiers journaux de g&#233;n&#233;ration
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Après avoir généré un projet dans l'IDE de Visual Studio, vous pouvez consulter les informations sur cette génération dans la fenêtre **Sortie** .  Grâce à ces informations, vous pouvez, par exemple, déboguer un échec de génération.  Pour les projets C\+\+, vous pouvez également afficher les mêmes informations dans un fichier .txt qui est créé et inscrit automatiquement.  Pour les projets de code managé, vous pouvez copier et coller les informations de la fenêtre **Sortie** dans un fichier .txt et les enregistrer vous\-même.  Vous pouvez également utiliser l'IDE pour spécifier quels genres d'informations vous souhaitez afficher sur chaque build.  
  
 Si vous générez tout type de projet à l'aide de MSBuild, vous pouvez créer un fichier .txt pour enregistrer des informations sur la génération.  Pour plus d'informations, consultez [Obtention de journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
### Pour afficher le fichier journal de génération pour le projet c\+\+  
  
1.  Dans **Explorateur Windows** ou **Explorateur de fichiers**, ouvrez le fichier suivant : \\…  \\ Visual Studio *Version*projets*Nomprojet*\\\\\\*Nomprojet*\\ debug \\*Nomprojet*.txt  
  
### Pour créer un fichier journal de génération d'un projet de code managé  
  
1.  Dans le menu **Générer**, choisissez **Générer la solution**.  
  
2.  Dans la fenêtre **Sortie**, mettez en surbrillance les informations de la génération, puis copiez\-les dans le presse\-papiers.  
  
3.  Ouvrez un éditeur de texte, tel que le bloc\-notes, coller des informations dans le fichier, puis enregistrez\-le.  
  
### Pour modifier la quantité d'informations incluse dans le journal de génération  
  
1.  Dans la barre de menus, sélectionnez **Outils**, **Options**.  
  
2.  Dans la page **Projets et solutions**, sélectionnez la page **Générer et exécuter** .  
  
3.  Dans la liste **Commentaires de sortie de génération du projet MSBuild**, sélectionnez l'une des valeurs suivantes, puis choisissez le bouton **OK** .  
  
    |Niveau de commentaires|Description|  
    |----------------------------|-----------------|  
    |Silencieux|Affiche un résumé de la build uniquement.|  
    |Minimal|Affiche un résumé de la build et les erreurs, les avertissements, et des messages qui sont catégorisés comme très importants.|  
    |Normal|Affiche un résumé de la build ; erreurs, avertissements, et messages qui sont catégorisés comme très importants ; les étapes principales de la génération.  Vous utiliserez ce niveau de détail le plus souvent.|  
    |Détaillé|Affiche un résumé de la build ; erreurs, avertissements, et messages qui sont catégorisés comme très importants ; toutes les étapes de la génération ; et messages qui sont catégorisés as of l'importance normale.|  
    |Diagnostic|Affiche toutes les données disponibles pour la génération.  Vous pouvez utiliser ce niveau de précision pour faciliter le débogage des problèmes avec des scripts de génération personnalisée et d'autres problèmes de génération.|  
  
     Pour plus d'informations, consultez [Options \(boîte de dialogue\), Projets et solutions, Générer et exécuter](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) et <xref:Microsoft.Build.Framework.LoggerVerbosity>.  
  
    > [!IMPORTANT]
    >  Vous devez régénérer le projet pour que les modifications entrent en vigueur dans la fenêtre **Sortie** \(tous les projets\) et le fichier d' *Nomprojet*.txt \(projets C\+\+ uniquement\).  
  
## Voir aussi  
 [Obtention de journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Génération et nettoyage de solutions et de projets dans Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Génération d'applications dans Visual Studio](../ide/compiling-and-building-in-visual-studio.md)