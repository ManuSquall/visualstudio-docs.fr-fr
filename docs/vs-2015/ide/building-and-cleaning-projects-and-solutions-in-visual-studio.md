---
title: Créer des solutions de nettoyage de projets
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.BuildProjectPicker
- vs.batchbuild
helpviewer_keywords:
- Clean Solution command
- builds [Visual Studio], managing
- solution build configurations, starting
- Build Solution command
- project build configurations, starting
- build configurations, starting
- project build configurations, dependencies
- Rebuild Solution command
- solution build configurations, build order
- builds [Visual Studio], preparing
ms.assetid: 710891fd-379e-42c2-a84b-44a7af694ca0
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0183e17da3eacad4fbcb3eed256396ab68249099
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60054545"
---
# <a name="building-and-cleaning-projects-and-solutions-in-visual-studio"></a>Génération et nettoyage de solutions et de projets dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En appliquant les procédures décrites dans cette rubrique, vous pouvez générer, régénérer ou nettoyer tout ou partie des projets ou éléments de projet dans une solution. Pour accéder à un tutoriel pas à pas, consultez [Procédure pas à pas : Génération d’une application](../ide/walkthrough-building-an-application.md).

> [!NOTE]
>  En fonction de vos paramètres actifs, l’interface utilisateur dans votre édition de Visual Studio peut-être différente de celle décrite dans cette rubrique. Pour changer vos paramètres, ouvrez le menu **Outils**, puis choisissez **Importation et exportation de paramètres**. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Pour générer, régénérer ou nettoyer une solution entière

1. Dans l’**Explorateur de solutions**, choisissez ou ouvrez la solution.

2. Dans la barre de menus, choisissez **Générer**, puis choisissez l’une des commandes suivantes :

    - Choisissez **Générer** ou **Générer la Solution** pour compiler uniquement les fichiers de projet et les composants qui ont été modifiés depuis la dernière génération.

        > [!NOTE]
        >  La commande **Générer** devient **Générer la Solution** quand une solution contient plusieurs projets.

    - Choisissez **Régénérer la Solution** pour « nettoyer » la solution, puis générer tous les fichiers projet et les composants.

    - Choisissez **Nettoyer la solution** pour supprimer tous les fichiers intermédiaires et de sortie. De nouvelles instances des fichiers intermédiaires et de sortie peuvent alors être générées avec uniquement les fichiers projet et les composant restants.

## <a name="to-build-or-rebuild-a-single-project"></a>Pour générer ou régénérer un projet unique

1. Dans l’**Explorateur de solutions**, choisissez ou ouvrez le projet.

2. Dans la barre de menus, choisissez **Générer**, puis **Générer** _ProjectName_ ou **Régénérer** _ProjectName_.

    - Choisissez **Générer** _ProjectName_ pour générer uniquement les composants qui ont été modifiés depuis la dernière génération du projet.

    - Choisissez **Régénérer** _ProjectName_ pour « nettoyer » le projet, puis générer les fichiers projet et tous les composants du projet.

## <a name="to-build-only-the-startup-project-and-its-dependencies"></a>Pour générer uniquement le projet de démarrage et ses dépendances

1. Dans la barre de menus, sélectionnez **Outils**, **Options**.

2. Dans la boîte de dialogue **Options**, développez le nœud **Projets et solutions**, puis choisissez la page **Générer et exécuter**.

    La boîte de dialogue **Générer et exécuter, Projets et solutions, Options** s’affiche.

3. Cochez la case **Générer des projets de démarrage et des dépendances à l’exécution**.

    Quand cette case est cochée, seuls le projet de démarrage actuel et ses dépendances sont générés quand vous effectuez l’une des opérations suivantes :

   - Dans la barre de menus, choisissez **déboguer** > **démarrer le débogage** (F5).

   - Dans la barre de menus, choisissez **Build** > **générer la Solution** (CTRL + MAJ + B).

     Quand cette case est décochée, tous les projets, leurs dépendances et les fichiers solution sont générés quand vous exécutez l’une des commandes précédentes. Par défaut, cette case à cocher est désactivée.

## <a name="to-build-only-the-selected-visual-c-project"></a>Pour générer uniquement le projet Visual C++ sélectionné

1. Choisissez un projet [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] puis, dans la barre de menus, choisissez **Générer**, **Projet uniquement** et l’une des commandes suivantes :

   - **Générer uniquement** *nom_projet*

   - **Régénérer uniquement** *nom_projet*

   - **Nettoyer uniquement** *nom_projet*

   - **Lier uniquement** *nom_projet*

     Ces commandes s’appliquent uniquement au projet [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] que vous avez choisi, sans générer, régénérer, nettoyer ou lier aucune dépendance de projet ou fichier de solution. En fonction de votre version de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], le sous-menu **Projet uniquement** peut contenir plus de commandes.

## <a name="to-compile-multiple-c-project-items"></a>Pour compiler plusieurs éléments de projet C++

1. Dans l’**Explorateur de solutions**, choisissez plusieurs fichiers qui ont plusieurs actions de compilation, ouvrez le menu contextuel pour l’un de ces fichiers, puis choisissez **Compiler**.

     Si les fichiers ont des dépendances, ils seront compilés par ordre de dépendance. La compilation échoue si les fichiers nécessitent un en-tête précompilé qui n’est pas disponible lors de la compilation. L’opération de compilation utilise la configuration de solution active.

## <a name="to-stop-a-build"></a>Pour arrêter une génération

1. Effectuez l'une des étapes suivantes :

    - Dans la barre de menus, choisissez **Générer**, **Annuler**.

    - Choisissez les touches Ctrl + Arrêt.

## <a name="see-also"></a>Voir aussi
 [Guide pratique pour Afficher, enregistrer et configurer les fichiers journaux de génération](../ide/how-to-view-save-and-configure-build-log-files.md) [obtention des journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md) [compilation et génération](../ide/compiling-and-building-in-visual-studio.md) [présentation des Configurations de Build](../ide/understanding-build-configurations.md) [Debug et Release des Configurations de projet](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) [C /C++ référence à la génération](http://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d) [commutateurs de ligne de commande Devenv](../ide/reference/devenv-command-line-switches.md) [Solutions et projets](../ide/solutions-and-projects-in-visual-studio.md)
