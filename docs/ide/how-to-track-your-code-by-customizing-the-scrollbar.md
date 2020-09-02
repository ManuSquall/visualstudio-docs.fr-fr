---
title: Mode de barre et mode de mappage pour la barre de défilement
ms.date: 03/20/2020
ms.topic: how-to
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d1b659dabed2337013ffb84ff48277f0edacb09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283981"
---
# <a name="how-to-customize-the-scroll-bar"></a>Procédure : Personnaliser la barre de défilement

Quand vous travaillez sur de longs fichiers de code, il peut être difficile de suivre où tout se trouve dans le fichier. Vous pouvez personnaliser la barre de défilement de l’éditeur de code pour avoir une vue générale de ce qui se produit dans votre code.

## <a name="annotations"></a>Annotations

Vous pouvez choisir si la barre de défilement affiche des annotations, telles que les modifications du code, les points d’arrêt, les signets, les erreurs et la position du signe d’insertion.

   1. Ouvrez la page des options **Barres de défilement** en choisissant **Outils** > **Options** > **Éditeur de texte** > **Tous les langages** > **Barres de défilement**.

   2. Sélectionnez **Afficher les annotations au-dessus de la barre de défilement verticale**, puis sélectionnez les annotations à afficher. Les annotations disponibles sont :

      - modifications
      - marques
      - erreurs
      - position du signe d’insertion

      > [!TIP]
      > L’option **Afficher les marques** inclut les points d’arrêt et les signets.

Testez-la en ouvrant un long fichier de code et en remplaçant du texte qui se répète à différents endroits dans le fichier. La barre de défilement affiche l'effet de ces remplacements. Vous pouvez ainsi annuler des modifications si vous avez remplacé un élément par erreur.

Voici à quoi ressemble la barre de défilement après la recherche d'une chaîne. Notez que toutes les instances de la chaîne sont affichées dans la barre de défilement.

![Barre de défilement Visual Studio après recherche d’une chaîne](../ide/media/enhancedscrollbarsearch.png)

Voici la barre de défilement après le remplacement de toutes les instances de la chaîne. Les marques rouge dans la barre de défilement montrent où le remplacement de texte a introduit des erreurs.

![Barre de défilement Visual Studio après remplacement d’une chaîne sans erreurs](../ide/media/enhancedscrollbarreplace.png)

## <a name="display-modes"></a>Modes d’affichage

La barre de défilement offre deux modes : le mode barre et le mode mappage.

### <a name="bar-mode"></a>Mode barre

Le *mode barre* affiche les indicateurs d’annotation dans la barre de défilement. En cliquant sur la barre de défilement, la page défile vers le haut ou vers le bas, mais ne va pas à cet emplacement dans le fichier.

### <a name="map-mode"></a>Mode mappage

Le *mode carte* affiche des lignes de code, en miniature, sur la barre de défilement. Vous pouvez choisir la largeur de la colonne de mappage en sélectionnant une valeur dans **Vue d’ensemble de la source**. Pour permettre un aperçu plus grand du code quand vous placez le pointeur sur le mappage, sélectionnez l’option **Afficher une info-bulle d’aperçu**. Les zones réduites sont grisées différemment et se développent quand vous double-cliquez dessus.

> [!TIP]
> Vous pouvez désactiver l’affichage du code miniature en mode mappage en définissant **Vue d’ensemble de la source** sur **Désactivé**. Si l’option **Afficher une info-bulle d’aperçu** est sélectionnée, vous voyez toujours un aperçu du code à cet emplacement quand vous placez votre pointeur sur la barre de défilement, et le curseur va toujours à cet emplacement dans le fichier quand vous cliquez.

L’image suivante illustre l’exemple de recherche avec le mode mappage et une largeur **moyenne** :

![Barre de défilement Visual Studio en mode mappage](../ide/media/enhancedscrollbar.png)

L’image suivante illustre l’option **Afficher une info-bulle d’aperçu** :

![Barre de défilement Visual Studio avec une info-bulle](../ide/media/enhancedscrollbarsearchtooltip.png)

> [!TIP]
> Pour modifier les couleurs affichées en mode carte, choisissez **Outils**  >  **options**  >  **environnement**  >  **polices et couleurs**. Ensuite, dans **éléments affichés**, choisissez l’un des éléments précédés de « vue d’ensemble », apportez les modifications souhaitées à la couleur, puis cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi

- [Fonctionnalités de l’éditeur de code](../ide/writing-code-in-the-code-and-text-editor.md)
