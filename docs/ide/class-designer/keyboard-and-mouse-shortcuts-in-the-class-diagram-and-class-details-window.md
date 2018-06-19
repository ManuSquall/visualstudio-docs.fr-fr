---
title: Raccourcis clavier et souris pour le Concepteur de classes
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.classdetails.window
helpviewer_keywords:
- class diagrams, keyboard shortcuts
- class diagrams, mouse shortcuts
ms.assetid: c12d8dac-9902-4fde-b721-2a8116da53b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: db39f9c58c0fa2f0ea57d94cd1be404173720088
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33957312"
---
# <a name="keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window"></a>Raccourcis clavier et souris dans le diagramme de classes et dans la fenêtre Détails de classe

Vous pouvez utiliser le clavier en plus de la souris pour naviguer dans le **Concepteur de classes** et dans la fenêtre **Détails de classe**.

## <a name="use-the-mouse-in-class-designer"></a>Utiliser la souris dans le Concepteur de classes

Les actions de la souris suivantes sont prises en charge dans les diagrammes de classes :

|Combinaison avec la souris|Contexte|Description|
|-----------------------|-------------|-----------------|
|Double-clic|éléments Shape|Ouvre l'éditeur de code.|
|Double-clic|Connecteur d'interface lollipop|Développe/réduit l'interface lollipop.|
|Double-clic|Étiquette du connecteur d'interface lollipop|Appelle la commande **Afficher l’interface**.|
|Roulette de la souris|Diagramme de classes|Fait défiler verticalement.|
|**Maj**+roulette de la souris|Diagramme de classes|Fait défiler horizontalement.|
|**Ctrl**+roulette de la souris|Diagramme de classes|Effectue un zoom.|
|**Ctrl**+**Maj**+clic|Diagramme de classes|Effectue un zoom.|

## <a name="use-the-mouse-in-the-class-details-window"></a>Utiliser la souris dans la fenêtre Détails de classe

À l’aide de la souris, vous pouvez changer l’apparence de la fenêtre **Détails de classe** et des données qui y sont affichées en effectuant les étapes suivantes :

- Cliquez sur une cellule modifiable pour en modifier le contenu. Vos modifications sont répercutées partout où ces données sont stockées ou affichées, notamment dans la fenêtre **Propriétés** et dans le code source.

- Cliquez sur une cellule dans une ligne pour afficher les propriétés de l’élément représenté par cette ligne dans la fenêtre **Propriétés**.

- Pour modifier la largeur d'une colonne, faites glisser la bordure droite de l'en-tête de colonne en fonction de la largeur de colonne souhaitée.

- Développez ou réduisez les nœuds de compartiment ou de propriété en cliquant sur les flèches situées à gauche de la ligne.

- La fenêtre **Détails de classe** comporte plusieurs boutons permettant de créer des membres dans la classe actuelle et de naviguer entre les compartiments des membres dans la grille de la fenêtre **Détails de classe**.

## <a name="use-the-keyboard-in-class-designer"></a>Utiliser le clavier dans le Concepteur de classes

Les actions du clavier suivantes sont prises en charge dans les diagrammes de classes :

|Touche|Contexte|Description|
|---------|-------------|-----------------|
|**Touches de direction**|À l'intérieur des formes de type|Navigation en arborescence dans le contenu de la forme (habillage de la forme pris en charge). Les touches droite et gauche permettent de développer et réduire l'élément actuel s'il peut être développé ou, sinon, de naviguer vers l'élément parent (voir la section sur la navigation en arborescence pour plus de détails sur le comportement).|
|**Touches de direction**|Formes de niveau supérieur|Permettent de déplacer les formes dans le diagramme.|
|**Maj**+**touches de direction**|À l'intérieur des formes de type|Combinaison de touches permettant la sélection continue d'éléments de forme, tels que des membres, des types imbriqués ou des compartiments. Ces raccourcis ne prennent pas en charge l'habillage.|
|**Accueil**|À l'intérieur des formes de type|Permet d'atteindre le titre de la forme de niveau supérieur.|
|**Accueil**|Formes de niveau supérieur|Permet d'atteindre la première forme dans le diagramme.|
|**Fin**|À l'intérieur des formes de type|Permet d'atteindre le dernier élément visible à l'intérieur de la forme.|
|**Fin**|Formes de niveau supérieur|Permet d'atteindre la dernière forme dans le diagramme.|
|**Maj**+**Origine**|À l'intérieur d'une forme de type|Sélectionne des éléments dans la forme, en commençant par l'élément actuel et en terminant par l'élément supérieur de cette forme.|
|**Maj**+**Fin**|À l'intérieur d'une forme de type|Identique à **Maj**+**Origine**, mais du haut vers le bas.|
|**Entrée**|Tous les contextes|Appelle l'action par défaut sur la forme qui est également réalisable avec un double-clic. Dans la plupart des cas, il s'agit de la commande Afficher le code, mais certains éléments définissent l'action par défaut différemment (lollipops, en-têtes de compartiment, étiquettes lollipop).|
|**+** et **-**|Tous les contextes|Si l’élément ayant le focus peut être développé, ces touches le développent ou le réduisent.|
|**>**|Tous les contextes|Sur un élément ayant des enfants, cette touche développe l’élément s’il était réduit et permet de naviguer vers le premier enfant.|
|**<**|Tous les contextes|Navigue jusqu'à l'élément parent.|
|**Alt**+**Maj**+**L**|À l'intérieur des formes de type + sur les formes de type|Navigue vers l'interface lollipop de la forme actuellement sélectionnée si elle est présente.|
|**Alt**+**Maj**+**B**|À l'intérieur des formes de type + sur les formes de type|Si la liste des types de base est indiquée sur la forme de type et possède plusieurs éléments, elle est développée si elle était réduite, et inversement.|
|**Supprimer**|Sur les formes de type et zones de commentaire|Appelle la commande **Supprimer du diagramme**.|
|**Supprimer**|Sur tout le reste|Appelle la commande **Supprimer du code** (membres, paramètres, associations, héritage, étiquettes lollipop).|
|**Ctrl**+**Suppr**|Tous les contextes|Appelle la commande **Supprimer du code** sur la sélection.|
|**Tab**|Tous les contextes|Fait naviguer jusqu'à l'enfant suivant dans le même parent (prend en charge l'habillage).|
|**Maj**+**Tab**|Tous les contextes|Fait naviguer jusqu'à l'enfant précédent dans le même parent (prend en charge l'habillage).|
|**Barre d’espace**|Tous les contextes|Active ou désactive la sélection de l'élément actuel.|

## <a name="use-the-keyboard-in-the-class-details-window"></a>Utiliser le clavier dans la fenêtre Détails de classe

> [!NOTE]
> Les combinaisons de touches suivantes ont été choisies pour reproduire spécifiquement l’expérience de saisie du code.

Utilisez les touches suivantes pour naviguer dans la fenêtre **Détails de classe** :

|||
|-|-|
|Touche|Résultat|
|**,** (virgule)|Si le curseur se trouve dans une ligne de paramètre, la saisie d'une virgule déplace le curseur dans le champ Nom du paramètre suivant. S’il se trouve dans la dernière ligne de paramètre d’une méthode, le curseur est placé dans le champ \<ajouter un paramètre>, que vous pouvez utiliser pour créer un paramètre.<br /><br /> Si le curseur se trouve ailleurs dans la fenêtre **Détails de classe**, la saisie d’une virgule ajoute simplement une virgule dans le champ actuel.|
|**;** (point-virgule) ou **)** (parenthèse fermante)|Déplace le curseur dans le champ Nom de la ligne de membre suivante dans la grille de la fenêtre **Détails de classe**.|
|**Tab**|Déplace le curseur dans le champ suivant (de gauche à droite, puis de haut en bas). Si le curseur quitte un champ dans lequel vous avez tapé du texte, **Détails de classe** traite ce texte et le stocke, sous réserve qu’aucune erreur n’ait été détectée.<br /><br /> Si le curseur se trouve dans un champ vide comme \<ajouter un paramètre>, la touche Tab le place dans le premier champ de la ligne suivante.|
|**Barre d’espace**|Déplace le curseur dans le champ suivant (de gauche à droite, puis de haut en bas). Si le curseur se trouve dans un champ vide comme \<ajouter un paramètre>, il est placé dans le premier champ de la ligne suivante. Notez qu’un \<espace> saisi juste après une virgule est ignoré.<br /><br /> Si le curseur se trouve dans le champ Résumé, la saisie d'un espace ajoute un caractère espace.<br /><br /> Si le curseur se trouve dans la colonne Masquer d'une ligne, la saisie d'un espace inverse la valeur de la case à cocher Masquer.|
|**Ctrl**+**Tab**|Bascule vers une autre fenêtre de document, par exemple, de la fenêtre **Détails de classe** vers un fichier de code ouvert.|
|**Échap**|Si vous avez commencé à taper du texte dans un champ, l'utilisation de la touche Échap annule la saisie en cours et rétablit le contenu précédent du champ. Si la fenêtre Détails de classe est active, mais qu’aucune cellule spécifique n’a le focus, l’utilisation de la touche Échap déplace le focus hors de la fenêtre **Détails de classe**.|
|**Flèche haut** et **flèche bas**|Ces touches déplacent verticalement le curseur de ligne en ligne dans la grille de la fenêtre **Détails de classe**.|
|**Flèche gauche**|Si le curseur se trouve dans la colonne Nom, l'utilisation de la flèche gauche réduit le nœud actuel dans l'arborescence (s'il est développé).|
|**Flèche droite**|Si le curseur se trouve dans la colonne Nom, l’utilisation de la flèche droite développe le nœud actuel dans l’arborescence (s’il est réduit).|

## <a name="see-also"></a>Voir aussi

- [Créer et configurer des membres de type](creating-and-configuring-type-members.md)