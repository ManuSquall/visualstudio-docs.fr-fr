---
title: Guide pratique pour suivre votre code en personnalisant la barre de défilement | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a9ebe7ec-4b6f-4ba2-a79e-80fab3db485b
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a852b0e5ac6c6a677caab97279a0b0cb0299d27f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670638"
---
# <a name="how-to-track-your-code-by-customizing-the-scrollbar"></a>Comment : suivre votre code en personnalisant la barre de défilement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quand vous travaillez sur de longs fichiers de code, il peut être difficile de tout garder en tête. Vous pouvez personnaliser la barre de défilement de la fenêtre de code pour avoir une vue générale de ce qui se produit dans votre code.

### <a name="to-show-annotations-on-the-scroll-bar"></a>Pour afficher les annotations dans la barre de défilement

1. Vous pouvez configurer la barre de défilement pour y afficher les modifications du code, les points d'arrêt, les erreurs et les signets.

     Ouvrez la page d’options **barre de défilement** (**Outils, options éditeur de texte). Tous les langages** ou une langue spécifique, ou tapez  **barre de défilement** dans la fenêtre lancement rapide).

2. Sélectionnez **Afficher les annotations au-dessus de la barre de défilement verticale**, puis sélectionnez les annotations à afficher. (L’option **Marques** inclut les points d’arrêt et les signets.)

3. Essayez maintenant. Ouvrez un fichier de code volumineux et remplacez un fichier qui se trouve à plusieurs endroits dans le fichier. La barre de défilement affiche l'effet de ces remplacements. Vous pouvez ainsi annuler des modifications si vous avez remplacé un élément par erreur.

     Voici à quoi ressemble la barre de défilement après la recherche d'une chaîne. Notez que toutes les instances de la chaîne sont affichées.

     ![Barre de défilement après recherche d’une chaîne.](../ide/media/enhancedscrollbarsearch.png "EnhancedScrollbarSearch")

     Voici la barre de défilement après le remplacement de toutes les instances de la chaîne. Vous voyez immédiatement que l'opération a causé quelques problèmes.

     ![Barre de défilement après remplacement d'une chaîne sans erreurs](../ide/media/enhancedscrollbarreplace.png "EnhancedScrollbarReplace")

### <a name="to-set-the-display-mode-for-the-scroll-bar"></a>Pour définir le mode d'affichage de la barre de défilement

1. La barre de défilement offre deux modes d'affichage : le mode barre (par défaut) et le mode mappage. Le mode barre affiche uniquement les indicateurs d'annotation dans la barre de défilement. En mode mappage, les lignes de code sont représentées dans la barre de défilement. Vous pouvez choisir la largeur des lignes et spécifier si les lignes affichent le code sous-jacent quand vous placez le pointeur dessus. Quand vous cliquez quelque part dans la barre de défilement, le curseur se déplace vers l'emplacement correspondant dans le code. Les zones réduites sont grisées différemment et se développent quand vous double-cliquez dessus.

     Dans la page d’options **Barre de défilement**, sélectionnez **Utiliser le mode barre pour la barre de défilement verticale** ou **Utiliser le mode mappage pour la barre de défilement verticale**. Vous pouvez choisir la largeur de l’affichage dans la liste déroulante **Vue d’ensemble du code source**.

     Voici comment se présente l'exemple de recherche avec le mode mappage et une largeur moyenne :

     ![Barre de défilement dans la carte du code](../ide/media/enhancedscrollbar.png "EnhancedScrollbar")

2. En mode mappage, pour activer les aperçus du code quand vous déplacez le curseur vers le haut et le bas dans la barre de défilement, sélectionnez l’option **Afficher l’info-bulle d’aperçu**. Voici à quoi cela ressemble :

     ![Barre de défilement avec une info-bulle](../ide/media/enhancedscrollbarsearchtooltip.png "EnhancedScrollbarSearchTooltip")

     Pour conserver le mode mappage et l’info-bulle d’aperçu de la barre de défilement, mais pas la vue d’ensemble du code source, définissez **Vue d’ensemble du code source** sur **Désactivé**.
