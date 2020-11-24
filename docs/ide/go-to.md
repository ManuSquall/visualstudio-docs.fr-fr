---
title: Atteindre le fichier, atteindre le symbole, atteindre la ligne
description: En savoir plus sur les commandes atteindre dans Visual Studio et sur la façon dont vous pouvez les utiliser pour effectuer des recherches ciblées sur votre code.
ms.custom: SEO-VS-2020
ms.date: 08/14/2018
ms.topic: conceptual
helpviewer_keywords:
- code editor, go to
- code editor, go to line
- go to line
- go to
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3e000224fc09810e15ba3cdbdc4be729139eaaa
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597533"
---
# <a name="find-code-using-go-to-commands"></a>Rechercher du code à l’aide des commandes Atteindre

Les commandes **Atteindre** de Visual Studio vous permettent d’effectuer une recherche ciblée dans votre code pour trouver rapidement des éléments spécifiques. Vous pouvez atteindre une ligne, un type, un symbole, un fichier ou un membre spécifique à partir d’une interface unifiée simple.

## <a name="how-to-use-it"></a>Comment l’utiliser

Entrée | Fonction
------------ | ---
**Clavier** | Appuyez sur **CTRL** + **T** ou **CTRL** + **,**
**Souris** | Sélectionnez **modifier**  >  **atteindre** atteindre  >  **tout** .

Une petite fenêtre s’affiche en haut à droite de votre éditeur de code.

![Fenêtre Atteindre tout](media/go-to-all.png)

À mesure que vous tapez dans la zone de texte, les résultats s’affichent dans une liste déroulante sous la zone de texte. Pour accéder à un élément, sélectionnez-le dans la liste.

![Fenêtre Naviguer vers](../ide/media/vside_navigatetowindow.png)

Vous pouvez aussi entrer un point d’interrogation (**?**) pour obtenir une aide supplémentaire.

![Aide sur Atteindre tout](media/go-to-all-help.png)

## <a name="filtered-searches"></a>Recherches filtrées

Par défaut, l’élément spécifié est recherché dans tous les éléments de solution. Toutefois, vous pouvez limiter votre recherche de code à des types d’éléments spécifiques en faisant précéder les termes de recherche de certains caractères. Vous pouvez également modifier rapidement le filtre de recherche en choisissant des boutons dans la barre d’outils de la boîte **de dialogue atteindre** . Les boutons qui changent les filtres de type se trouvent à gauche, et les boutons qui changent l’étendue de recherche se trouvent à droite.

![Atteindre des membres](../ide/media/vside_navigation_toolbar.png)

### <a name="filter-to-a-specific-type-of-code-element"></a>Filtrer sur un type spécifique d’élément de code

Pour limiter votre recherche à un type spécifique d’élément de code, vous pouvez spécifier un préfixe dans la zone de recherche ou sélectionner l’une des cinq icônes de filtre ci-dessous :

Préfixe | Icône | Raccourci | Description
:-: | - | - | -
:| ![Icône de ligne](media/gotoall-line-icon.png) | **CTRL** + **G** | Atteindre le numéro de ligne spécifié
f| ![Icône de fichiers](media/gotoall-files-icon.png) | **CTRL** + **1**, **CTRL** + **F** | Atteindre le fichier spécifié
r| ![Icône de fichiers récents](media/gotoall-recent-files-icon.png) | **CTRL** + **1**, **CTRL** + **R** | Atteindre le fichier spécifié, récemment ouvert
t| ![Icône de types](media/gotoall-types-icon.png) | **CTRL** + **1**, **CTRL** + **T** | Atteindre le type spécifié
m| ![Icône de membres](media/gotoall-members-icon.png) | **CTRL** + **1**, **CTRL** + **M** | Atteindre le membre spécifié
\#| ![Icône de symboles](media/gotoall-symbols-icon.png) | **CTRL** + **1**, **CTRL** + **S** | Atteindre le symbole spécifié

### <a name="filter-to-a-specific-location"></a>Filtrer sur un emplacement spécifique

Pour limiter votre recherche à un emplacement spécifique, sélectionnez l’une des deux icônes de document ci-dessous :

Icône | Description
---- | ---
![Document actif](media/gotoall_currentdocument.png) | Rechercher dans le document actif uniquement
![Documents externes](media/gotoall_external.png) | Rechercher dans des documents externes en plus de ceux qui se trouvent dans le projet ou la solution

## <a name="camel-casing"></a>Casse mixte

Si vous utilisez une [casse mixte](https://en.wikipedia.org/wiki/Camel_case) dans votre code, vous pouvez trouver plus rapidement des éléments de code en entrant uniquement les lettres majuscules de leur nom. Par exemple, si votre code a un type appelé `CredentialViewModel` , vous pouvez affiner la recherche en choisissant le filtre de **type** (**t**), puis en entrant uniquement les majuscules du nom ( `CVM` ) dans la boîte de dialogue atteindre. Cette fonctionnalité peut être particulièrement utile si votre code contient des noms longs.

![Fenêtre Naviguer vers - recherche en lettres capitales](../ide/media/vside_capitalsearch.png)

## <a name="settings"></a>Paramètres

Sélectionnez l’icône d’engrenage ![icône Engrenage](media/gotoall_gear.png) si vous souhaitez changer le comportement de cette fonctionnalité :

Paramètre | Description
------- | ---
Utiliser l'onglet d'aperçu | Afficher l’élément sélectionné immédiatement dans l’onglet d’aperçu de l’IDE
Afficher les détails | Afficher les informations sur un projet, un fichier et une ligne, et un récapitulatif des commentaires de documentation dans la fenêtre
Centrer la fenêtre | Déplacer cette fenêtre pour qu’elle s’affiche en haut au centre de l’éditeur de code, au lieu d’en haut à droite

## <a name="see-also"></a>Voir aussi

- [Naviguer dans le code](../ide/navigating-code.md)
- [Atteindre la ligne, boîte de dialogue](../ide/reference/go-to-line.md)
- [Atteindre la définition et Aperçu de la définition](../ide/go-to-and-peek-definition.md)
