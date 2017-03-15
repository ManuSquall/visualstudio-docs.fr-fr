---
title: "Pr&#233;sentation des configurations de build | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SolutionProperties.ActiveConfig"
  - "vs.build.newprojectconfiguration"
  - "vc.proj.configurationsctrl.multipleconfigs"
  - "vs.build.editsolutionconfigurations"
  - "vs.build.editprojectconfigurations"
  - "vs.multipleconfigurations"
  - "vs.build.newsolutionconfiguration"
  - "VS.ConfigurationManager"
  - "VS.MultipleConfig"
helpviewer_keywords: 
  - "configurations de build"
  - "configurations de build, paramètres avancés"
  - "configurations de build de projet"
  - "projets (Visual Studio), configuration de build"
  - "configurations de build de solution, à propos des configurations de build"
  - "solutions (Visual Studio), configuration de build"
ms.assetid: 934c727d-3a22-429c-bd13-3552cecf2e24
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Pr&#233;sentation des configurations de build
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez enregistrer différentes configurations de propriétés de solution et de projet à utiliser dans différents types de builds.  Pour créer, sélectionner, modifier ou supprimer une configuration, vous pouvez utiliser le **Gestionnaire de configurations**.  Pour l'ouvrir, dans la barre de menus, sélectionnez **Générer**, **Gestionnaire de configurations**, ou tapez simplement Configuration dans la zone **Lancement rapide**.  Vous pouvez également utiliser la liste **Configurations de solutions** dans la barre d'outils **Standard** pour sélectionner une configuration ou ouvrir le **Gestionnaire de configurations**.  
  
> [!NOTE]
>  Si les paramètres de configuration de solution ne figurent pas dans la barre d'outils et si vous ne pouvez pas accéder au **Gestionnaire de configurations**, les paramètres de développement de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] peuvent être appliqués.  Pour plus d'informations, consultez [Comment : gérer des configurations en appliquant les paramètres du développeur Visual Basic](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).  
  
 Par défaut, les configurations Debug et Release sont incluses dans les projets créés à l'aide des modèles [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Une configuration Debug prend en charge le débogage d'une application, et une configuration Release génère une version de l'application qui peut être déployée.  Pour plus d'informations, consultez [Comment : définir des configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md).  Vous pouvez également créer des configurations de solution et des configurations de projet personnalisées.  Pour plus d'informations, consultez [Comment : créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md).  
  
## Configurations de solutions  
 Une configuration de solution spécifie comment les projets de la solution doivent être générés et déployés.  Pour modifier une configuration de solution ou en définir une nouvelle, dans le **Gestionnaire de configurations**, sous **Configuration de la solution active**, choisissez **Modifier** ou **Nouveau**.  
  
 Chaque entrée dans la zone **Contextes des projets** d'une configuration de solution représente un projet dans la solution.  Pour chaque combinaison de **Configuration de la solution active** et **Plateforme de la solution active**, vous pouvez définir la façon dont chaque projet est utilisé.  \(Pour plus d'informations concernant les plateformes de solution, consultez [Présentation des plateformes de générations](../ide/understanding-build-platforms.md)\).  
  
> [!NOTE]
>  Lorsque vous définissez une nouvelle configuration de solution et activez la case à cocher **Créer des configurations de projet**, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] attribue automatiquement la nouvelle configuration à tous les projets.  De la même manière, lorsque vous définissez une nouvelle plateforme de solution et activez la case à cocher **Créer des plateformes de projet**, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] attribue automatiquement la nouvelle plateforme à tous les projets.  En outre, si vous ajoutez un projet ciblant une nouvelle plateforme, Visual Studio ajoute cette plateforme à la liste des plateformes de solution et l'attribue à tous les projets.  
>   
>  Vous pouvez toujours modifier les paramètres de chaque projet.  
  
 La configuration de solution active fournit également le contexte à l'IDE.  Par exemple, si vous travaillez sur un projet et que la configuration indique qu'il doit être généré pour un appareil mobile, la **Boîte à outils** n'affiche que les éléments qui peuvent être utilisés dans un projet d'appareil mobile.  
  
## Configurations de projet  
 La configuration et la plateforme ciblées par un projet sont utilisées ensemble pour spécifier les propriétés à utiliser lors de sa génération.  Un projet peut avoir un ensemble différent de définitions de propriété pour chaque combinaison de configuration et de plateforme.  Pour modifier les propriétés d'un projet, vous pouvez utiliser ses pages de propriétés.  \(Dans l'**Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Propriétés**\).  
  
 Pour chaque configuration de projet, vous pouvez définir des propriétés dépendantes de la configuration si nécessaire.  Les propriétés du projet servent à déterminer, par exemple, les éléments de projet à inclure dans une version particulière ainsi que les fichiers de sortie à créer, leur emplacement et leur niveau d'optimisation.  
  
 Les configurations de projet peuvent varier considérablement.  Par exemple, les propriétés d'une configuration peuvent indiquer que son fichier de sortie est optimisé pour occuper le moins d'espace possible, tandis qu'une autre configuration peut indiquer que son fichier exécutable s'exécute à la vitesse maximale.  
  
 Les configurations de projet sont enregistrées par solution, et non par utilisateur, afin qu'elles puissent être partagées par une équipe.  
  
 Bien que les dépendances d'un projet ne soient pas liées à la configuration, seuls les projets spécifiés dans la configuration de solution active seront générés.  
  
## Comment Visual Studio assigne des configurations de projet  
 Lorsque vous définissez une nouvelle configuration de solution sans copier les paramètres d'une configuration existante, Visual Studio utilise les critères ci\-après pour assigner des configurations de projet par défaut.  Les critères sont évalués dans l'ordre indiqué.  
  
1.  Si un projet a un nom de configuration \(*\<nom de la configuration\> \<nom de la plateforme\>*\) qui correspond exactement au nom de la nouvelle configuration de solution, cette configuration est assignée.  Les noms de configuration ne respectent pas la casse.  
  
2.  Si le projet a un nom de configuration dont une partie indique un nom de configuration identique à la nouvelle configuration de solution, cette configuration est assignée, même si l'autre partie du nom indique une plateforme différente.  
  
3.  Si aucun nom ne correspond en partie au nom de configuration, la première configuration répertoriée dans le projet est assignée.  
  
## Comment Visual Studio assigne des configurations de solution  
 Lorsque vous créez une configuration de projet \(dans le **Gestionnaire de configurations**, en sélectionnant **Nouveau** dans le menu déroulant de la colonne **Configuration** pour ce projet\) et activez la case à cocher **Créer des configurations de solutions**, Visual Studio recherche une configuration de solution du même nom pour générer le projet sur chaque plateforme prise en charge.  Dans certains cas, Visual Studio renomme des configurations de solution existantes ou en définit de nouvelles.  
  
 Visual Studio utilise les critères ci\-après pour assigner des configurations de solution.  
  
-   Si une configuration de projet ne spécifie pas de plateforme ou spécifie seulement une plateforme, une configuration de solution portant le même nom que la nouvelle configuration de projet est utilisée si elle existe déjà, ou ajoutée dans le cas contraire.  Le nom par défaut de cette configuration de solution n'inclut pas le nom d'une plateforme ; il prend la forme *\<nom de la configuration de projet\>*.  
  
-   Si un projet prend en charge plusieurs plateformes, une configuration de solution est trouvée ou ajoutée pour chaque plateforme prise en charge.  Le nom de chaque configuration de solution comprend le nom de la configuration de projet et celui de la plateforme, et se présente sous la forme *\<nom de la configuration de projet\> \<nom de la plateforme\>*.  
  
## Voir aussi  
 [Procédure pas à pas : génération d'une application](../ide/walkthrough-building-an-application.md)   
 [Génération d'applications dans Visual Studio](../ide/compiling-and-building-in-visual-studio.md)   
 [Projets et solutions](../ide/solutions-and-projects-in-visual-studio.md)   
 [Référence à la génération C\/C\+\+](/visual-cpp/build/reference/c-cpp-building-reference)   
 [Commutateurs de la ligne de commande de Devenv](../ide/reference/devenv-command-line-switches.md)