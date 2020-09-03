---
title: Rechercher dans les fichiers | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findreplace.findinfiles
- vs.findinfiles
helpviewer_keywords:
- objects [Visual Studio], finding
- text searches, replacing text
- objects [Visual Studio], searching for
- Find and Replace window, Find in Files tab
- text searches, Find and Replace window
- documents, searching
- files, searching
- Find in Files tab, Find and Replace window
ms.assetid: 989e0737-46d7-4474-8453-fad52a74669d
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5e21d0880813452e37c9e20afdc98321e4b2e3a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655899"
---
# <a name="find-in-files"></a>Rechercher dans les fichiers
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’option Rechercher dans les fichiers** vous permet de faire des recherches dans un ensemble défini de fichiers. Les correspondances trouvées et les actions prises sont répertoriées dans la fenêtre résultats de la **recherche** sélectionnée dans **options de résultat**.

 Vous pouvez utiliser l’une des méthodes suivantes pour afficher l’option **Rechercher dans les fichiers** de la fenêtre **Rechercher et remplacer**.

### <a name="to-display-find-in-files"></a>Pour afficher l'option Rechercher dans les fichiers

1. Dans la barre de menus, choisissez **Edition**, puis **Rechercher et remplacer**.

2. Choisissez **Rechercher dans les fichiers**.

   Pour annuler une opération de recherche, appuyez sur Ctrl+Pause.

> [!NOTE]
> L'outil Rechercher et remplacer n'effectue pas de recherche dans les répertoires définis avec l'attribut `Hidden` ou `System`.

## <a name="find-what"></a>Rechercher
 Pour rechercher une nouvelle chaîne de texte ou expression, entrez-la dans cette zone. Pour rechercher une des 20 dernières chaînes que vous avez recherchées récemment, ouvrez la liste et sélectionnez la chaîne à rechercher. Choisissez le bouton adjacent **Générateur d’expressions** si vous souhaitez utiliser une ou plusieurs expressions régulières dans votre chaîne de recherche. Pour plus d’informations, consultez [Utilisation d’expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="look-in"></a>Regarder dans
 L’option sélectionnée dans la liste déroulante **Regarder dans** détermine si l’option **Rechercher dans les fichiers** limite la recherche aux fichiers qui sont actuellement actifs ou l’étend à tous les fichiers stockés dans certains dossiers. Sélectionnez une étendue de recherche dans la liste ou cliquez sur le bouton **Parcourir (...)** pour afficher la boîte de dialogue **Choisir des dossiers de recherche** et spécifier l’ensemble de répertoires de votre choix. Vous pouvez également taper un chemin directement dans la zone **Regarder dans**.

> [!WARNING]
> Avec les options **Solution complète** ou **Projet actuel**, les fichiers solution et projet ne sont pas inclus dans la recherche. Pour effectuer une recherche dans les fichiers projet, choisissez un dossier de recherche.

> [!NOTE]
> Si l’option **Regarder dans** sélectionnée entraîne la recherche dans un fichier que vous avez extrait du contrôle de code source, la recherche ne porte que sur la version du fichier ayant été téléchargée sur votre ordinateur local.

## <a name="include-subfolders"></a>Inclure les sous-dossiers
 Spécifie que les sous-dossiers du dossier choisi dans **Regarder dans** sont inclus dans la recherche.

## <a name="find-options"></a>Options de recherche
 Vous pouvez développer ou réduire la section **options de recherche** . Les options suivantes peuvent être sélectionnées ou désélectionnées :

 Respecter la casse lorsqu’elle est sélectionnée, la recherche des **résultats** de la recherche est sensible à la casse

 Mot entier quand vous sélectionnez cette option, les fenêtres résultats de la **recherche** retournent uniquement les correspondances de mots entières.

 Utiliser des expressions régulières si cette case à cocher est activée, vous pouvez utiliser des notations spéciales pour définir des modèles de texte à faire correspondre dans les zones de texte **Rechercher** ou **remplacer par** . Pour obtenir la liste de ces notations, consultez [Utilisation d’expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 Examiner ces types de fichiers cette liste indique les types de fichiers dans lesquels effectuer la recherche **dans les répertoires de recherche** . Si ce champ est laissé vide, tous les fichiers présents dans les répertoires choisis dans **Regarder dans** sont examinés.

 Sélectionnez un élément dans la liste pour entrer une chaîne de recherche prédéfinie à rechercher dans les fichiers de ces types particuliers.

## <a name="result-options"></a>Options de résultat
 Vous pouvez développer ou réduire la section **options de résultat** . Les options suivantes peuvent être sélectionnées ou désélectionnées :

 Fenêtre résultats de la recherche 1 : lorsque cette option est sélectionnée, les résultats de la recherche actuelle remplacent le contenu de la fenêtre résultats de la **recherche 1** . Cette fenêtre s'ouvre automatiquement pour afficher vos résultats de recherche. Pour ouvrir cette fenêtre manuellement, sélectionnez **Autres fenêtres** dans le menu **Affichage** et choisissez **Résultats de la recherche 1**.

 Fenêtre résultats de la recherche 2 : lorsque cette option est sélectionnée, les résultats de la recherche actuelle remplacent le contenu de la fenêtre résultats de la **recherche 2** . Cette fenêtre s'ouvre automatiquement pour afficher vos résultats de recherche. Pour ouvrir cette fenêtre manuellement, sélectionnez **Autres fenêtres** dans le menu **Affichage** et choisissez **Résultats de la recherche 2**.

 Afficher les noms de fichiers affiche uniquement la liste des fichiers contenant des correspondances de recherche au lieu d’afficher les correspondances de recherche.

 L’ajout de résultats ajoute les résultats de la recherche aux résultats de la recherche précédents.

## <a name="see-also"></a>Voir aussi
 [Recherche et remplacement de texte](../ide/finding-and-replacing-text.md) [remplacer dans des fichiers](../ide/replace-in-files.md) [commandes Visual Studio](../ide/reference/visual-studio-commands.md)
