---
title: Rechercher dans les fichiers
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e1f067df647f843819e085f283005606699f3bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595473"
---
# <a name="find-in-files"></a>Rechercher dans les fichiers

**Rechercher dans les fichiers** vous permet de rechercher un ensemble de fichiers spécifié. Les correspondances trouvées et les actions prises sont répertoriées dans la fenêtre résultats de la **recherche** sélectionnée dans **options de résultat**.

Vous pouvez utiliser l’une des méthodes suivantes pour afficher l’option **Rechercher dans les fichiers** de la fenêtre **Rechercher et remplacer**.

## <a name="to-display-find-in-files"></a>Pour afficher l'option Rechercher dans les fichiers

1. Dans la barre de menus, choisissez **modifier**  >  **Rechercher et remplacer**.

1. Choisissez **Rechercher dans les fichiers**.

Pour annuler une opération de recherche, appuyez sur **CTRL**  +  **Pause**.

> [!NOTE]
> L’outil Rechercher et remplacer n’effectue pas de recherche dans les répertoires ayant l’attribut `Hidden` ou `System`.

## <a name="find-what"></a>Rechercher

Pour rechercher une nouvelle chaîne de texte ou expression, entrez-la dans cette zone. Pour rechercher l’une des 20 dernières chaînes que vous avez recherchées, ouvrez la liste déroulante et choisissez la chaîne. Choisissez le bouton adjacent **Générateur d’expressions** si vous souhaitez utiliser une ou plusieurs expressions régulières dans votre chaîne de recherche. Pour plus d’informations, consultez [utilisation d’expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> Le bouton **Générateur d’expressions** est activé uniquement si vous avez sélectionné **Expressions régulières** sous **Options de recherche**.

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

**Respecter la casse**

Si vous sélectionnez cette option, la fenêtre **Résultats de la recherche** affiche uniquement les correspondances qui respectent la casse.

**Mot entier**

Si vous sélectionnez cette option, la fenêtre **Résultats de la recherche** affiche uniquement les correspondances de mot entier.

**Utiliser des expressions régulières**

Si cette case est cochée, vous pouvez utiliser des notations spéciales pour définir des modèles de texte à rechercher dans les zones de texte **Rechercher** ou **Remplacer par**. Pour obtenir la liste de ces notations, consultez [utilisation d’expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

**Examiner ces types de fichiers**

Cette liste indique les types de fichiers à examiner dans les répertoires choisis dans **Regarder dans**. Si ce champ est laissé vide, tous les fichiers présents dans les répertoires choisis dans **Regarder dans** sont examinés.

Sélectionnez un élément dans la liste pour entrer une chaîne de recherche prédéfinie à rechercher dans les fichiers de ces types particuliers.

## <a name="result-options"></a>Options de résultat

Vous pouvez développer ou réduire la section **options de résultat** . Les options suivantes peuvent être sélectionnées ou désélectionnées :

**Fenêtre résultats de la recherche 1**

Si cette option est sélectionnée, les résultats de la recherche actuelle remplacent le contenu de la fenêtre **Résultats de la recherche 1**. Cette fenêtre s'ouvre automatiquement pour afficher vos résultats de recherche. Pour ouvrir cette fenêtre manuellement, sélectionnez **Autres fenêtres** dans le menu **Affichage** et choisissez **Résultats de la recherche 1**.

**Fenêtre résultats de la recherche 2**

Si cette option est sélectionnée, les résultats de la recherche actuelle remplacent le contenu de la fenêtre **Résultats de la recherche 2**. Cette fenêtre s'ouvre automatiquement pour afficher vos résultats de recherche. Pour ouvrir cette fenêtre manuellement, sélectionnez **Autres fenêtres** dans le menu **Affichage** et choisissez **Résultats de la recherche 2**.

**Afficher les noms des fichiers seulement**

Affiche une liste des fichiers contenant des correspondances de recherche au lieu d'afficher les correspondances elles-mêmes.

**Ajouter les résultats**

Ajoute les résultats de la recherche actuelle aux résultats des recherches précédentes.

## <a name="see-also"></a>Voir aussi

- [Recherche et remplacement de texte](../ide/finding-and-replacing-text.md)
- [Remplacer dans les fichiers](../ide/replace-in-files.md)
- [Commandes Visual Studio](../ide/reference/visual-studio-commands.md)
