---
title: 'Comment : ajouter des diagrammes de classes aux projets (Concepteur de classes)'
ms.date: 05/08/2018
ms.topic: conceptual
helpviewer_keywords:
- class diagrams, creating
- Class Designer [Visual Studio], opening
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87a6c1e996d820724138b6bf38c6440193a4c26b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588835"
---
# <a name="how-to-add-class-diagrams-to-projects"></a>Guide pratique pour ajouter des diagrammes de classes aux projets

Pour concevoir, modifier et refactoriser des classes et d'autres types, ajoutez un diagramme de classes à votre projet C#, Visual Basic ou C++. Pour visualiser différentes parties du code d'un projet, ajoutez plusieurs diagrammes de classes à ce dernier.

Vous ne pouvez pas créer de diagrammes de classes à partir de projets qui partagent du code dans plusieurs applications. Pour créer des diagrammes de classes UML, consultez [Créer des projets et des diagrammes de modélisation UML](../../modeling/what-s-new-for-design-in-visual-studio.md).

## <a name="install-the-class-designer-component"></a>Installer le composant Concepteur de classes

Si vous n’avez pas installé le composant **Concepteur de classes**, effectuez les étapes suivantes pour le faire.

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

Dans **l’Explorateur de solutions**, ouvrez le menu contextuel d’un fichier de classe (clic droit), puis choisissez **Afficher le diagramme de classes**.

\- ou -

Dans **Affichage de classes**, ouvrez le menu contextuel de l’espace de noms ou du type, puis choisissez **Afficher le diagramme de classes**.

> [!TIP]
> Si **l’Affichage de classes** n’est pas ouvert, ouvrez **l’Affichage de classes** à partir du menu **Affichage**.

## <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>Pour afficher le contenu d'un projet complet dans un diagramme de classes

Dans **l’Explorateur de solutions** ou dans Affichage de classes, cliquez avec le bouton droit sur le projet et choisissez **Afficher**, puis choisissez **Afficher le diagramme de classes**.

Un diagramme de classes est alors créé et rempli automatiquement.

> [!NOTE]
> Le Concepteur de classes n’est pas disponible dans les projets .NET Core.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer des types à l’aide du Concepteur de classes](how-to-create-types.md)
- [Guide pratique pour afficher les types existants](how-to-view-existing-types.md)
- [Concevoir et afficher des classes et des types](designing-and-viewing-classes-and-types.md)
