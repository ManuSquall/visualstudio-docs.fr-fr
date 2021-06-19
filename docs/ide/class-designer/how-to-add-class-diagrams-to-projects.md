---
title: Ajouter des diagrammes de classes aux projets (Concepteur de classes)
description: Apprenez à concevoir, modifier et refactoriser des classes et d’autres types, ajoutez un diagramme de classes à votre projet C#, Visual Basic ou C++.
ms.custom: SEO-VS-2020
ms.date: 05/08/2018
ms.topic: how-to
helpviewer_keywords:
- class diagrams, creating
- Class Designer [Visual Studio], opening
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0af2717efec7cab8594f193c06e8813bd556b01f
ms.sourcegitcommit: c3713f284c4fe10b10996d5eb67077ddd8641424
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112375784"
---
# <a name="how-to-add-class-diagrams-to-projects"></a>Guide pratique pour ajouter des diagrammes de classes aux projets

Pour concevoir, modifier et refactoriser des classes et d'autres types, ajoutez un diagramme de classes à votre projet C#, Visual Basic ou C++. Pour visualiser différentes parties du code d'un projet, ajoutez plusieurs diagrammes de classes à ce dernier.

Vous ne pouvez pas créer de diagrammes de classes à partir de projets qui partagent du code dans plusieurs applications. Pour créer des diagrammes de classes UML, consultez [Créer des projets et des diagrammes de modélisation UML](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

## <a name="install-the-class-designer-component"></a>Installer le composant Concepteur de classes

Si vous n’avez pas installé le composant **Concepteur de classes**, effectuez les étapes suivantes pour le faire.

1. Ouvrez **Programme d’installation de Visual Studio** à partir du menu Démarrer de Windows ou en sélectionnant **Outils** > **Obtenir les outils et fonctionnalités** dans la barre de menus de Visual Studio.

   Le **programme d’installation de Visual Studio** s’ouvre.

1. Sélectionnez l’onglet **Composants individuels**, puis faites défiler vers le bas jusqu’à la catégorie **Outils de code**.

1. Sélectionnez **Concepteur de classes**, puis **Modifier**.

   ![Composant Concepteur de classes dans le programme d’installation de Visual Studio](media/class-designer-component.png)

   L’installation du composant **Concepteur de classes** démarre.

## <a name="add-a-blank-class-diagram-to-a-project"></a>Ajouter un diagramme de classes vide à un projet

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de projet, puis choisissez **Ajouter** > **Nouvel élément**. Ou appuyez sur **CTRL** + **MAJ** + **A**.

   La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.

2. Développez **éléments communs**  >  **général**, puis sélectionnez **diagramme de classes** dans la liste modèle. Pour les projets Visual C++, examinez la catégorie **Utilitaire** afin de rechercher le modèle **Diagramme de classes**.

   > [!NOTE]
   > Si vous ne voyez pas le modèle **Diagramme de classes**, [effectuez les étapes](#install-the-class-designer-component) pour installer le composant **Concepteur de classes** pour Visual Studio.

   Le diagramme de classes s’ouvre dans le Concepteur de classes et apparaît comme fichier avec l’extension *.cd* dans **l’Explorateur de solutions**. Vous pouvez faire glisser des formes et des lignes vers le diagramme à partir de la **boîte à outils**.

Pour ajouter plusieurs diagrammes de classes, répétez les étapes de la procédure.

## <a name="add-a-class-diagram-based-on-existing-types"></a>Ajouter un diagramme de classes basé sur des types existants

Dans **l’Explorateur de solutions**, ouvrez le menu contextuel d’un fichier de classe (clic droit), puis choisissez **Afficher le diagramme de classes**.

-ou-

Dans **Affichage de classes**, ouvrez le menu contextuel de l’espace de noms ou du type, puis choisissez **Afficher le diagramme de classes**.

> [!TIP]
> Si **affichage de classes** n’est pas ouvert, ouvrez **affichage de classes** à partir du menu **affichage** .

## <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>Pour afficher le contenu d'un projet complet dans un diagramme de classes

Dans **Explorateur de solutions** ou affichage de classes, cliquez avec le bouton droit sur le projet et choisissez **Afficher**, puis choisissez **afficher le diagramme de classes**.

Un diagramme de classes est alors créé et rempli automatiquement.

> [!NOTE]
> Le Concepteur de classes n’est pas disponible dans les projets .NET Core.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer des types à l’aide du Concepteur de classes](how-to-create-types.md)
- [Comment : afficher les types existants](how-to-view-existing-types.md)
- [Concevoir et afficher des classes et des types](designing-and-viewing-classes-and-types.md)
