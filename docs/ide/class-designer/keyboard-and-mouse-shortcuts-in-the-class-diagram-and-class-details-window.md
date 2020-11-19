---
title: Raccourcis clavier et souris pour le Concepteur de classes
description: Découvrez comment utiliser le clavier en plus de la souris pour effectuer des actions de navigation dans Concepteur de classes et dans la fenêtre Détails de classe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.classdetails.window
helpviewer_keywords:
- class diagrams, keyboard shortcuts
- class diagrams, mouse shortcuts
ms.assetid: c12d8dac-9902-4fde-b721-2a8116da53b7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c184a12474e2d7ff0b626547acaaf2a37d460c8e
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901100"
---
# <a name="keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window"></a>Raccourcis clavier et souris dans le diagramme de classes et dans la fenêtre Détails de classe

Vous pouvez utiliser le clavier en plus de la souris pour naviguer dans le **Concepteur de classes** et dans la fenêtre **Détails de classe**.

## <a name="use-the-mouse-in-class-designer"></a>Utiliser la souris dans le Concepteur de classes

Les actions de la souris suivantes sont prises en charge dans les diagrammes de classes :

|Combinaison avec la souris|Context|Description|
| - |-------------|-----------------|
|Double-clic|éléments Shape|Ouvre l'éditeur de code.|
|Double-clic|Connecteur d'interface lollipop|Développe/réduit l'interface lollipop.|
|Double-clic|Étiquette du connecteur d'interface lollipop|Appelle la commande **Afficher l’interface**.|
|Roulette de la souris|Diagramme de classes|Fait défiler verticalement.|
|**Maj**+roulette de la souris|Diagramme de classes|Fait défiler horizontalement.|
|**CTRL** + roulette de la souris|Diagramme de classes|Effectue un zoom.|
|**CTRL** + **MAJ** + clic|Diagramme de classes|Effectue un zoom.|

## <a name="use-the-mouse-in-the-class-details-window"></a>Utiliser la souris dans la fenêtre Détails de classe

À l’aide de la souris, vous pouvez modifier l’apparence de la fenêtre **Détails de classe** et des données qu’elle affiche de la manière suivante :

- Cliquez sur une cellule modifiable pour en modifier le contenu. Vos modifications sont répercutées partout où ces données sont stockées ou affichées, notamment dans la fenêtre **Propriétés** et dans le code source.

- Cliquez sur une cellule dans une ligne pour afficher les propriétés de l’élément représenté par cette ligne dans la fenêtre **Propriétés**.

- Pour modifier la largeur d'une colonne, faites glisser la bordure droite de l'en-tête de colonne en fonction de la largeur de colonne souhaitée.

- Développez ou réduisez les nœuds de compartiment ou de propriété en cliquant sur les flèches situées à gauche de la ligne.

- La fenêtre **Détails de classe** comporte plusieurs boutons permettant de créer des membres dans la classe actuelle et de naviguer entre les compartiments des membres dans la grille de la fenêtre **Détails de classe**.

## <a name="use-the-keyboard-in-class-designer"></a>Utiliser le clavier dans le Concepteur de classes

Les actions du clavier suivantes sont prises en charge dans les diagrammes de classes :

|Clé|Context|Description|
|---------|-------------|-----------------|
|**Touches de direction**|À l'intérieur des formes de type|Navigation en arborescence dans le contenu de la forme (habillage de la forme pris en charge). Les touches droite et gauche permettent de développer et réduire l'élément actuel s'il peut être développé ou, sinon, de naviguer vers l'élément parent (voir la section sur la navigation en arborescence pour plus de détails sur le comportement).|
|**Touches de direction**|Formes de niveau supérieur|Permettent de déplacer les formes dans le diagramme.|
|**MAJ** + **touches de direction**|À l'intérieur des formes de type|Combinaison de touches permettant la sélection continue d'éléments de forme, tels que des membres, des types imbriqués ou des compartiments. Ces raccourcis ne prennent pas en charge l'habillage.|
|**Page d'accueil**|À l'intérieur des formes de type|Permet d'atteindre le titre de la forme de niveau supérieur.|
|**Page d'accueil**|Formes de niveau supérieur|Permet d'atteindre la première forme dans le diagramme.|
|**End**|À l'intérieur des formes de type|Permet d'atteindre le dernier élément visible à l'intérieur de la forme.|
|**End**|Formes de niveau supérieur|Permet d'atteindre la dernière forme dans le diagramme.|
|**MAJ** + **Page d’hébergement**|À l'intérieur d'une forme de type|Sélectionne des éléments dans la forme, en commençant par l'élément actuel et en terminant par l'élément supérieur de cette forme.|
|**MAJ** + **Fin**|À l'intérieur d'une forme de type|Identique à **Shift** + la **page** de décalage, mais dans la direction verticale.|
|**Entrez**|Tous les contextes|Appelle l'action par défaut sur la forme qui est également réalisable avec un double-clic. Dans la plupart des cas, il s'agit de la commande Afficher le code, mais certains éléments définissent l'action par défaut différemment (lollipops, en-têtes de compartiment, étiquettes lollipop).|
|**+** les **-**|Tous les contextes|Si l’élément ayant le focus peut être développé, ces touches le développent ou le réduisent.|
|**>**|Tous les contextes|Sur un élément ayant des enfants, cette touche développe l’élément s’il était réduit et permet de naviguer vers le premier enfant.|
|**<**|Tous les contextes|Navigue jusqu'à l'élément parent.|
|**ALT** + **MAJ** + **L**|À l'intérieur des formes de type + sur les formes de type|Navigue vers l'interface lollipop de la forme actuellement sélectionnée si elle est présente.|
|**ALT** + **MAJ** + **B**|À l'intérieur des formes de type + sur les formes de type|Si la liste des types de base est indiquée sur la forme de type et possède plusieurs éléments, elle est développée si elle était réduite, et inversement.|
|**Supprimer**|Sur les formes de type et zones de commentaire|Appelle la commande **Supprimer du diagramme**.|
|**Supprimer**|Sur tout le reste|Appelle la commande **Supprimer du code** (membres, paramètres, associations, héritage, étiquettes lollipop).|
|**CTRL** + **Supprimer**|Tous les contextes|Appelle la commande **Supprimer du code** sur la sélection.|
|**Onglet**|Tous les contextes|Fait naviguer jusqu'à l'enfant suivant dans le même parent (prend en charge l'habillage).|
|**MAJ** + **Onglet**|Tous les contextes|Fait naviguer jusqu'à l'enfant précédent dans le même parent (prend en charge l'habillage).|
|**Touche**|Tous les contextes|Active ou désactive la sélection de l'élément actuel.|

## <a name="use-the-keyboard-in-the-class-details-window"></a>Utiliser le clavier dans la fenêtre Détails de classe

> [!NOTE]
> Les combinaisons de touches suivantes ont été choisies pour reproduire spécifiquement l’expérience de saisie du code.

Utilisez les touches suivantes pour naviguer dans la fenêtre **Détails de classe** :

|Clé|Résultats|
|-|-|
|**,** (virgule)|Si le curseur se trouve dans une ligne de paramètre, la saisie d'une virgule déplace le curseur dans le champ Nom du paramètre suivant. Si le curseur se trouve dans la dernière ligne de paramètre d’une méthode, il déplace le curseur vers le \<add parameter> champ, que vous pouvez utiliser pour créer un nouveau paramètre.<br /><br /> Si le curseur se trouve ailleurs dans la fenêtre **Détails de classe**, la saisie d’une virgule ajoute simplement une virgule dans le champ actuel.|
|**;** (point-virgule) ou **)** (parenthèse fermante)|Déplace le curseur dans le champ Nom de la ligne de membre suivante dans la grille de la fenêtre **Détails de classe**.|
|**Onglet**|Déplace le curseur dans le champ suivant (de gauche à droite, puis de haut en bas). Si le curseur quitte un champ dans lequel vous avez tapé du texte, **Détails de classe** traite ce texte et le stocke, sous réserve qu’aucune erreur n’ait été détectée.<br /><br /> Si le curseur se trouve dans un champ vide, tel que \<add parameter> , la touche Table déplace vers le premier champ de la ligne suivante.|
|**Touche**|Déplace le curseur dans le champ suivant (de gauche à droite, puis de haut en bas). Si le curseur se trouve dans un champ vide, tel que \<add parameter> , il se déplace vers le premier champ de la ligne suivante. Notez que l' \<space> entrée juste après une virgule est ignorée.<br /><br /> Si le curseur se trouve dans le champ Résumé, la saisie d'un espace ajoute un caractère espace.<br /><br /> Si le curseur se trouve dans la colonne Masquer d'une ligne, la saisie d'un espace inverse la valeur de la case à cocher Masquer.|
|**CTRL** + **Onglet**|Bascule vers une autre fenêtre de document, par exemple, de la fenêtre **Détails de classe** vers un fichier de code ouvert.|
|**Échap**|Si vous avez commencé à taper du texte dans un champ, l'utilisation de la touche Échap annule la saisie en cours et rétablit le contenu précédent du champ. Si la fenêtre Détails de classe est active, mais qu’aucune cellule spécifique n’a le focus, l’utilisation de la touche Échap déplace le focus hors de la fenêtre **Détails de classe**.|
|**Flèche haut** et **flèche bas**|Ces touches déplacent verticalement le curseur de ligne en ligne dans la grille de la fenêtre **Détails de classe**.|
|**Flèche gauche**|Si le curseur se trouve dans la colonne Nom, l'utilisation de la flèche gauche réduit le nœud actuel dans l'arborescence (s'il est développé).|
|**Flèche droite**|Si le curseur se trouve dans la colonne Nom, l’utilisation de la flèche droite développe le nœud actuel dans l’arborescence (s’il est réduit).|

## <a name="see-also"></a>Voir aussi

- [Créer et configurer des membres de type](creating-and-configuring-type-members.md)
- [Guide pratique pour utiliser uniquement le clavier](../reference/how-to-use-the-keyboard-exclusively.md)
- [Raccourcis clavier par défaut dans Visual Studio](../default-keyboard-shortcuts-in-visual-studio.md)
- [Raccourcis clavier dans Blend](../../xaml-tools/keyboard-shortcuts-in-blend.md)
