---
title: Présentation des configurations de build
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
f1_keywords:
- SolutionProperties.ActiveConfig
- vs.build.newprojectconfiguration
- vc.proj.configurationsctrl.multipleconfigs
- vs.build.editsolutionconfigurations
- vs.build.editprojectconfigurations
- vs.multipleconfigurations
- vs.build.newsolutionconfiguration
- VS.ConfigurationManager
- VS.MultipleConfig
helpviewer_keywords:
- solution build configurations, about build configurations
- build configurations
- project build configurations
- build configurations, advanced
- projects [Visual Studio], build configuration
- solutions [Visual Studio], build configuration
ms.assetid: 934c727d-3a22-429c-bd13-3552cecf2e24
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47a76c054a71d88800bf1af225c332c9df3d2035
ms.sourcegitcommit: e3c3d2b185b689c5e32ab4e595abc1ac60b6b9a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2020
ms.locfileid: "76269135"
---
# <a name="understand-build-configurations"></a>Présentation des configurations de build

Vous avez besoin de configurations de build lorsque vous devez générer vos projets avec des paramètres différents. Par exemple, **Debug** et **Release** sont des configurations et des options de compilateur différentes sont utilisées en conséquence lors de leur génération.  Une configuration est active et est indiquée dans la barre de commandes en haut de l’IDE.

![Configuration active](media/understanding-build-configurations/active-config.png)

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Créer des configurations dans Visual Studio pour Mac](/visualstudio/mac/configurations).

La configuration et le contrôle de plateforme où sont stockés les fichiers de sortie générés. Normalement, lorsque Visual Studio génère votre projet, la sortie est placée dans un sous-dossier de projet nommé avec la configuration active (par exemple, *bin/debug/x86*), mais vous pouvez le modifier.

Vous pouvez créer vos propres configurations de build au niveau de la solution et du projet. La configuration de la solution détermine quels projets sont inclus dans la build lorsque cette configuration est active. Seuls les projets spécifiés dans la configuration de solution active seront générés. La configuration du projet détermine quels paramètres de génération et options du compilateur sont utilisés lorsque vous générez le projet.

Pour créer, sélectionner, modifier ou supprimer une configuration, vous pouvez utiliser le **Gestionnaire de configurations**. Pour l’ouvrir, dans la barre de menus, choisissez **Générer** > **Gestionnaire de configurations**, ou tapez simplement **Configuration** dans la zone de recherche. Vous pouvez également utiliser la liste **Configurations de solutions** dans la barre d’outils **Standard** pour sélectionner une configuration ou ouvrir le **Gestionnaire de configurations**.

![Gestionnaire de configurations](media/understanding-build-configurations/config-manager.png)

> [!NOTE]
> Si les paramètres de configuration de solution ne figurent pas dans la barre d’outils et si vous ne pouvez pas accéder au **Gestionnaire de configurations**, les paramètres de développement de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] peuvent être appliqués. Pour plus d’informations, consultez [Guide pratique pour gérer les configurations de build en appliquant les paramètres du développeur Visual Basic](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).

Par défaut, les configurations **Debug** et **Release** sont incluses dans les projets créés à l’aide de modèles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Une configuration **Debug** prend en charge le débogage d’une application, et une configuration **Release** génère une version de l’application qui peut être déployée. Pour plus d’informations, consultez [Guide pratique pour définir des configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md). Vous pouvez également créer des configurations de solution et des configurations de projet personnalisées. Pour plus d’informations, consultez [Guide pratique pour créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md).

## <a name="solution-configurations"></a>Configurations de solution

Une configuration de solution spécifie comment les projets de la solution doivent être générés et déployés. Pour modifier une configuration de solution ou en définir une nouvelle, dans le **Gestionnaire de configurations**, sous **Configuration de la solution active**, choisissez **Modifier** ou **Nouveau**.

Chaque entrée dans la zone **Contextes des projets** d’une configuration de solution représente un projet dans la solution. Pour chaque combinaison de **Configuration de la solution active** et de **Plateforme de la solution active**, vous pouvez définir la façon dont chaque projet est utilisé. (Pour plus d’informations sur les plateformes de solution, consultez [Présentation des plateformes de build](../ide/understanding-build-platforms.md).)

Quand vous définissez une nouvelle configuration de solution et que vous cochez la case **Créer des configurations de projet**, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] attribue automatiquement la nouvelle configuration à tous les projets. De la même manière, quand vous définissez une nouvelle plateforme de solution et que vous cochez la case **Créer des plateformes de projet**, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] attribue automatiquement la nouvelle plateforme à tous les projets. En outre, si vous ajoutez un projet ciblant une nouvelle plateforme, Visual Studio ajoute cette plateforme à la liste des plateformes de solution et l'attribue à tous les projets. Vous pouvez toujours modifier les paramètres de chaque projet.

La configuration de solution active fournit également le contexte à l'IDE. Par exemple, si vous travaillez sur un projet et que la configuration indique qu’il doit être généré pour un appareil mobile, la **Boîte à outils** n’affiche que les éléments qui peuvent être utilisés dans un projet d’appareil mobile.

## <a name="project-configurations"></a>Configurations de projet

La configuration et la plateforme ciblées par un projet sont utilisées ensemble pour spécifier les paramètres de build et les options du compilateur à utiliser lors de sa génération. Un projet peut avoir des paramètres différents pour chaque combinaison de configuration et de plateforme. Pour modifier les propriétés d’un projet, ouvrez le menu contextuel du projet dans **Explorateur de solutions**, puis choisissez **Propriétés**.  En haut de l’onglet **générer** du concepteur de projet, choisissez une configuration active pour modifier ses paramètres de génération.

![Configurations du concepteur de projets](media/understanding-build-configurations/project-designer-configuration.png)

## <a name="how-visual-studio-assigns-project-configurations"></a>Comment Visual Studio affecte des configurations de projet

Lorsque vous définissez une nouvelle configuration de solution sans copier les paramètres d'une configuration existante, Visual Studio utilise les critères ci-après pour assigner des configurations de projet par défaut. Les critères sont évalués dans l'ordre indiqué.

1. Si un projet a un nom de configuration ( *\<nom de la configuration> \<nom de la plateforme>* ) qui correspond exactement au nom de la nouvelle configuration de solution, cette configuration est attribuée. Les noms de configuration ne respectent pas la casse.

1. Si le projet a un nom de configuration dont une partie indique un nom de configuration identique à la nouvelle configuration de solution, cette configuration est assignée, même si l'autre partie du nom indique une plateforme différente.

1. Si aucun nom ne correspond en partie au nom de configuration, la première configuration répertoriée dans le projet est assignée.

## <a name="how-visual-studio-assigns-solution-configurations"></a>Comment Visual Studio affecte des configurations de solution

Quand vous créez une configuration de projet (dans le **Gestionnaire de configurations**, en choisissant **Nouveau** dans le menu déroulant de la colonne **Configuration** de ce projet) et que vous cochez la case **Créer des configurations de solutions**, Visual Studio recherche une configuration de solution du même nom pour générer le projet sur chaque plateforme prise en charge. Dans certains cas, Visual Studio renomme des configurations de solution existantes ou en définit de nouvelles.

Visual Studio utilise les critères ci-après pour assigner des configurations de solution.

- Si une configuration de projet ne spécifie pas de plateforme ou spécifie seulement une plateforme, une configuration de solution portant le même nom que la nouvelle configuration de projet est utilisée si elle existe déjà, ou ajoutée dans le cas contraire. Le nom par défaut de cette configuration de solution n’inclut pas le nom d’une plateforme ; il prend la forme *\<nom de la configuration de projet*.

- Si un projet prend en charge plusieurs plateformes, une configuration de solution est trouvée ou ajoutée pour chaque plateforme prise en charge. Le nom de chaque configuration de solution comprend le nom de la configuration de projet et celui de la plateforme, et se présente sous la forme *\<nom de la configuration de projet> \<nom de la plateforme*.

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : générer une application](../ide/walkthrough-building-an-application.md)
- [Compiler et générer](../ide/compiling-and-building-in-visual-studio.md)
- [Solutions et projets](../ide/solutions-and-projects-in-visual-studio.md)
- [Informations de référence sur les builds C/C++](/cpp/build/reference/c-cpp-building-reference)
- [Fonctionnement des plateformes de génération](understanding-build-platforms.md)
- [Créer des configurations (Visual Studio pour Mac)](/visualstudio/mac/configurations)
