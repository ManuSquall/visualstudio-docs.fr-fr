---
title: Fenêtre Boîte à outils
description: En savoir plus sur la fenêtre boîte à outils et sur la manière dont elle affiche les contrôles que vous pouvez ajouter aux projets Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 06/01/2020
ms.topic: reference
f1_keywords:
- vs.toolbox.general
helpviewer_keywords:
- Toolbox [Visual Studio]
- custom controls [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0a4947562eb49501e60711111d8765716cbae5c6
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112925213"
---
# <a name="toolbox"></a>Boîte à outils

La fenêtre **Boîte à outils** affiche les contrôles que vous pouvez ajouter à des projets Visual Studio. Pour ouvrir la **boîte à outils**, choisissez **Afficher**  >  la **boîte à outils** dans la barre de menus ou appuyez sur **CTRL** + **ALT** + **X**.

![Capture d’écran de la fenêtre boîte à outils montrant les options de la section conteneurs.](media/vs-2019/toolbox.png "Capture d’écran de la fenêtre boîte à outils")

Vous pouvez glisser-déplacer différents contrôles sur la surface du concepteur que vous utilisez, puis les redimensionner et les positionner.

La boîte à outils s’affiche conjointement avec les vues du concepteur, telles que le mode concepteur d’un fichier XAML ou d’un projet d’application Windows Forms. **Boîte à outils** affiche uniquement les contrôles utilisables dans le concepteur actuel. Vous pouvez rechercher des éléments dans **Boîte à outils** pour filtrer davantage les éléments qui s’affichent.

> [!NOTE]
> Pour certains types de projet, **Boîte à outils** n’affiche pas tous les éléments.

La version de .NET que cible votre projet détermine également les contrôles qui apparaissent dans la boîte à outils. Vous pouvez modifier si nécessaire la version du framework cible à partir des pages des propriétés du projet. Sélectionnez le nœud de projet dans l’**Explorateur de solutions** puis, dans la barre de menus, choisissez **Projet** > **Propriétés de nom_projet**. Sous l’onglet **Application**, utilisez le menu déroulant **Framework cible**.

::: moniker range=">=vs-2019"

![Capture d’écran de la boîte de dialogue d’application montrant les options dans la liste déroulante Framework cible.](media/vs-2019/toolbox-change-dotnet-version.png "Capture d’écran de la boîte de dialogue dans laquelle vous pouvez modifier la version .NET")

::: moniker-end

## <a name="manage-the-toolbox-window-and-its-controls"></a>Gérer la fenêtre Boîte à outils et ses contrôles

Par défaut, la **boîte à outils** est réduite le long du côté gauche de l’IDE de Visual Studio et apparaît lorsque le curseur est placé sur celle-ci. Vous pouvez épingler **Boîte à outils** (en cliquant sur l’icône **Épingler** dans la barre d’outils de Boîte à outils) afin que l’application demeure ouverte quand vous déplacez le curseur. Vous pouvez également annuler l’ancrage de la fenêtre **Boîte à outils** et la faire glisser n’importe où à l’écran. Vous pouvez masquer **Boîte à outils**, l’ancrer et annuler son ancrage ; pour ce faire, cliquez avec le bouton droit sur la barre d’outils de Boîte à outils, puis sélectionnez l’option concernée.

> [!TIP]
> Si la boîte à outils ne s’affiche plus comme étant réduite le long du côté gauche de l’IDE de Visual Studio, vous pouvez la rajouter en sélectionnant **fenêtre**  >  **Réinitialiser la disposition de fenêtre** dans la barre de menus.

Vous pouvez réorganiser les éléments d’un onglet de **boîte à outils** ou ajouter des onglets et des éléments personnalisés à l’aide des commandes suivantes du menu contextuel du clic droit :

- **Renommer l’élément** : renomme l’élément sélectionné.

- **Vue Liste** : affiche les contrôles sous forme de liste verticale. Si cette option est décochée, les contrôles apparaissent horizontalement.

- **Afficher tout** : affiche tous les contrôles possibles (pas seulement ceux qui s’appliquent au concepteur actuel).

- **Choisir les éléments** : ouvre la boîte de dialogue **Choisir des éléments de boîte à outils**, dans laquelle vous pouvez spécifier les éléments qui apparaissent dans la **boîte à outils**. Vous pouvez afficher ou masquer un élément en cochant ou en décochant sa case.

- **Trier les éléments par ordre alphabétique** : trie les éléments par nom.

- **Réinitialiser la barre d’outils** : restaure les paramètres et éléments par défaut de **Boîte à outils**.

- **Ajouter un onglet** : ajoute un nouvel onglet à **Boîte à outils**.

- **Monter** : déplace l’élément sélectionné vers le haut.

- **Descendre** : déplace l’élément sélectionné vers le bas.

## <a name="create-and-distribute-custom-toolbox-controls"></a>Créer et distribuer des contrôles de boîte à outils personnalisés

Vous pouvez créer des contrôles **Boîte à outils** personnalisés en commençant par un modèle de projet basé sur [Windows Presentation Foundation](../../extensibility/creating-a-wpf-toolbox-control.md) ou [Windows Forms](../../extensibility/creating-a-windows-forms-toolbox-control.md). Vous pouvez ensuite distribuer votre contrôle personnalisé à vos collègues ou le publier sur le web à l’aide du [programme d’installation de contrôles de Boîte à outils](https://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx).

## <a name="next-steps"></a>Étapes suivantes

Consultez les liens suivants pour en savoir plus sur certains onglets de la **boîte à outils** disponibles :

- [Boîte à outils, onglet Données](../../ide/reference/toolbox-data-tab.md)
- [Boîte à outils, onglet Composants](../../ide/reference/toolbox-components-tab.md)
- [Boîte à outils, onglet HTML](../../ide/reference/toolbox-html-tab.md)

## <a name="see-also"></a>Voir aussi

- [Choisir des éléments de boîte à outils, composants WPF](choose-toolbox-items-wpf-components.md)
