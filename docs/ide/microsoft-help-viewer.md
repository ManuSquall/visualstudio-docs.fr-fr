---
title: Documentation d’aide hors connexion de Visual Studio
ms.date: 11/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-help-viewer
ms.topic: conceptual
f1_keywords:
- hv_general
helpviewer_keywords:
- Microsoft Help Viewer Help
- Help Viewer, printing a topic
- printing a topic [Help Viewer]
- Help Viewer, toolbar
- Help on Help [Help Viewer]
- Help Viewer, window components
- Help Viewer, navigating
- toolbar [Help Viewer]
ms.assetid: 74e41666-2ce8-4ac0-a0e5-3723d1e322c2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: be587e708857a5c46c92986decff75a4807f8897
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="microsoft-help-viewer"></a>Microsoft Help Viewer

Vous pouvez installer et afficher le contenu de divers produits et technologies sur votre ordinateur local à l’aide de Microsoft Help Viewer, notamment Visual Studio, le .NET Framework, la référence du langage, SQL Server et le développement Windows. Help Viewer vous permet d’effectuer les opérations suivantes :

-   Rechercher et télécharger des ensembles de contenu, aussi appelés livres.

-   Parcourir la table des matières pour rechercher des rubriques par titre.

-   Rechercher des sujets dans l'index.

-   Trouver des informations à l'aide de la recherche en texte intégral.

-   Afficher, imprimer des rubriques et leur ajouter des signets.

Pour installer Help Viewer, consultez [Installation de Microsoft Help Viewer](../ide/microsoft-help-viewer-installation.md). Pour commencer à lire des rubriques d’aide dans Help Viewer plutôt qu’en ligne, accédez au menu **Aide** de Visual Studio, puis choisissez **Définir les préférences pour l’aide** > **Lancer dans la visionneuse d’aide**.

## <a name="help-viewer-tour"></a>Visite guidée de Help Viewer

Vous pouvez rechercher des informations dans le contenu installé à l’aide des onglets de navigation, afficher le contenu installé sous le ou les onglets de la rubrique et gérer le contenu avec l’onglet **Gérer le contenu**. Vous pouvez également effectuer d’autres tâches en utilisant les boutons de la barre d’outils et rechercher des informations supplémentaires en bas à droite de la fenêtre.

### <a name="navigation-tabs"></a>Onglets de navigation

|Onglet|Description|
|---|-----------|
|Sommaire|Affiche le contenu installé sous forme de hiérarchie (table des matières). Vous pouvez spécifier des critères pour filtrer les titres qui s’affichent.|
|Index|Affiche une liste alphabétique des termes indexés. Vous pouvez effectuer des recherches dans l’index, spécifier des critères pour filtrer les entrées et rechercher les entrées d’index contenant ou commençant par du texte que vous spécifiez.|
|Favoris|Vous pouvez utiliser le bouton **Ajouter aux Favoris** pour définir comme « favoris » des rubriques qui s’affichent sous cet onglet. La section **Historique** affiche une liste de rubriques que vous avez récemment consultées.|
|Rechercher|Fournit une zone de texte dans laquelle vous pouvez rechercher des termes n’importe où dans le contenu, notamment dans les titres de rubrique et le code.|

### <a name="view-topics"></a>Afficher les rubriques

Chaque rubrique apparaît sous son propre onglet, et vous pouvez ouvrir plusieurs rubriques en même temps.

### <a name="manage-content"></a>Gérer le contenu

Vous pouvez installer, mettre à jour, déplacer et supprimer du contenu sous l’onglet **Gérer le contenu**. En haut de l’onglet, le contrôle **Source d’installation** vous permet de spécifier si vous voulez installer les livres à partir d’un emplacement réseau ou d’un disque ou un URI. La zone **Chemin d’accès au stockage local** indique l’emplacement où sont installés les livres sur l’ordinateur local. Vous pouvez les déplacer vers un autre emplacement à l’aide du bouton **Déplacer**.

La liste de contenu indique quels sont les livres que vous pouvez installer ou avez déjà installés, si une mise à jour est disponible et quelle est la taille de chaque livre. Vous pouvez installer ou supprimer un ou plusieurs livres en choisissant les liens **Ajouter** ou **Supprimer**, puis le bouton **Mettre à jour** du volet **Modifications en attente**. Si des mises à jour sont disponibles pour un livre que vous avez déjà installé, vous pouvez actualiser ce contenu en choisissant le lien **Cliquez ici pour télécharger** en bas de la fenêtre. Par ailleurs, tous les livres installés sont actualisés si des mises à jour sont disponibles au moment où vous installez des livres supplémentaires.

> [!NOTE]
> Les fonctionnalités de l’onglet **Gérer le contenu** peuvent varier si l’administrateur Help Viewer désactive ces fonctionnalités, ou si aucun accès Internet n’est disponible.

### <a name="toolbar-buttons"></a>Boutons de la barre d'outils

La barre d’outils de la fenêtre de **Help Viewer** contient les boutons suivants :

-   Le bouton **Afficher la rubrique dans le sommaire** affiche l’emplacement de la rubrique sous l’onglet **Sommaire**.

-   Le bouton **Ajouter aux favoris** ajoute la rubrique active à l’onglet **Favoris**.

-   Le bouton **Chercher dans la rubrique** met en surbrillance le texte de recherche dans la rubrique active.

-   Le bouton **Imprimer** imprime ou affiche un aperçu de la rubrique active.

-   Le bouton **Options de la visionneuse** affiche des paramètres comme la taille du texte affiché, le nombre de résultats de recherche à retourner, le nombre de rubriques à afficher dans l’historique et s’il faut rechercher les mises à jour en ligne.

-   Le bouton **Gérer le contenu** active l’onglet **Gérer le contenu**.

-   Le petit triangle à droite ouvre une liste d’onglets, dont les onglets de la rubrique et l’onglet **Gérer le contenu**. Vous pouvez choisir le nom d’un onglet pour qu’il devienne l’onglet actif.

## <a name="see-also"></a>Voir aussi

- [Installation de Microsoft Help Viewer](../ide/microsoft-help-viewer-installation.md)
- [Guide de l’administrateur Help Viewer](../ide/help-viewer-administrator-guide.md)
- [Installer et gérer du contenu local](../ide/install-and-manage-local-content.md)
