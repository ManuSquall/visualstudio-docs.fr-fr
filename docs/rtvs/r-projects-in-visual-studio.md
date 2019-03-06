---
title: Projets R
description: Guide pratique pour créer des projets R managés dans Visual Studio, y compris les propriétés, les commandes de projet et les modèles.
ms.date: 06/29/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 3fbe819a13466c3b67f34b0de9d7e60e10aaa57b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55936185"
---
# <a name="create-r-projects-in-visual-studio"></a>Créer des projets R dans Visual Studio

Un projet R (un fichier *.rxproj*) identifie tous les fichiers sources et de contenu associés à votre projet. Il contient également des informations de génération pour chaque fichier, tient à jour les informations pour l’intégration aux systèmes de contrôle de code source et vous permet d’organiser votre application en composants logiques. Les informations relatives à l’espace de travail, telles que la liste des packages installés, sont toutefois gérées séparément dans l’espace de travail.

Les projets sont toujours gérés dans une *solution* Visual Studio, qui peut contenir un nombre quelconque de projets pouvant faire référence les uns aux autres. Consultez [Utiliser plusieurs types de projets dans Visual Studio](#use-multiple-project-types-in-visual-studio).

## <a name="creating-a-new-r-project"></a>Création d’un projet R

1. Démarrez Visual Studio.
1. Choisissez **Fichier > Nouveau > Projet**. (**Ctrl**+**MAJ**+**N**)
1. Sélectionnez « Projet R » sous **Modèles > R**, donnez au projet un nom et un emplacement, puis sélectionnez **OK** :

    ![Boîte de dialogue Nouveau projet pour R dans Visual Studio (RTVS dans VS2017)](media/getting-started-01-new-project.png)

Cette commande crée un projet avec un fichier *script.R* vide ouvert dans l’éditeur. Notez également dans l’**Explorateur de solutions** que deux autres fichiers figurent dans le projet :

![Contenu d’un projet R créé à partir du modèle](media/projects-template-results.png)

Le fichier *.Rhistory* enregistre toutes les commandes que vous entrez dans la Fenêtre [interactive R](interactive-repl-for-r-in-visual-studio.md). Vous pouvez ouvrir une fenêtre d’historique dédiée avec la commande **Outils R** > **Fenêtres** > **Historique**. Cette fenêtre comporte un bouton de barre d’outils et des éléments de menu contextuel pour effacer le contenu de l’historique.

Le fichier *rproject.rproj* tient à jour certains paramètres de projet propres à R qui ne sont pas tenus à jour par Visual Studio :

| Property | Par défaut | Description |
| --- | --- | --- |
| Version | 1.0 | Version des Outils R pour Visual Studio utilisée pour créer le projet. |
| RestoreWorkspace | Par défaut | Charger automatiquement les variables d’espace de travail précédentes à partir du fichier `.RData` dans le répertoire du projet. |
| SaveWorkspace | Par défaut | Enregistrer les variables d’espace de travail actuelles dans le fichier `.RData` dans le répertoire du projet lors de la fermeture d’un projet. |
| AlwaysSaveHistory | Par défaut | Enregistrer l’historique de la Fenêtre interactive actuelle pour le fichier `.RHistory` dans le répertoire du projet lors de la fermeture d’un projet. |
| EnableCodeIndexing | Oui | Détermine s’il faut exécuter une tâche d’indexation en arrière-plan pour accélérer les recherches de code. |
| UseSpacesForTab | Oui | Détermine s’il faut insérer des espaces (Oui) ou un caractère de tabulation (Non) quand la touche **Tab** est enfoncée dans l’éditeur. |
| NumSpacesForTab | 2 | Nombre d’espaces à insérer si UseSpacesForTab est Oui. |
| Encodage | UTF-8 | Encodage par défaut des fichiers `.R`. |
| RnwWeave | Sweave | Package à utiliser lors de la fusion d’un fichier Rnw. |
| LaTeX | pdfLaTeX | Bibliothèque à utiliser lors de la conversion de RMarkdwon au format PDF. |

### <a name="converting-a-folder-of-files-to-an-r-project"></a>Conversion d’un dossier de fichiers en projet R

Si vous avez un dossier de fichiers *.R* que vous souhaitez gérer dans un projet, effectuez les étapes suivantes :

1. Créez un projet dans Visual Studio comme décrit dans la section précédente.
1. Copiez vos fichiers dans le dossier du projet.
1. Dans l’Explorateur de solutions Visual Studio, cliquez avec le bouton droit sur le projet, sélectionnez **Ajouter** > **Élément existant** et accédez aux fichiers à ajouter. Quand vous sélectionnez **OK**, ils apparaissent dans l’arborescence du projet.
1. Pour organiser le code en sous-dossiers, cliquez avec le bouton droit sur le projet, sélectionnez tout d’abord **Ajouter** > **Nouveau dossier**, puis copiez les fichiers dans ce dossier et ajoutez les éléments existants à l’étape 3.

## <a name="project-properties"></a>Propriétés de projet

Pour ouvrir les pages de propriétés du projet, cliquez avec le bouton droit sur le projet dans l’**Explorateur de solutions**, puis sélectionnez **Propriétés**, ou sélectionnez l’élément de menu **Projet > Propriétés de (nom du projet)**. La fenêtre qui s’ouvre affiche les propriétés du projet :


| Onglet | Property | Description |
| --- | --- | --- |
| Exécuter | Fichier de démarrage | Nom du fichier qui s’exécute avec la commande **Fichier de démarrage source**, **F5**, **Déboguer** > **Démarrer le débogage**, ou **Déboguer** > **Démarrer sans débogage**. Vous pouvez également le définir comme fichier de démarrage en cliquant avec le bouton droit sur le fichier dans le projet et en sélectionnant **Définir comme script R de démarrage**. |
| | Réinitialiser la Fenêtre interactive R à l’exécution | Efface toutes les variables de l’espace de travail de la fenêtre interactive quand vous exécutez le projet. Cela permet de garantir l’absence de contenu d’espace de travail résiduel des exécutions précédentes. |
| | Chemin de projet distant | Chemin à un espace de travail distant. |
| | Transférer des fichiers à l’exécution | Indique si les fichiers projet, conformément au filtre dans **Fichiers à transférer**, doivent être copiés vers un espace de travail distant à chaque exécution. |
| | Fichiers à transférer | Noms de fichiers et caractères génériques indiquant les fichiers à copier vers un espace de travail distant si **Transférer des fichiers à l’exécution** est sélectionné. |
| Paramètres | (Fichier Settings.R) | Les paramètres de projet R proviennent des fichiers *Settings.R* ou **.Settings.R* qui se trouvent dans le projet. S’il n’existe aucun fichier de paramètres, vous pouvez ajouter des variables, enregistrer la page, et un fichier *Settings.R* par défaut est créé pour vous. Vous pouvez également ajouter le fichier de paramètres au projet par le biais de la commande de menu **Fichier** > **Ajouter un nouvel élément**. <br/> Les paramètres sont stockés sous forme de code R et le fichier peut être approvisionné avant d’exécuter d’autres modules. Ainsi, l’environnement est prérempli avec les paramètres prédéfinis. |

## <a name="r-specific-project-commands"></a>Commandes de projet propres à R

Les projets Visual Studio prennent en charge plusieurs commandes générales par l’intermédiaire du menu contextuel et du menu **Projet**. Pour des détails sur ces fonctionnalités générales, consultez [Solutions et projets dans Visual Studio](../ide/solutions-and-projects-in-visual-studio.md). N’oubliez pas toutefois que les outils R pour Visual Studio (RTVS) ajoutent certaines de leurs propres commandes au menu contextuel pour un projet R, ainsi que des fichiers et des dossiers dans le projet.

| Commande | Description |
| --- | --- |
| Définir le répertoire de travail ici | Définit le dossier du projet comme répertoire de travail de la fenêtre interactive R. Peut également être utilisé sur n’importe quel sous-dossier dans un projet. |
| Ouvrir le dossier conteneur | Ouvre l’Explorateur Windows à l’emplacement du fichier sélectionné. |
| Ajouter un script R | Crée et ouvre un nouveau fichier *.R* avec un nom par défaut. Vous pouvez aussi utiliser la commande **Ajouter** > **Nouvel élément** pour créer des fichiers *.R* et plusieurs autres types de fichiers. Consultez [Modèles d’élément propres à R](#r-specific-item-templates). |
| Ajouter un fichier Markdown R | Crée et ouvre un nouveau document *.rmd* avec un nom par défaut. Vous pouvez aussi utiliser la commande **Ajouter** > **Nouvel élément** pour créer des fichiers *.rmd* et plusieurs autres types de fichiers. Consultez [Modèles d’élément propres à R](#r-specific-item-templates).  |
| Publier les procédures stockées | Démarre un processus pour publier toutes les procédures stockées contenues dans le script R. Consultez [Utiliser des procédures stockées SQL Server](integrating-sql-server-with-r.md#work-with-sql-server-stored-procedures). |

## <a name="r-specific-item-templates"></a>Modèles d’élément propres à R

Les outils R pour Visual Studio incluent plusieurs modèles pour des types de fichiers spécifiques. Vous pouvez y accéder en cliquant avec le bouton droit sur un projet R et en sélectionnant **Ajouter** > **Nouvel élément**, en sélectionnant **Projet** > **Ajouter un nouvel élément** ou en utilisant **Fichier** > **Nouveau** > **Fichier** et en sélectionnant l’onglet **R**. Le meilleur moyen d’explorer un modèle consiste à créer un projet et à insérer des fichiers de chaque type.

> [!Note]
> Les commandes **Ajouter** > **Nouvel élément** affichent également les types de fichiers généraux qui ne sont pas répertoriés dans le tableau. Avec **Fichier** > **Nouveau** > **Fichier**, ces types figurent plutôt sous l’onglet **Général**.

| Type de fichier | Description |
| --- | --- |
| Script R | Fichier texte contenant les mêmes commandes qui peuvent être entrées sur la ligne de commande R. |
| R Markdown | Fichier contenant un document [R Markdown](rmarkdown-with-r-in-visual-studio.md). |
| Paramètres R | Fichier qui contient des paramètres d’application R. |
| Documentation R | Fichier de documentation R générique contenant uniquement les champs de nom, d’alias et de titre. |
| Documentation R (fonction) | Fichier de documentation R contenant de nombreux champs avec des commentaires pour décrire une fonction. |
| Documentation R (jeu de données) | Fichier de documentation R contenant de nombreux champs avec des commentaires pour décrire un jeu de données. |
| Requête SQL | Fichier *.sql* vide. Consultez [Utiliser SQL Server et R](integrating-sql-server-with-r.md). |
| Procédure stockée avec R | Fichier R avec un fichier de modèle de requête SQL enfant et de procédure stockée enfant. Consultez [Utiliser SQL Server et R](integrating-sql-server-with-r.md). |

## <a name="use-multiple-project-types-in-visual-studio"></a>Utiliser plusieurs types de projets dans Visual Studio

Les solutions Visual Studio constituent un emplacement logique idéal où regrouper et gérer des projets associés. Les solutions aident à organiser le code et facilitent la collaboration au sein des équipes.

Dans l’exemple ci-dessous, la solution contient un projet R avec un modèle créé à l’aide de R et d’Azure Machine Learning, un projet Python/scikit-learn, un projet C++ contenant des modules de travail de calcul intensif, un projet SQL pour la gestion des données et un projet Python/Bottle pour le site web qui publie le résultat :

![Explorateur de solutions Visual Studio affichant plusieurs projets associés dans une solution](media/projects-polyglot.png)

Le projet affiché en gras est le projet de « démarrage » de la solution. Pour le changer, cliquez sur un autre projet et sélectionnez **Définir comme projet de démarrage**.

> [!Note]
> À l’heure actuelle, il n’existe pas d’intégration de langage R en C#/C++ explicite (comme il en existe pour Python ; consultez [Créer une extension C++ pour Python](../python/working-with-c-cpp-python-in-visual-studio.md)).  Il existe toutefois des bibliothèques qui fournissent des ponts C# et C++ pour R.

Pour plus d’informations sur la gestion de projets et de solutions en général, consultez [Solutions et projets dans Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).
