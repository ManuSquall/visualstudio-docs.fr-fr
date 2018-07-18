---
title: Utiliser la table des matières de l’application Help Viewer dans Visual Studio
ms.date: 11/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-help-viewer
ms.topic: conceptual
f1_keywords:
- hv_contents
helpviewer_keywords:
- Help Viewer, table of contents filtering
- Help Viewer, Contents tab
- Contents tab [Help Viewer]
- table of contents filtering [Help Viewer]
ms.assetid: 8b98464d-2b05-4710-ad68-5647e78c6b7b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e7d9ae19cb2a37c6fbf6595a7f3a39895d22190
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31945751"
---
# <a name="how-to-find-topics-in-the-table-of-contents"></a>Guide pratique pour rechercher des rubriques dans la table des matières

Sous l’onglet **Sommaire**, vous pouvez utiliser la table des matières pour rechercher des informations. La table des matières est une liste pouvant être développée qui contient toutes les rubriques des livres installés. Pour obtenir des informations d’accessibilité sur la navigation dans la table des matières, consultez [Touches de raccourci (Help Viewer)](../ide/shortcut-keys-help-viewer.md).

> [!IMPORTANT]
> Le nombre de rubriques disponibles dans la table des matières dépend du filtre que vous avez sélectionné.

## <a name="filter-the-toc"></a>Filtrer la table des matières

Vous pouvez filtrer la table des matières pour réduire le nombre de rubriques qui s’affichent sous l’onglet **Sommaire**. Les titres apparaissent dans la liste que s'ils contiennent la racine du terme que vous spécifiez. Par exemple, si vous spécifiez le filtre « configurer », seuls les titres qui contiennent « configure » ou « configurer » s'affichent. Les nœuds dont les titres ne contiennent pas le terme sont réduits à un seul nœud avec des points de suspension (**...**).

1.  Choisissez l’onglet **Sommaire**.

2.  Dans la zone de texte **Filtrer le contenu**, entrez un terme.

> [!NOTE]
> Si le filtre met trop longtemps à s’exécuter, vous pouvez afficher les résultats plus rapidement à l’aide de l’opérateur de recherche avancé `title:`.

## <a name="synchronize-a-topic-with-the-toc"></a>Synchroniser une rubrique avec la table des matières

Si vous avez ouvert une rubrique à l’aide des fonctionnalités d’index ou de recherche en texte intégral, vous pouvez localiser cette rubrique dans la table des matières en synchronisant celle-ci avec la fenêtre de la rubrique.

1.  Affichez une rubrique.

2.  Cliquez dans la barre d’outils sur le bouton **Afficher la rubrique dans le sommaire**, ou appuyez sur **Ctrl**+**S**.

     L’onglet **Sommaire** s’ouvre et affiche l’emplacement de la rubrique dans la table des matières.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour rechercher des rubriques dans l’index](../ide/how-to-find-topics-in-the-index.md)
- [Guide pratique pour rechercher des rubriques](../ide/how-to-search-for-topics.md)
- [Microsoft Help Viewer](../ide/microsoft-help-viewer.md)