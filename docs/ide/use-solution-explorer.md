---
title: En savoir plus sur la fenêtre outil Explorateur de solutions
description: découvrez comment vous pouvez utiliser la fenêtre outil Explorateur de solutions dans Visual Studio pour créer & gérer vos fichiers, projets et solutions.
ms.date: 06/29/2021
ms.topic: conceptual
f1_keywords:
- vs.addnewitem
helpviewer_keywords:
- solution explorer [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fbbae8b974a7e88abffd9a12eb253dfea6c7165b
ms.sourcegitcommit: 8fb1500acb7e6314fbb6b78eada78ef5d61d39bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2021
ms.locfileid: "113280494"
---
# <a name="how-to-use-solution-explorer"></a>Comment utiliser Explorateur de solutions

Vous pouvez utiliser la fenêtre outil Explorateur de solutions pour créer & gérer vos solutions et projets, et pour afficher & interagir avec votre code. Dans cet article, nous allons détailler les options d’interface utilisateur qui vous permettent de le faire.

> [!NOTE]
> Cette rubrique s’applique uniquement à Visual Studio sur Windows.

## <a name="solution-explorer-tool-window"></a>Explorateur de solutions fenêtre outil

pour commencer, jetons un coup d’œil à la fenêtre outil Explorateur de solutions dans l' [IDE Visual Studio](../get-started/visual-studio-ide.md), avec une Solution de console C# ouverte qui comporte deux projets.

[![La fenêtre outil Explorateur de solutions dans Visual Studio.](media/solution-explorer-tool-window.png)](media/solution-explorer-tool-window.png#lightbox)

La fenêtre outil contient les éléments d’interface utilisateur suivants :

- **Barre de menus**, dans laquelle vous pouvez contrôler l’apparence de vos fichiers
- **Barre de recherche**, dans laquelle vous pouvez rechercher des fichiers et des types de fichiers spécifiques
- **Fenêtre principale**, dans laquelle vous pouvez afficher et gérer vos fichiers, projets, & solutions
- **Nœud** de la solution, où vous pouvez gérer vos solutions
- **nœud Project**, où vous pouvez gérer vos projets
- **Nœud dépendances**, dans lequel vous pouvez gérer votre solution & les dépendances du projet
- **Nœud de programme**, dans lequel vous pouvez afficher, modifier et gérer votre programme ou votre application (application)
- **[onglet modifications git](../version-control/git-with-visual-studio.md?view=vs-2019&preserve-view=true#git-changes-window)**, dans lequel vous pouvez utiliser git & GitHub dans Visual Studio pour collaborer sur des projets avec votre équipe

> [!TIP]
> si vous ne voyez pas la fenêtre outil Explorateur de solutions, vous pouvez l’ouvrir à partir de la barre de menus Visual Studio à l’aide de l’option **afficher** le  >  **Explorateur de solutions**, ou en appuyant sur **Ctrl** + **Alt** + **L**.

## <a name="solution-explorer-menu-bar"></a>Barre de menus Explorateur de solutions

Pour continuer, examinons de plus près la barre de menus Explorateur de solutions.

![Barre de menus Explorateur de solutions dans Visual Studio.](media/solution-explorer-menu-bar.png)

La barre de menus contient les éléments d’interface utilisateur suivants, de gauche à droite :

- Bouton **précédent** , pour basculer entre les résultats de la recherche
- Bouton **suivant** , pour basculer entre les résultats de la recherche
- Bouton d' **hébergement** pour revenir à l’affichage par défaut
- Bouton **bascule** pour basculer entre les solutions et les vues disponibles
- Bouton du **filtre des modifications en attente** & menu déroulant pour afficher les fichiers ouverts ou les fichiers avec des modifications en attente
- Bouton **synchroniser avec le document actif** pour rechercher un fichier à partir de l’éditeur de code
- Bouton **Actualiser** qui apparaît uniquement lorsque vous sélectionnez une dépendance, telle qu’une fonction ou un package
- Bouton **réduire tout** , pour réduire l’affichage des fichiers dans la fenêtre principale
- Bouton **Afficher tous les fichiers** , pour afficher tous les fichiers, y compris les [projets déchargés](filtered-solutions.md#toggle-unloaded-project-visibility)
- Bouton **Propriétés** , pour afficher et modifier les paramètres de fichiers et de composants spécifiques
- Bouton **aperçu des éléments sélectionnés** , pour afficher un fichier ou un composant sélectionné dans l’éditeur de code

### <a name="solution-explorer-right-click-context-menu"></a>Explorateur de solutions menu contextuel, cliquez avec le bouton droit sur

Dans Explorateur de solutions, il existe plusieurs propriétés de fichier avec lesquelles vous pouvez interagir en utilisant le menu contextuel. Pour plus d’informations sur les options du menu contextuel avec le bouton droit, consultez la page [gérer les propriétés du projet et de la solution](managing-project-and-solution-properties.md) .

## <a name="see-also"></a>Voir aussi

- [Que sont les solutions et les projets dans Visual Studio ?](solutions-and-projects-in-visual-studio.md)
- [Personnalisation des dispositions de fenêtres dans Visual Studio](customizing-window-layouts-in-visual-studio.md)
