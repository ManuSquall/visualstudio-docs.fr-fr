---
title: 'Comment : ajouter des diagrammes de classes aux projets (Concepteur de classes)'
ms.date: 11/04/2016
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
ms.openlocfilehash: 962df3467b8ff37a15c181a764e646ae3fb1e980
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-class-diagrams-to-projects-class-designer"></a>Guide pratique pour ajouter des diagrammes de classes aux projets (Concepteur de classes)

Pour concevoir, modifier et refactoriser des classes et d'autres types, ajoutez un diagramme de classes à votre projet C#, Visual Basic ou C++. Pour visualiser différentes parties du code d'un projet, ajoutez plusieurs diagrammes de classes à ce dernier.

Vous ne pouvez pas créer de diagrammes de classes à partir de projets qui partagent du code dans plusieurs applications. Pour créer des diagrammes de classes UML, consultez [Créer des projets et des diagrammes de modélisation UML](../../modeling/create-uml-modeling-projects-and-diagrams.md).

## <a name="to-add-a-blank-class-diagram-to-a-project"></a>Pour ajouter un diagramme de classes vide à un projet

1.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet. Choisissez **Ajouter un nouvel élément** ou **Ajouter** > **Nouvel élément**.

2.  Dans la liste des modèles, choisissez **Diagramme de classes**. Pour des projets Visual C++, regardez sous **Modèles**, puis sous **Utilitaire** pour trouver ce modèle.

     Le diagramme de classes s’ouvre dans le Concepteur de classes et apparaît comme fichier avec l’extension .cd dans l’Explorateur de solutions dans la hiérarchie de projet. Utilisez la boîte à outils Concepteur de classes pour faire glisser des formes et des lignes vers le diagramme.

3.  Pour ajouter plusieurs diagrammes de classes, répétez les étapes de la procédure.

## <a name="to-add-a-class-diagram-based-on-existing-types"></a>Pour ajouter un diagramme de classes basé sur des types existants

- Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du fichier de classe, puis choisissez **Afficher le diagramme de classes**.

     - ou -

     Dans **Affichage de classes**, ouvrez le menu contextuel de l’espace de noms ou du type, puis choisissez **Afficher le diagramme de classes**.

## <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>Pour afficher le contenu d'un projet complet dans un diagramme de classes

- Dans **l’Explorateur de solutions** ou dans Affichage de classes, cliquez avec le bouton droit sur le projet et choisissez **Afficher**, puis choisissez **Afficher le diagramme de classes**.

     Un diagramme de classes est alors créé et rempli automatiquement.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer des types à l’aide du Concepteur de classes](how-to-create-types.md)
- [Guide pratique pour afficher les types existants](how-to-view-existing-types.md)
- [Concevoir et afficher des classes et des types](designing-and-viewing-classes-and-types.md)
- [Afficher les types et les relations](viewing-types-and-relationships.md)
- [Utiliser des diagrammes de classes](working-with-class-diagrams.md)
