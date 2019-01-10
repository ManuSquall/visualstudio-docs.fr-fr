---
title: Fenêtre Boîte à outils
ms.date: 01/18/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vs.toolbox.general
- vs.toolbox
helpviewer_keywords:
- Toolbox [Visual Studio]
- custom controls [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 46a3a0a415af9cddcba63040fd445de7869921e2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53918610"
---
# <a name="toolbox"></a>Boîte à outils

La fenêtre **Boîte à outils** affiche les contrôles que vous pouvez ajouter à des projets Visual Studio. Pour ouvrir Boîte à outils, cliquez sur **Boîte à outils** dans le menu **Affichage**.

![Fenêtre Boîte à outils](media/toolbox.png)

Vous pouvez glisser-déplacer différents contrôles sur la surface du concepteur que vous utilisez, puis les redimensionner et les positionner.

Boîte à outils accompagne les modes concepteur, tels que celui associé à un fichier XAML. **Boîte à outils** affiche uniquement les contrôles utilisables dans le concepteur actuel. Vous pouvez rechercher des éléments dans **Boîte à outils** pour filtrer davantage les éléments qui s’affichent.

> [!NOTE]
> Pour certains types de projet, **Boîte à outils** n’affiche pas tous les éléments.

La version .NET Framework que cible votre projet détermine également les contrôles qui apparaissent dans Boîte à outils. Vous pouvez configurer votre projet pour cibler une version différente de .NET Framework à partir des pages de propriétés du projet. Sélectionnez le nœud de projet dans l’**Explorateur de solutions** puis, dans la barre de menus, choisissez **Projet** > **Propriétés de nom_projet**. Sous l’onglet **Application**, utilisez le menu déroulant **Framework cible**.

## <a name="manage-the-toolbox-window-and-its-controls"></a>Gérer la fenêtre Boîte à outils et ses contrôles

Par défaut, **Boîte à outils** est réduite le long du côté gauche de l’IDE de Visual Studio et apparaît quand le curseur se trouve au-dessus d’elle. Vous pouvez épingler **Boîte à outils** (en cliquant sur l’icône **Épingler** dans la barre d’outils de Boîte à outils) afin que l’application demeure ouverte quand vous déplacez le curseur. Vous pouvez également annuler l’ancrage de la fenêtre **Boîte à outils** et la faire glisser n’importe où à l’écran. Vous pouvez masquer **Boîte à outils**, l’ancrer et annuler son ancrage ; pour ce faire, cliquez avec le bouton droit sur la barre d’outils de Boîte à outils, puis sélectionnez l’option concernée.

Vous pouvez réorganiser les éléments d’un onglet de **Boîte à outils** ou ajouter des onglets et des éléments personnalisés à l’aide des commandes suivantes du menu contextuel :

- **Renommer un élément** : renomme l’élément sélectionné.

- **Afficher tout** : affiche tous les contrôles possibles (pas seulement ceux qui s’appliquent au concepteur actuel).

- **Vue Liste** : affiche les contrôles sous forme de liste verticale. Si cette option est décochée, les contrôles apparaissent horizontalement.

- **Choisir les éléments** : ouvre la boîte de dialogue **Choisir des éléments de boîte à outils**, dans laquelle vous pouvez spécifier les éléments qui apparaissent dans la **boîte à outils**. Vous pouvez afficher ou masquer un élément en cochant ou en décochant sa case.

- **Trier les éléments par ordre alphabétique** : trie les éléments par leur nom.

- **Réinitialiser la barre d’outils** : restaure les paramètres et éléments par défaut de **Boîte à outils**.

- **Ajouter un onglet** : ajoute un nouvel onglet à **Boîte à outils**.

- **Monter** : déplace l’élément sélectionné vers le haut.

- **Descendre** : déplace l’élément sélectionné vers le bas.

## <a name="create-and-distribute-custom-toolbox-controls"></a>Créer et distribuer des contrôles de boîte à outils personnalisés

Vous pouvez créer des contrôles **Boîte à outils** personnalisés en commençant par un modèle de projet basé sur [Windows Presentation Foundation](../../extensibility/creating-a-wpf-toolbox-control.md) ou [Windows Forms](../../extensibility/creating-a-windows-forms-toolbox-control.md). Vous pouvez ensuite distribuer votre contrôle personnalisé à vos collègues ou le publier sur le web à l’aide du [programme d’installation de contrôles de Boîte à outils](http://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx).

## <a name="help-on-toolbox-tabs"></a>Aide sur les onglets de Boîte à outils

Les rubriques suivantes fournissent davantage d’informations sur les différents onglets **Boîte à outils** disponibles :

- [Boîte à outils, Onglet Données](../../ide/reference/toolbox-data-tab.md)
- [Boîte à outils, Onglet Composants](../../ide/reference/toolbox-components-tab.md)
- [Boîte à outils, onglet HTML](../../ide/reference/toolbox-html-tab.md)

## <a name="see-also"></a>Voir aussi

- [Choisir des éléments de boîte à outils, composants WPF](choose-toolbox-items-wpf-components.md)