---
title: Présentation des configurations de build
ms.date: 01/20/2020
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
ms.openlocfilehash: a37d4fa5dc92253b94dc64590c9df5fec7703ceb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77904163"
---
# <a name="understand-build-configurations"></a>Présentation des configurations de build

Vous avez besoin de configurations de construction lorsque vous avez besoin de construire vos projets avec des paramètres différents. Par exemple, **Debug** et **Release** sont des configurations et différentes options de compilateur sont utilisées en conséquence lors de leur construction.  Une configuration est active et est indiquée dans la barre de commande en haut de l’IDE.

![Configuration active](media/understanding-build-configurations/active-config.png)

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Créer des configurations dans Visual Studio pour Mac](/visualstudio/mac/configurations).

La configuration et le contrôle de la plate-forme où les fichiers de sortie intégrés sont stockés. Normalement, lorsque Visual Studio construit votre projet, la sortie est placée dans un sous-plieur de projet nommé avec la configuration active (par exemple, *bin/Debug/x86),* mais vous pouvez changer cela.

Vous pouvez créer vos propres configurations de construction au niveau de la solution et du projet. La configuration de la solution détermine quels projets sont inclus dans la construction lorsque cette configuration est active. Seuls les projets spécifiés dans la configuration de la solution active seront construits. Si plusieurs plates-formes cibles sont sélectionnées dans Configuration Manager, tous les projets qui s’appliquent à cette plate-forme sont construits. La configuration du projet détermine les paramètres de construction et les options de compilateur qui sont utilisées lorsque vous construisez le projet.

Pour créer, sélectionner, modifier ou supprimer une configuration, vous pouvez utiliser le **Gestionnaire de configurations**. Pour l’ouvrir, sur la barre de menu, choisissez **Build** > **Configuration Manager**, ou tout simplement **tapez configuration** dans la boîte de recherche. Vous pouvez également utiliser la liste **Configurations de solutions** dans la barre d’outils **Standard** pour sélectionner une configuration ou ouvrir le **Gestionnaire de configurations**.

![Gestionnaire de configuration](media/understanding-build-configurations/config-manager.png)

> [!NOTE]
> Si vous ne trouvez pas de paramètres de configuration de solution [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] sur la barre d’outils et que vous ne pouvez pas accéder au Gestionnaire de **configuration,** des paramètres de développement peuvent être appliqués. Pour plus d’informations, consultez [Guide pratique pour gérer les configurations de build en appliquant les paramètres du développeur Visual Basic](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).

Par défaut, les configurations **Debug** et **Release** sont [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] incluses dans les projets créés à l’aide de modèles. Une configuration **Debug** prend en charge le débogage d’une application, et une configuration **De Release** construit une version de l’application qui peut être déployée. Pour plus d’informations, consultez [Guide pratique pour définir des configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md). Vous pouvez également créer des configurations de solution et des configurations de projet personnalisées. Pour plus d’informations, consultez [Guide pratique pour créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md).

## <a name="solution-configurations"></a>Configurations de solution

Une configuration de solution spécifie comment les projets de la solution doivent être générés et déployés. Pour modifier une configuration de solution ou en définir une nouvelle, dans le **Gestionnaire de configurations**, sous **Configuration de la solution active**, choisissez **Modifier** ou **Nouveau**.

Chaque entrée dans la zone **Contextes des projets** d’une configuration de solution représente un projet dans la solution. Pour chaque combinaison de **Configuration de la solution active** et de **Plateforme de la solution active**, vous pouvez définir la façon dont chaque projet est utilisé. (Pour plus d’informations sur les plateformes de solution, consultez [Présentation des plateformes de build](../ide/understanding-build-platforms.md).)

Quand vous définissez une nouvelle configuration de solution et que vous cochez la case **Créer des configurations de projet**, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] attribue automatiquement la nouvelle configuration à tous les projets. De la même manière, quand vous définissez une nouvelle plateforme de solution et que vous cochez la case **Créer des plateformes de projet**, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] attribue automatiquement la nouvelle plateforme à tous les projets. En outre, si vous ajoutez un projet ciblant une nouvelle plateforme, Visual Studio ajoute cette plateforme à la liste des plateformes de solution et l'attribue à tous les projets. Vous pouvez toujours modifier les paramètres de chaque projet.

La configuration de solution active fournit également le contexte à l'IDE. Par exemple, si vous travaillez sur un projet et que la configuration indique qu’il doit être généré pour un appareil mobile, la **Boîte à outils** n’affiche que les éléments qui peuvent être utilisés dans un projet d’appareil mobile.

## <a name="project-configurations"></a>Configurations de projet

La configuration et la plate-forme qu’un projet cible sont utilisées ensemble pour spécifier les paramètres de construction et les options de compilateur à utiliser lors de sa construction. Un projet peut avoir des paramètres différents pour chaque combinaison de configuration et de plate-forme. Pour modifier les propriétés d’un projet, ouvrez le menu raccourci pour le projet dans **Solution Explorer**, puis choisissez **Propriétés**.  En haut de l’onglet **Build** du concepteur du projet, choisissez une configuration active pour modifier ses paramètres de construction.

![Configurations de concepteur de projets](media/understanding-build-configurations/project-designer-configuration.png)

## <a name="building-multiple-configurations"></a>Construire plusieurs configurations

Lorsque vous construisez une solution à l’aide de la commande **Build** > **Build Solution,** Visual Studio ne construit que la configuration active. Tous les projets spécifiés dans cette configuration de solution sont construits, et la seule configuration de projet qui est construite est celle spécifiée dans la configuration de solution active et la plate-forme de solution active, qui est indiquée dans la barre d’outils de Visual Studio. Par exemple, **Debug** et **x86**. D’autres configurations et plates-formes définies ne sont pas construites.

Si vous souhaitez créer plusieurs configurations et plates-formes en une seule action, vous pouvez utiliser l’option **Build** > **Batch Build** dans Visual Studio. Pour accéder à cette fonctionnalité, appuyez sur **Ctrl**+**Q** pour ouvrir la boîte de recherche, et entrez `Batch build`. La construction par lots n’est pas disponible pour tous les types de projets. Voir [comment : Construire plusieurs configurations simultanément](how-to-build-multiple-configurations-simultaneously.md).

## <a name="how-visual-studio-assigns-project-configurations"></a>Comment Visual Studio affecte des configurations de projet

Lorsque vous définissez une nouvelle configuration de solution sans copier les paramètres d'une configuration existante, Visual Studio utilise les critères ci-après pour assigner des configurations de projet par défaut. Les critères sont évalués dans l'ordre indiqué.

1. Si un projet a un nom de configuration*\<(nom de configuration> nom de \<plate-forme>*) qui correspond exactement au nom de la nouvelle configuration de solution, cette configuration est attribuée. Les noms de configuration ne respectent pas la casse.

1. Si le projet a un nom de configuration dont une partie indique un nom de configuration identique à la nouvelle configuration de solution, cette configuration est assignée, même si l'autre partie du nom indique une plateforme différente.

1. Si aucun nom ne correspond en partie au nom de configuration, la première configuration répertoriée dans le projet est assignée.

## <a name="how-visual-studio-assigns-solution-configurations"></a>Comment Visual Studio affecte des configurations de solution

Quand vous créez une configuration de projet (dans le **Gestionnaire de configurations**, en choisissant **Nouveau** dans le menu déroulant de la colonne **Configuration** de ce projet) et que vous cochez la case **Créer des configurations de solutions**, Visual Studio recherche une configuration de solution du même nom pour générer le projet sur chaque plateforme prise en charge. Dans certains cas, Visual Studio renomme des configurations de solution existantes ou en définit de nouvelles.

Visual Studio utilise les critères ci-après pour assigner des configurations de solution.

- Si une configuration de projet ne spécifie pas de plateforme ou spécifie seulement une plateforme, une configuration de solution portant le même nom que la nouvelle configuration de projet est utilisée si elle existe déjà, ou ajoutée dans le cas contraire. Le nom par défaut de cette configuration de solution n’inclut pas un nom de plate-forme ; il prend le nom de configuration du * \<projet *de forme>.

- Si un projet prend en charge plusieurs plateformes, une configuration de solution est trouvée ou ajoutée pour chaque plateforme prise en charge. Le nom de chaque configuration de solution inclut à la fois le nom de configuration du projet et le nom de la plate-forme, et a le nom de configuration du projet de formulaire * \<> nom \<de plate-forme>*.

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : générer une application](../ide/walkthrough-building-an-application.md)
- [Compilation et génération](../ide/compiling-and-building-in-visual-studio.md)
- [Solutions et projets](../ide/solutions-and-projects-in-visual-studio.md)
- [Informations de référence sur les builds C/C++](/cpp/build/reference/c-cpp-building-reference)
- [Comprendre les plates-formes de construction](understanding-build-platforms.md)
- [Créer des configurations (Visual Studio pour Mac)](/visualstudio/mac/configurations)
