---
title: 'Comment : migrer un langage spécifique à un domaine vers une nouvelle version'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: ab671cfffdf43d9b69ecda7f06c27a0e8df6bf70
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43775911"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Comment : migrer un langage spécifique à un domaine vers une nouvelle version
Vous pouvez migrer des projets qui définissent et utilisent le langage spécifique à un domaine à [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] à partir de la version de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] qui a été distribué avec [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)].

 Un outil de migration est fourni dans le cadre de [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)]. L’outil convertit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projets et solutions qui utilisent ou définissent des outils DSL.

 Vous devez exécuter l’outil de migration de manière explicite : il n’est pas lancée automatiquement lorsque vous ouvrez une solution dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Vous trouverez l’outil et le document des instructions détaillées sur ce chemin d’accès :

 **% Programme Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>Avant de migrer vos projets DSL
 L’outil de migration modifie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fichiers projet (**.csproj**) et les fichiers solution (**.sln**).

#### <a name="to-prepare-projects-for-migration"></a>Pour préparer des projets pour la migration.

-   Assurez-vous que le **.csproj** et **.sln** fichiers peuvent être écrits. S’ils sont sous contrôle de code source, assurez-vous qu’ils sont extraits.

-   Effectuez une copie des dossiers que vous voulez migrer.

## <a name="migrating-a-collection-of-projects"></a>Migration d’une Collection de projets

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Pour migrer des Solutions et projets DSL pour Visual Studio 2010

1.  Démarrez l’outil de Migration de DSL.

    -   Double-cliquez sur l’outil dans l’Explorateur Windows (ou Explorateur de fichiers) ou de démarrer l’outil à partir d’une invite de commandes. L’outil se trouve dans cet emplacement :

         **%ProgramFiles%\Microsoft visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2.  Choisissez un dossier qui contient les solutions et projets que vous souhaitez convertir.

    -   Entrez le chemin d’accès dans la zone située en haut de l’outil, ou cliquez sur **Parcourir**.

     L’outil de migration affiche une arborescence de projets qui définissent ou utiliser DSL. L’organigramme inclut chaque projet qui utilise le **Microsoft.VisualStudio.Modeling.Sdk** ou **TextTemplating** assemblys.

3.  Passez en revue l’arborescence de projets et décochez les projets que vous ne souhaitez pas convertir.

    -   Sélectionnez un projet ou une solution pour afficher la liste des modifications pour rend l’outil.

        > [!NOTE]
        >  Les cases à cocher qui apparaissent en regard des noms de dossier n’ont aucun effet. Vous devez développer les dossiers pour inspecter les projets et solutions.

4.  Convertir les projets.

    1.  Cliquez sur **convertir**.

         Avant de chaque fichier de projet est converti, une copie de _projet_**.csproj** est enregistré en tant que _projet_**. vs2008.csproj**

         Une copie de chaque _solution_**.sln** est enregistré en tant que _solution_**. vs2008.sln**

    2.  Examiner les échecs de conversion sont signalés.

         Échecs sont signalés dans la fenêtre texte. En outre, l’arborescence affiche un indicateur rouge sur chaque nœud qui n’a pas pu convertir. Vous pouvez cliquer sur le nœud pour obtenir plus d’informations sur cet échec.

5.  **Transformer tous les modèles** dans les solutions contenant correctement converti des projets.

    1.  Ouvrez la solution.

    2.  Cliquez sur le **transformer tous les modèles** bouton dans l’en-tête de l’Explorateur de solutions.

        > [!NOTE]
        >  Vous pouvez effectuer cette étape inutiles. Pour plus d’informations, consultez [comment automatiser transformer tous les modèles](http://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a).

6.  Mettre à jour votre code personnalisé dans les projets convertis.

    -   Tentez de générer les projets et examiner les échecs.

    -   Tester votre concepteur.


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Voir aussi

- [Billets de blog connexes](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)