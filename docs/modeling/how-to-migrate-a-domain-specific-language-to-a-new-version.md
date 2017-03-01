---
title: "Comment : migrer un langage spécifique à un domaine vers une nouvelle Version | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a1ae073-443e-45ca-8bc9-9b944362b449
caps.latest.revision: 14
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: 397efd1049ea52b2e7c67a46509d2a088c6fa488
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Comment : migrer un langage spécifique à un domaine vers une nouvelle version
Vous pouvez migrer les projets qui définissent et utilisent le langage spécifique au domaine pour [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] à partir de la version de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] qui a été distribué avec [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)].  
  
 Un outil de migration est fourni dans le cadre de [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)]. L’outil convertit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projets et solutions qui utilisent ou définissent des outils DSL.  
  
 Vous devez exécuter l’outil de migration explicitement : il n’est pas lancé automatiquement lorsque vous ouvrez une solution dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Vous trouverez l’outil et le document des instructions détaillées sur ce chemin d’accès :  
  
 **% Programme Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
## <a name="before-you-migrate-your-dsl-projects"></a>Avant de migrer vos projets DSL  
 L’outil de migration modifie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] les fichiers projet (**.csproj**) et les fichiers solution (**.sln**).  
  
#### <a name="to-prepare-projects-for-migration"></a>Pour préparer des projets pour la migration.  
  
-   Assurez-vous que le **.csproj** et **.sln** fichiers puissent être écrits. S’ils sont sous contrôle de code source, assurez-vous qu’ils sont extraits.  
  
-   Effectuez une copie des dossiers que vous souhaitez migrer.  
  
## <a name="migrating-a-collection-of-projects"></a>Migration d’une Collection de projets  
  
#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Pour migrer des DSL projets et Solutions de Visual Studio 2010  
  
1.  Démarrez l’outil de Migration de DSL.  
  
    -   Double-cliquez sur l’outil dans l’Explorateur Windows (ou Explorateur de fichiers) ou de démarrer l’outil à partir d’une invite de commandes. L’outil est dans cet emplacement :  
  
         **%ProgramFiles%\Microsoft visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
2.  Choisissez un dossier qui contient les solutions et les projets que vous souhaitez convertir.  
  
    -   Entrez le chemin d’accès dans la zone en haut de l’outil, ou cliquez sur **Parcourir**.  
  
     L’outil de migration affiche une arborescence de projets que vous définissez ou utilisez DSL. L’organigramme inclut tous les projets qui utilise le **Microsoft.VisualStudio.Modeling.Sdk** ou **TextTemplating** assemblys.  
  
3.  Examinez l’arborescence de projets et désactivez les projets que vous ne souhaitez pas convertir.  
  
    -   Sélectionnez un projet ou une solution pour afficher la liste des modifications qui fera de l’outil.  
  
        > [!NOTE]
        >  Les cases à cocher qui apparaissent en regard des noms de dossiers n’ont aucun effet. Vous devez développer les dossiers pour inspecter les projets et solutions.  
  
4.  Convertir les projets.  
  
    1.  Cliquez sur **convertir**.  
  
         Avant chaque fichier de projet est converti, une copie de *projet***.csproj** est enregistré en tant que *projet***. vs2008.csproj**  
  
         Une copie de chaque *solution***.sln** est enregistré en tant que *solution***. vs2008.sln**  
  
    2.  Examiner les échecs de conversion sont signalés.  
  
         Échecs sont signalés dans la fenêtre texte. En outre, l’arborescence affiche un indicateur rouge sur chaque nœud qui n’a pas pu convertir. Vous pouvez cliquer sur le nœud pour obtenir plus d’informations sur cet échec.  
  
5.  **Transformer tous les modèles** dans les solutions contenant correctement converti des projets.  
  
    1.  Ouvrez la solution.  
  
    2.  Cliquez sur le **transformer tous les modèles** bouton dans l’en-tête de l’Explorateur de solutions.  
  
        > [!NOTE]
        >  Vous pouvez effectuer cette étape inutile. Pour plus d’informations, consultez [comment automatiser transformer tous les modèles](http://msdn.microsoft.com/en-us/b63cfe20-fe5e-47cc-9506-59b29bca768a).  
  
6.  Mettre à jour votre code personnalisé dans les projets convertis.  
  
    -   Essayez de générer les projets, puis recherchez les défaillances.  
  
    -   Testez votre concepteur.  
  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Voir aussi  
 [Billets de blog connexes](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)


