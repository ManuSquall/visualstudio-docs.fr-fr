---
title: 'Comment : migrer un langage spécifique à un domaine vers une nouvelle Version | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: d65739aa02f5e5a36f317bd113dd4dc349bde957
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Comment : migrer un langage spécifique à un domaine vers une nouvelle version
Vous pouvez migrer les projets qui définissent et utilisent le langage spécifique à un domaine à [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] à partir de la version de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] qui a été distribuée avec [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)].  
  
 Un outil de migration est fourni dans le cadre de [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)]. L’outil convertit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projets et solutions qui utilisent ou définissent des outils DSL.  
  
 Vous devez exécuter l’outil de migration explicitement : il n’est pas lancé automatiquement lorsque vous ouvrez une solution dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Vous trouverez l’outil et le document des instructions détaillées sur ce chemin d’accès :  
  
 **% Programme Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
## <a name="before-you-migrate-your-dsl-projects"></a>Avant de la migration de vos projets de DSL  
 L’outil de migration modifie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fichiers projet (**.csproj**) et les fichiers solution (**.sln**).  
  
#### <a name="to-prepare-projects-for-migration"></a>Pour préparer des projets pour la migration.  
  
-   Assurez-vous que le **.csproj** et **.sln** fichiers peuvent être écrites. S’ils sont sous contrôle de code source, assurez-vous qu’ils sont extraits.  
  
-   Effectuez une copie des dossiers que vous souhaitez effectuer la migration.  
  
## <a name="migrating-a-collection-of-projects"></a>Migration d’une Collection de projets  
  
#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Pour migrer DSL projets et Solutions Visual Studio 2010  
  
1.  Démarrez l’outil de Migration DSL.  
  
    -   Double-cliquez sur l’outil dans l’Explorateur Windows (ou l’Explorateur de fichiers) ou de démarrer l’outil à partir d’une invite de commandes. L’outil est à cet emplacement :  
  
         **%ProgramFiles%\Microsoft visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
2.  Choisissez un dossier qui contient les solutions et les projets que vous voulez convertir.  
  
    -   Entrez le chemin d’accès dans la zone en haut de l’outil, ou cliquez sur **Parcourir**.  
  
     L’outil de migration affiche une arborescence de projets qui définissent ou utiliser DSL. L’organigramme inclut chaque projet qui utilise le **Microsoft.VisualStudio.Modeling.Sdk** ou **TextTemplating** assemblys.  
  
3.  Passez en revue l’arborescence de projets et désélectionnez les projets que vous ne souhaitez pas convertir.  
  
    -   Sélectionnez un projet ou une solution pour afficher la liste des modifications qui permettront à l’outil.  
  
        > [!NOTE]
        >  Les cases à cocher qui apparaissent en regard des noms de dossier n’ont aucun effet. Vous devez développer les dossiers à inspecter les projets et solutions.  
  
4.  Convertir les projets.  
  
    1.  Cliquez sur **convertir**.  
  
         Avant de chaque fichier de projet est converti, une copie de *projet *** .csproj** est enregistré sous la forme *projet ***.vs2008.csproj**  
  
         Une copie de chaque *solution *** .sln** est enregistré sous la forme *solution ***.vs2008.sln**  
  
    2.  Recherchez les échecs de conversion qui sont signalés.  
  
         Erreurs sont signalées dans la fenêtre de texte. En outre, l’arborescence affiche un indicateur rouge sur chaque nœud qui n’a pas pu convertir. Vous pouvez cliquer sur le nœud pour obtenir plus d’informations sur cet échec.  
  
5.  **Transformer tous les modèles** dans les solutions contenant correctement convertis les projets.  
  
    1.  Ouvrez la solution.  
  
    2.  Cliquez sur le **transformer tous les modèles** bouton dans l’en-tête de l’Explorateur de solutions.  
  
        > [!NOTE]
        >  Vous pouvez effectuer cette étape inutiles. Pour plus d’informations, consultez [comment automatiser transformer tous les modèles](http://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a).  
  
6.  Mettre à jour votre code personnalisé dans les projets convertis.  
  
    -   Essayez de générer les projets et examiner les erreurs.  
  
    -   Testez votre concepteur.  
  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Voir aussi  
 [Billets de blog connexes](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)

