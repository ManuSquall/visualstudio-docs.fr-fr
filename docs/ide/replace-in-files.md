---
title: Rechercher et remplacer dans les fichiers
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- find and replace
- replace in files
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dddd55714e53516ba1ccd8a11c99761a4db7136a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75585624"
---
# <a name="replace-in-files"></a>Remplacer dans les fichiers

**Remplacer dans les fichiers** vous permet de rechercher une chaîne ou une expression dans le code d’un ensemble défini de fichiers, et de modifier l’ensemble ou une partie des correspondances trouvées. Les correspondances trouvées et les actions prises sont répertoriées dans la fenêtre résultats de la **recherche** sélectionnée dans **options de résultat**.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans **l’aide** en fonction de vos paramètres actifs ou de l’édition. Pour modifier vos paramètres, par exemple pour définir les paramètres **Général** ou **Visual C++**, choisissez **Outils** > **Importation et exportation de paramètres**, puis choisissez **Réinitialiser tous les paramètres**.

Vous pouvez utiliser l’une des méthodes suivantes pour afficher l’option **Remplacer dans les fichiers** dans la fenêtre **Rechercher et remplacer**.

## <a name="to-display-replace-in-files"></a>Pour afficher Remplacer dans les fichiers

1. Dans le menu **Edition**, développez **Rechercher et remplacer**.

2. Choisissez **Remplacer dans les fichiers**.

   — ou —

   Si la fenêtre **Rechercher et remplacer** est déjà ouverte, dans la barre d’outils, choisissez **Remplacer dans les fichiers**.

## <a name="find-what"></a>Rechercher

Pour rechercher une nouvelle chaîne de texte ou expression, entrez-la dans cette zone. Pour rechercher l’une des 20 dernières chaînes que vous avez recherchées, ouvrez la liste déroulante et choisissez la chaîne. Choisissez le bouton adjacent **Générateur d’expressions** si vous souhaitez utiliser une ou plusieurs expressions régulières dans votre chaîne de recherche. Pour plus d’informations, consultez [Utiliser des expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> Le bouton **Générateur d’expressions** est activé uniquement si vous avez sélectionné **Expressions régulières** sous **Options de recherche**.

## <a name="replace-with"></a>Remplacer par

Pour remplacer des instances de la chaîne dans la zone **Rechercher** par une autre chaîne, entrez la chaîne de remplacement dans la zone **Remplacer par**. Pour supprimer des instances de la chaîne dans la zone **Rechercher**, laissez ce champ vide. Ouvrez la liste pour afficher les 20 chaînes que vous avez recherchées le plus récemment. Choisissez le bouton adjacent **Générateur d’expressions** si vous souhaitez utiliser une ou plusieurs expressions régulières dans votre chaîne de remplacement. Pour plus d’informations, consultez [Utiliser des expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="look-in"></a>Regarder dans

L’option choisie dans la liste déroulante **Regarder dans** détermine si la fonction **Remplacer dans les fichiers** effectue la recherche uniquement dans les fichiers actuellement actifs ou dans tous les fichiers stockés dans certains dossiers. Sélectionnez une étendue de recherche dans la liste, tapez le chemin d’un dossier ou cliquez sur le bouton **Parcourir (...)** pour afficher la boîte de dialogue **Choisir des dossiers de recherche** et choisissez un ensemble de dossiers. Vous pouvez également taper un chemin directement dans la zone **Regarder dans**.

> [!NOTE]
> Si l’option **Regarder dans** sélectionnée entraîne la recherche dans un fichier que vous avez extrait du contrôle de code source, la recherche ne porte que sur la version du fichier ayant été téléchargée sur votre ordinateur local.

## <a name="find-options"></a>Options de recherche

Vous pouvez développer ou réduire la section **options de recherche** . Les options suivantes peuvent être sélectionnées ou désélectionnées :

**Respecter la casse**

Quand vous sélectionnez cette option, les fenêtres **Résultats de la recherche** afficheront seulement les instances de la chaîne **Rechercher** dont le contenu et la casse sont identiques. Par exemple, la recherche de « MyObject » avec l’option **Respecter la casse** sélectionnée retourne « MyObject », mais pas « myobject » ni « MYOBJECT ».

**Mot entier**

Quand vous sélectionnez cette option, les fenêtres **Résultats de la recherche** afficheront seulement les instances de la chaîne **Rechercher** contenant les mêmes mots entiers. Par exemple, la recherche de « MyObject » retourne « MyObject », mais pas « CMyObject » ni « MyObjectC ».

**Utiliser des expressions régulières**

Quand cette case est cochée, vous pouvez utiliser des notations spéciales pour définir des modèles de texte dans les zones de texte **Rechercher** ou **Remplacer par**. Pour obtenir la liste de ces notations, consultez [Utiliser des expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

**Examiner ces types de fichiers**

Cette liste indique les types de fichiers à examiner dans les répertoires choisis dans **Regarder dans**. Si ce champ est laissé vide, tous les fichiers dans les répertoires choisis dans **Regarder dans** sont examinés. Sélectionnez un élément dans la liste pour entrer une chaîne de recherche prédéfinie à rechercher dans les fichiers de ces types particuliers.

## <a name="result-options"></a>Options de résultat

Vous pouvez développer ou réduire la section **options de résultat** . Les options suivantes peuvent être sélectionnées ou désélectionnées :

Fenêtre résultats de la **recherche 1**

Si cette option est sélectionnée, les résultats de la recherche actuelle remplacent le contenu de la fenêtre **Résultats de la recherche 1**. Cette fenêtre s'ouvre automatiquement pour afficher vos résultats de recherche. Pour ouvrir cette fenêtre manuellement, sélectionnez **Autres fenêtres** dans le menu **Affichage** et choisissez **Résultats de la recherche 1**.

Fenêtre résultats de la **recherche 2**

Si cette option est sélectionnée, les résultats de la recherche actuelle remplacent le contenu de la fenêtre **Résultats de la recherche 2**. Cette fenêtre s'ouvre automatiquement pour afficher vos résultats de recherche. Pour ouvrir cette fenêtre manuellement, sélectionnez **Autres fenêtres** dans le menu **Affichage** et choisissez **Résultats de la recherche 2**.

**Afficher les noms des fichiers seulement**

Lorsque cette case à cocher est activée, les fenêtres résultats de la **recherche** répertorient les noms complets et les chemins d’accès de tous les fichiers qui contiennent la chaîne recherchée. Toutefois, les résultats ne contiennent pas la ligne de code où apparaît la chaîne. Cette case à cocher est disponible uniquement pour **Rechercher dans les fichiers** .

**Conserver les fichiers modifiés ouverts après un remplacement global**

Lorsque cette option est activée, tous les fichiers dans lesquels des remplacements ont été effectués restent ouverts afin que vous puissiez annuler ou enregistrer ces modifications. Les contraintes de mémoire peuvent limiter le nombre de fichiers qui peuvent rester ouverts suite à une opération de remplacement.

> [!CAUTION]
> Vous ne pouvez utiliser la commande **Annuler** qu’avec les fichiers qui restent ouverts à des fins d’édition. Si vous n’activez pas cette option, les fichiers qui n’étaient pas ouverts à des fins d’édition restent fermés et l’option **Annuler** n’est pas disponible pour ces fichiers.

## <a name="see-also"></a>Voir aussi

- [Rechercher et remplacer du texte](../ide/finding-and-replacing-text.md)
- [Rechercher dans les fichiers](../ide/find-in-files.md)
- [Commandes Visual Studio](../ide/reference/visual-studio-commands.md)
