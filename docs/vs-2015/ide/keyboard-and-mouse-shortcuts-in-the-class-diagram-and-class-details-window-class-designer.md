---
title: Raccourcis clavier et souris dans le diagramme de classes et dans la fenêtre Détails de classe (Concepteur de classes) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdetails.window
helpviewer_keywords:
- class diagrams, keyboard shortcuts
- class diagrams, mouse shortcuts
ms.assetid: c12d8dac-9902-4fde-b721-2a8116da53b7
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5865059e60907397ae7d69b230676ac63a5c3386
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543115"
---
# <a name="keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer"></a>Raccourcis clavier et souris dans le diagramme de classes et dans la fenêtre Détails de classe(Concepteur de classes)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser le clavier en plus de la souris pour naviguer dans le Concepteur de classes et dans la fenêtre **Détails de classe**.

 **Dans cette rubrique**

- [Utilisation de la souris dans le Concepteur de classes](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#MouseClassDesigner)

- [Utilisation de la souris dans le fenêtre Détails de classe](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#MouseClassDetails)

- [Utilisation du clavier dans le Concepteur de classes](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#KeyboardClassDesigner)

- [Utilisation du clavier dans le fenêtre Détails de classe](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#KeyboardClassDetails)

## <a name="using-the-mouse-in-class-designer"></a><a name="MouseClassDesigner"></a>Utilisation de la souris dans Concepteur de classes
 Les actions de la souris suivantes sont prises en charge dans les diagrammes de classes :

|Combinaison avec la souris|Context|Description|
|-----------------------|-------------|-----------------|
|Double-clic|éléments Shape|Ouvre l'éditeur de code.|
||Connecteur d'interface lollipop|Développe/réduit l'interface lollipop.|
||Étiquette du connecteur d'interface lollipop|Appelle la commande **Afficher l’interface**.|
|Roulette de la souris|Diagramme de classes|Fait défiler verticalement.|
|Maj+roulette de la souris|Diagramme de classes|Fait défiler horizontalement.|
|Ctrl+roulette de la souris|Diagramme de classes|Effectue un zoom.|
|Ctrl+Maj+clic|Diagramme de classes|Effectue un zoom.|

## <a name="using-the-mouse-in-the-class-details-window"></a><a name="MouseClassDetails"></a> Utilisation de la souris dans la fenêtre Détails de classe
 À l'aide de la souris, vous pouvez modifier l'apparence de la fenêtre Détails de classe et des données qui y sont affichées, en procédant comme suit :

- Cliquez sur une cellule modifiable pour en modifier le contenu. Vos modifications sont répercutées partout où ces données sont stockées ou affichées, y compris dans la fenêtre Propriétés et dans le code source.

- Cliquez sur une cellule dans une ligne pour afficher les propriétés de l'élément représenté par cette ligne dans la fenêtre Propriétés.

- Pour modifier la largeur d'une colonne, faites glisser la bordure droite de l'en-tête de colonne en fonction de la largeur de colonne souhaitée.

- Développez ou réduisez les nœuds de compartiment ou de propriété en cliquant sur les flèches situées à gauche de la ligne.

- La fenêtre Détails de classe comporte plusieurs boutons permettant d'ajouter de nouveaux membres à la classe actuelle et de naviguer entre les compartiments des membres dans la grille de la fenêtre Détails de classe. Pour plus d'informations, consultez la section sur les boutons de la fenêtre Détails de classe.

## <a name="using-the-keyboard-in-class-designer"></a><a name="KeyboardClassDesigner"></a>Utilisation du clavier dans Concepteur de classes
 Les actions du clavier suivantes sont prises en charge dans les diagrammes de classes :

|Clé|Context|Description|
|---------|-------------|-----------------|
|Touches de direction|À l'intérieur des formes de type|Navigation en arborescence dans le contenu de la forme (habillage de la forme pris en charge). Les touches droite et gauche permettent de développer et réduire l'élément actuel s'il peut être développé ou, sinon, de naviguer vers l'élément parent (voir la section sur la navigation en arborescence pour plus de détails sur le comportement).|
||Formes de niveau supérieur|Permettent de déplacer les formes dans le diagramme.|
|Maj+touches de direction|À l'intérieur des formes de type|Combinaison de touches permettant la sélection continue d'éléments de forme, tels que des membres, des types imbriqués ou des compartiments. Ces raccourcis ne prennent pas en charge l'habillage.|
|Origine|À l'intérieur des formes de type|Permet d'atteindre le titre de la forme de niveau supérieur.|
||Formes de niveau supérieur|Permet d'atteindre la première forme dans le diagramme.|
|FIN|À l'intérieur des formes de type|Permet d'atteindre le dernier élément visible à l'intérieur de la forme.|
||Formes de niveau supérieur|Permet d'atteindre la dernière forme dans le diagramme.|
|Maj+Début|À l'intérieur d'une forme de type|Sélectionne des éléments dans la forme, en commençant par l'élément actuel et en terminant par l'élément supérieur de cette forme.|
|Maj+Fin|À l'intérieur d'une forme de type|Identique à Maj+Origine, mais du haut vers le bas.|
|ENTRÉE|Tous les contextes|Appelle l'action par défaut sur la forme qui est également réalisable avec un double-clic. Dans la plupart des cas, il s'agit de la commande Afficher le code, mais certains éléments définissent l'action par défaut différemment (lollipops, en-têtes de compartiment, étiquettes lollipop).|
|+/-|Tous les contextes|Si l’élément ayant le focus peut être développé, ces touches le développent/réduisent.|
|>|Tous les contextes|Sur un élément ayant des enfants, cette touche développe l’élément s’il était réduit et permet de naviguer vers le premier enfant.|
|<|Tous les contextes|Navigue jusqu'à l'élément parent.|
|Alt+Maj+L|À l'intérieur des formes de type + sur les formes de type|Navigue vers l'interface lollipop de la forme actuellement sélectionnée si elle est présente.|
|Alt+Maj+B|À l'intérieur des formes de type + sur les formes de type|Si la liste des types de base est indiquée sur la forme de type et possède plusieurs éléments, elle est développée si elle était réduite, et inversement.|
|Suppression|Sur les formes de type et zones de commentaire|Appelle la commande **Supprimer du diagramme**.|
||Sur tout le reste|Appelle la commande **Supprimer du code** (membres, paramètres, associations, héritage, étiquettes lollipop).|
|Ctrl+Suppr|Tous les contextes|Appelle la commande **Supprimer du code** sur la sélection.|
|Tab|Tous les contextes|Fait naviguer jusqu'à l'enfant suivant dans le même parent (prend en charge l'habillage).|
|Maj+Tab|Tous les contextes|Fait naviguer jusqu'à l'enfant précédent dans le même parent (prend en charge l'habillage).|
|SPACE|Tous les contextes|Active ou désactive la sélection de l'élément actuel.|

## <a name="using-the-keyboard-in-the-class-details-window"></a><a name="KeyboardClassDetails"></a> Utilisation du clavier dans la fenêtre Détails de classe

> [!NOTE]
> Les combinaisons de touches suivantes ont été choisies pour reproduire spécifiquement l’expérience de saisie du code.

 Utilisez les touches suivantes pour naviguer dans la fenêtre Détails de classe :

|Clé|Résultats|
|-|-|
|, (virgule)|Si le curseur se trouve dans une ligne de paramètre, la saisie d'une virgule déplace le curseur dans le champ Nom du paramètre suivant. Si le curseur se trouve dans la dernière ligne de paramètre d’une méthode, il déplace le curseur vers le \<add parameter> champ, que vous pouvez utiliser pour créer un nouveau paramètre.<br /><br /> Si le curseur se trouve ailleurs dans la fenêtre Détails de classe, la saisie d'une virgule ajoute simplement une virgule dans le champ actuel.|
|; (point-virgule)<br /><br /> ou<br /><br /> ) (parenthèse fermante)|Déplace le curseur dans le champ Nom de la ligne de membre suivante dans la grille de la fenêtre Détails de classe.|
|Onglet|Déplace le curseur dans le champ suivant (de gauche à droite, puis de haut en bas). Si le curseur quitte un champ dans lequel vous avez tapé du texte, la fenêtre Détails de classe traite ce texte et le stocke, sous réserve qu'aucune erreur n'ait été détectée.<br /><br /> Si le curseur se trouve dans un champ vide, tel que \<add parameter> , la touche Table déplace vers le premier champ de la ligne suivante.|
|\<space>|Déplace le curseur dans le champ suivant (de gauche à droite, puis de haut en bas). Si le curseur se trouve dans un champ vide, tel que \<add parameter> , il se déplace vers le premier champ de la ligne suivante. Notez que l' \<space> entrée juste après une virgule est ignorée.<br /><br /> Si le curseur se trouve dans le champ Résumé, la saisie d'un espace ajoute un caractère espace.<br /><br /> Si le curseur se trouve dans la colonne Masquer d'une ligne, la saisie d'un espace inverse la valeur de la case à cocher Masquer.|
|Ctrl+Tab|Bascule vers une autre fenêtre de document, par exemple, de la fenêtre Détails de classe vers un fichier de code ouvert.|
|Échap (Échappement)|Si vous avez commencé à taper du texte dans un champ, l'utilisation de la touche Échap annule la saisie en cours et rétablit le contenu précédent du champ. Si la fenêtre Détails de classe est active, mais qu'aucune cellule spécifique n'a le focus, l'utilisation de la touche Échap déplace le focus hors de la fenêtre Détails de classe.|
|Haut et Bas|Ces touches déplacent verticalement le curseur de ligne en ligne dans la grille de la fenêtre Détails de classe.|
|Flèche gauche|Si le curseur se trouve dans la colonne Nom, l'utilisation de la flèche gauche réduit le nœud actuel dans l'arborescence (s'il est développé).|
|Flèche droite|Si le curseur se trouve dans la colonne Nom, l’utilisation de la flèche droite développe le nœud actuel dans l’arborescence (s’il est réduit).|

## <a name="see-also"></a>Voir aussi
 [Création et configuration de membres de type (Concepteur de classes)](../ide/creating-and-configuring-type-members-class-designer.md)
