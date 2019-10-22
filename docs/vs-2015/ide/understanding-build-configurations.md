---
title: Présentation des configurations de build | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a7e7c184fd150c46b3a8be0ec583d4223487ad32
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672766"
---
# <a name="understanding-build-configurations"></a>Présentation des configurations de build
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez enregistrer différentes configurations de propriétés de solution et de projet à utiliser dans différents types de builds. Pour créer, sélectionner, modifier ou supprimer une configuration, vous pouvez utiliser le **Gestionnaire de configurations**. Pour l’ouvrir, dans la barre de menus, choisissez **Générer**, **Gestionnaire de configurations**, ou tapez simplement **Configuration** dans la zone **Lancement rapide**. Vous pouvez également utiliser la liste **Configurations de solutions** dans la barre d’outils **Standard** pour sélectionner une configuration ou ouvrir le **Gestionnaire de configurations**.

> [!NOTE]
> Si les paramètres de configuration de solution ne figurent pas dans la barre d’outils et si vous ne pouvez pas accéder au **Gestionnaire de configurations**, les paramètres de développement de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] peuvent être appliqués. Pour plus d’informations, consultez [Guide pratique pour gérer les configurations de build en appliquant les paramètres du développeur Visual Basic](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).

 Par défaut, les configurations Debug et Release sont incluses dans les projets créés à l'aide des modèles [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Une configuration Debug prend en charge le débogage d’une application, et une configuration Release génère une version de l’application qui peut être déployée. Pour plus d’informations, consultez [Guide pratique pour définir des configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md). Vous pouvez également créer des configurations de solution et des configurations de projet personnalisées. Pour plus d’informations, consultez [Guide pratique pour créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md).

## <a name="solution-configurations"></a>Configurations de solutions
 Une configuration de solution spécifie comment les projets de la solution doivent être générés et déployés. Pour modifier une configuration de solution ou en définir une nouvelle, dans le **Gestionnaire de configurations**, sous **Configuration de la solution active**, choisissez **Modifier** ou **Nouveau**.

 Chaque entrée dans la zone **Contextes des projets** d’une configuration de solution représente un projet dans la solution. Pour chaque combinaison de **Configuration de la solution active** et de **Plateforme de la solution active**, vous pouvez définir la façon dont chaque projet est utilisé. (Pour plus d’informations concernant les plateformes de solution, consultez [Présentation des plateformes de génération](../ide/understanding-build-platforms.md).)

> [!NOTE]
> Quand vous définissez une nouvelle configuration de solution et que vous cochez la case **Créer des configurations de projet**, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] attribue automatiquement la nouvelle configuration à tous les projets. De la même manière, quand vous définissez une nouvelle plateforme de solution et que vous cochez la case **Créer des plateformes de projet**, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] attribue automatiquement la nouvelle plateforme à tous les projets. En outre, si vous ajoutez un projet ciblant une nouvelle plateforme, Visual Studio ajoute cette plateforme à la liste des plateformes de solution et l'attribue à tous les projets.
>
> Vous pouvez toujours modifier les paramètres de chaque projet.

 La configuration de solution active fournit également le contexte à l'IDE. Par exemple, si vous travaillez sur un projet et que la configuration indique qu’il doit être généré pour un appareil mobile, la **Boîte à outils** n’affiche que les éléments qui peuvent être utilisés dans un projet d’appareil mobile.

## <a name="project-configurations"></a>Configurations de projet
 La configuration et la plateforme ciblées par un projet sont utilisées ensemble pour spécifier les propriétés à utiliser lors de sa génération. Un projet peut avoir un ensemble différent de définitions de propriété pour chaque combinaison de configuration et de plateforme. Pour modifier les propriétés d'un projet, vous pouvez utiliser ses pages de propriétés. (Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du projet, puis choisissez **Propriétés**.)

 Pour chaque configuration de projet, vous pouvez définir des propriétés dépendantes de la configuration si nécessaire. Les propriétés du projet servent à déterminer, par exemple, les éléments de projet à inclure dans une version particulière ainsi que les fichiers de sortie à créer, leur emplacement et leur niveau d'optimisation.

 Les configurations de projet peuvent varier considérablement. Par exemple, les propriétés d'une configuration peuvent indiquer que son fichier de sortie est optimisé pour occuper le moins d'espace possible, tandis qu'une autre configuration peut indiquer que son fichier exécutable s'exécute à la vitesse maximale.

 Les configurations de projet sont enregistrées par solution, et non par utilisateur, afin qu'elles puissent être partagées par une équipe.

 Bien que les dépendances d'un projet ne soient pas liées à la configuration, seuls les projets spécifiés dans la configuration de solution active seront générés.

## <a name="how-visual-studio-assigns-project-configurations"></a>Comment Visual Studio assigne des configurations de projet
 Lorsque vous définissez une nouvelle configuration de solution sans copier les paramètres d'une configuration existante, Visual Studio utilise les critères ci-après pour assigner des configurations de projet par défaut. Les critères sont évalués dans l'ordre indiqué.

1. Si un projet a un nom de configuration ( *\<nom de la configuration> \<nom de la plateforme>* ) qui correspond exactement au nom de la nouvelle configuration de solution, cette configuration est attribuée. Les noms de configuration ne respectent pas la casse.

2. Si le projet a un nom de configuration dont une partie indique un nom de configuration identique à la nouvelle configuration de solution, cette configuration est assignée, même si l'autre partie du nom indique une plateforme différente.

3. Si aucun nom ne correspond en partie au nom de configuration, la première configuration répertoriée dans le projet est assignée.

## <a name="how-visual-studio-assigns-solution-configurations"></a>Comment Visual Studio assigne des configurations de solution
 Quand vous créez une configuration de projet (dans le **Gestionnaire de configurations**, en choisissant **Nouveau** dans le menu déroulant de la colonne **Configuration** de ce projet) et que vous cochez la case **Créer des configurations de solutions**, Visual Studio recherche une configuration de solution du même nom pour générer le projet sur chaque plateforme prise en charge. Dans certains cas, Visual Studio renomme des configurations de solution existantes ou en définit de nouvelles.

 Visual Studio utilise les critères ci-après pour assigner des configurations de solution.

- Si une configuration de projet ne spécifie pas de plateforme ou spécifie seulement une plateforme, une configuration de solution portant le même nom que la nouvelle configuration de projet est utilisée si elle existe déjà, ou ajoutée dans le cas contraire. Le nom par défaut de cette configuration de solution n’inclut pas le nom d’une plateforme ; il prend la forme *\<nom de la configuration de projet*.

- Si un projet prend en charge plusieurs plateformes, une configuration de solution est trouvée ou ajoutée pour chaque plateforme prise en charge. Le nom de chaque configuration de solution comprend le nom de la configuration de projet et celui de la plateforme, et se présente sous la forme *\<nom de la configuration de projet> \<nom de la plateforme*.

## <a name="see-also"></a>Voir aussi
 [Procédure pas à pas : génération d’une application](../ide/walkthrough-building-an-application.md) [compilation et génération](../ide/compiling-and-building-in-visual-studio.md) de [solutions et de projets](../ide/solutions-and-projects-in-visual-studio.md) [C/C++ Building](https://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d) [commutateurs de ligne de commande devenv](../ide/reference/devenv-command-line-switches.md)
