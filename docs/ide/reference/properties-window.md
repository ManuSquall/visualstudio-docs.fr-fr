---
title: Propriétés (fenêtre)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- properties [Visual Studio], Properties Window
- handler functions, Properties window
- handlers, Properties window
- Windows messages
- properties [Visual Studio], setting at design time
- properties [Visual Studio], editing
- Property Browser
- Windows messages, adding message handlers
- Properties window, overrides
- virtual functions, Properties window
- Properties window
ms.assetid: e6e0fa4f-75c4-4a52-af15-281cd61876ca
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2848a8197dfe62836918de51ae6e7d01677dac6d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947298"
---
# <a name="properties-window"></a>Propriétés (fenêtre)
Utilisez cette fenêtre pour afficher et modifier les événements et propriétés au moment du design des objets sélectionnés qui sont situés dans les éditeurs et les concepteurs. Vous pouvez également utiliser la fenêtre **Propriétés** pour afficher et modifier les propriétés des fichiers, des projets et des solutions. Vous trouverez la fenêtre **Propriétés** dans le menu **Affichage**. Vous pouvez également l’ouvrir en appuyant sur F4 ou en tapant **Propriétés** dans la fenêtre **Lancement rapide**.

 La fenêtre **Propriétés** affiche différents types de champs d’édition, en fonction des besoins d’une propriété particulière. Ces champs d’édition sont notamment des zones d’édition, des listes déroulantes et des liens vers des boîtes de dialogue d’éditeur personnalisé. Les propriétés affichées en gris sont en lecture seule.

## <a name="uielement-list"></a>Liste des éléments d’interface
 Nom de l’objet

 Répertorie les objets actuellement sélectionnés. Seuls les objets de l’éditeur ou du concepteur actif sont visibles. Quand vous sélectionnez plusieurs objets, seules les propriétés communes à tous les objets sélectionnés s’affichent.

 Par catégorie

 Répertorie, par catégorie, toutes les propriétés et valeurs de propriété pour l’objet sélectionné. Vous pouvez réduire une catégorie afin de limiter le nombre de propriétés visibles. Quand vous développez ou réduisez une catégorie, un signe plus (+) ou moins (-) s’affiche à gauche du nom de la catégorie. Les catégories sont répertoriées par ordre alphabétique.

 Alphabétique

 Trie par ordre alphabétique l’ensemble des événements et propriétés au moment du design pour les objets sélectionnés. Pour modifier une propriété non estompée, cliquez dans la cellule située à sa droite et entrez les modifications souhaitées.

 Pages de propriétés

 Affiche la boîte de dialogue **Pages de propriétés** ou le **Concepteur de projets** pour l’élément sélectionné. La boîte de dialogue Pages de propriétés affiche un sous-ensemble, un ensemble équivalent ou un sur-ensemble des propriétés disponibles dans la fenêtre **Propriétés**. Utilisez ce bouton pour afficher et modifier des propriétés relatives à la configuration active de votre projet.

 Propriétés

 Affiche les propriétés définies pour un objet. De nombreux objets possèdent également des événements qui peuvent être affichés à l’aide de la fenêtre **Propriétés**.

 Trier par source de propriété

 Propriétés de groupes par source, telles que l’héritage, les styles appliqués et les liaisons. Uniquement disponible lors de la modification de fichiers XAML dans le concepteur.

 Événements

 Affiche les événements définis pour un objet.

> [!NOTE]
> Ce contrôle de barre d’outils de la fenêtre **Propriétés** n’est disponible que quand un Concepteur de formulaires ou de contrôles est actif dans le contexte d’un projet [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Lors de la modification de fichiers XAML, les événements apparaissent sous un onglet séparé de la fenêtre Propriétés.


 Messages

 Répertorie tous les messages Windows. Vous permet d’ajouter ou de supprimer des fonctions gestionnaires spécifiées pour les messages fournis pour la classe sélectionnée.

> [!NOTE]
> Ce contrôle de barre d’outils de la fenêtre **Propriétés** n’est disponible que quand la fenêtre active est **Affichage de classes** dans le contexte d’un projet [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].


 Overrides

 Répertorie toutes les fonctions virtuelles de la classe sélectionnée, et vous permet d’ajouter ou de supprimer des fonctions de substitution.

> [!NOTE]
> Ce contrôle de barre d’outils de la fenêtre **Propriétés** n’est disponible que quand la fenêtre active est **Affichage de classes** dans le contexte d’un projet [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].


 Volet Description

 Présente le type de la propriété et la décrit brièvement. Vous pouvez activer et désactiver la description de la propriété à l’aide de la commande Description du menu contextuel.

> [!NOTE]
> Ce contrôle de barre d’outils de la fenêtre **Propriétés** n’est pas disponible lors de la modification de fichiers XAML dans le concepteur.


 Vue miniatures

 Affiche une représentation visuelle de l’élément actuellement sélectionné lors de la modification de fichiers XAML dans le concepteur.

 Rechercher

 Fournit une fonction de recherche pour les propriétés et événements lors de la modification de fichiers XAML dans le concepteur. La zone de recherche répond aux recherches de correspondance partielle de texte et met à jour les résultats de la recherche au fur et à mesure de la saisie.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les propriétés de projet](../../ide/reference/project-properties-reference.md)
- [Personnalisation des dispositions de fenêtres](../../ide/customizing-window-layouts-in-visual-studio.md)