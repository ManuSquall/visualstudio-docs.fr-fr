---
title: Guide pratique pour ajouter des diagrammes de classes aux projets (Concepteur de classes)
ms.date: 05/08/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- class diagrams, creating
- Class Designer [Visual Studio], opening
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 94e13d4c1dbda200c2e2660e4b3b44e62ed99496
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="how-to-add-class-diagrams-to-projects"></a>Guide pratique pour ajouter des diagrammes de classes aux projets

Pour concevoir, modifier et refactoriser des classes et d'autres types, ajoutez un diagramme de classes à votre projet C#, Visual Basic ou C++. Pour visualiser différentes parties du code d'un projet, ajoutez plusieurs diagrammes de classes à ce dernier.

Vous ne pouvez pas créer de diagrammes de classes à partir de projets qui partagent du code dans plusieurs applications. Pour créer des diagrammes de classes UML, consultez [Créer des projets et des diagrammes de modélisation UML](../../modeling/create-uml-modeling-projects-and-diagrams.md).

## <a name="install-the-class-designer-component"></a>Installer le composant Concepteur de classes

Si vous exécutez Visual Studio 2017 et que vous n’avez pas installé le composant **Concepteur de classes**, effectuez les étapes suivantes pour l’installer.

1. Ouvrez **Programme d’installation de Visual Studio** à partir du menu Démarrer de Windows ou en sélectionnant **Outils** > **Obtenir les outils et fonctionnalités** dans la barre de menus de Visual Studio.

   Le **programme d’installation de Visual Studio** s’ouvre.

1. Sélectionnez l’onglet **Composants individuels**, puis faites défiler vers le bas jusqu’à la catégorie **Outils de code**.

1. Sélectionnez **Concepteur de classes**, puis **Modifier**.

   ![Composant Concepteur de classes dans le programme d’installation de Visual Studio](media/class-designer-component.png)

   L’installation du composant **Concepteur de classes** démarre.

## <a name="add-a-blank-class-diagram-to-a-project"></a>Ajouter un diagramme de classes vide à un projet

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de projet, puis choisissez **Ajouter** > **Nouvel élément**. Vous pouvez aussi appuyer sur **Ctrl**+**Maj**+**A**.

   La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.

2. Développez **Éléments communs** > **Général**, puis sélectionnez **Diagramme de classes** dans la liste de modèles. Pour les projets Visual C++, examinez la catégorie **Utilitaire** afin de rechercher le modèle **Diagramme de classes**.

   > [!NOTE]
   > Si vous ne voyez pas le modèle **Diagramme de classes**, [effectuez les étapes](#install-the-class-designer-component) pour installer le composant **Concepteur de classes** pour Visual Studio.

   Le diagramme de classes s’ouvre dans le Concepteur de classes et apparaît comme fichier avec l’extension *.cd* dans **l’Explorateur de solutions**. Vous pouvez faire glisser des formes et des lignes vers le diagramme à partir de la **boîte à outils**.

Pour ajouter plusieurs diagrammes de classes, répétez les étapes de la procédure.

## <a name="add-a-class-diagram-based-on-existing-types"></a>Ajouter un diagramme de classes basé sur des types existants

Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du fichier de classe, puis choisissez **Afficher le diagramme de classes**.

- ou -

Dans **Affichage de classes**, ouvrez le menu contextuel de l’espace de noms ou du type, puis choisissez **Afficher le diagramme de classes**.

## <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>Pour afficher le contenu d'un projet complet dans un diagramme de classes

Dans **l’Explorateur de solutions** ou dans Affichage de classes, cliquez avec le bouton droit sur le projet et choisissez **Afficher**, puis choisissez **Afficher le diagramme de classes**.

Un diagramme de classes est alors créé et rempli automatiquement.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer des types à l’aide du Concepteur de classes](how-to-create-types.md)
- [Guide pratique pour afficher les types existants](how-to-view-existing-types.md)
- [Concevoir et afficher des classes et des types](designing-and-viewing-classes-and-types.md)
- [Afficher les types et les relations](viewing-types-and-relationships.md)
- [Utiliser des diagrammes de classes](working-with-class-diagrams.md)
