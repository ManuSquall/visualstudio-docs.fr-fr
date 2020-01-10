---
title: 'Comment : afficher des types existants (Concepteur de classes)'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 04b109bfa5741a5d4349f2d503bd1c821e19029d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588705"
---
# <a name="how-to-view-existing-types-in-class-designer"></a>Guide pratique pour afficher des types existants dans le Concepteur de classes

Pour voir un type existant et ses membres, ajoutez sa forme à un diagramme de classes.

Vous pouvez voir les types locaux et les types référencés. Un type local existe dans le projet actuellement ouvert et est disponible en lecture/écriture. Un type référencé existe dans un autre projet ou dans un assembly référencé et est en lecture seule.

Pour concevoir de nouveaux types sur les diagrammes de classes, consultez [Guide pratique pour créer des types à l’aide du Concepteur de classes](how-to-create-types.md).

## <a name="to-see-types-in-a-project-on-a-class-diagram"></a>Pour voir les types d'un projet dans un diagramme de classes

1. À partir d’un projet dans **l’Explorateur de solutions**, ouvrez un fichier de diagramme de classes (.cd) existant. Ou, s'il n'existe aucun diagramme de classes, ajoutez un nouveau diagramme de classes au projet. Consultez [Guide pratique pour ajouter des diagrammes de classes aux projets](how-to-add-class-diagrams-to-projects.md).

2. À partir du projet dans **l’Explorateur de solutions**, faites glisser un fichier de code source vers le diagramme de classes.

    > [!NOTE]
    > Si votre solution contient un projet qui partage du code dans plusieurs applications, vous pouvez faire glisser des fichiers ou du code vers un diagramme de classes uniquement à partir des sources suivantes :
    >
    > - le projet d'application qui contient le schéma ;
    > - un projet partagé importé par le projet d'application ;
    > - un projet référencé ;
    > - un assembly.

    Les formes représentant les types définis dans le fichier de code source apparaissent sur le diagramme à l'emplacement où vous avez fait glisser le fichier.

Vous pouvez aussi afficher les types du projet en faisant glisser un ou plusieurs nœuds à partir du nœud du projet de **l’Affichage de classes** vers le diagramme de classes.

> [!TIP]
> Si **l’Affichage de classes** n’est pas ouvert, ouvrez **l’Affichage de classes** à partir du menu **Affichage**.

Pour afficher les types à des emplacements par défaut du diagramme, sélectionnez un ou plusieurs types dans **l’Affichage de classes**, cliquez avec le bouton droit sur les types sélectionnés et choisissez **Afficher le diagramme de classes**.

> [!NOTE]
> Si un diagramme de classes fermé contenant le type existe déjà dans le projet, le diagramme de classes s'ouvre et affiche la forme du type. Toutefois, s’il n’existe dans le projet aucun diagramme de classes contenant le type, le **Concepteur de classes** crée un diagramme de classes dans le projet et l’ouvre pour afficher le type.

Lorsque vous affichez un type sur le diagramme pour la première fois, sa forme apparaît réduite par défaut. Vous pouvez développer la forme pour afficher son contenu.

### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>Pour afficher le contenu d'un projet dans un diagramme de classes

Dans **l’Explorateur de solutions** ou dans **Affichage de classes**, cliquez avec le bouton droit sur le projet et choisissez **Afficher**, puis **Afficher le diagramme de classes**. Un diagramme de classes est alors créé et rempli automatiquement.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour afficher l’héritage entre des types](how-to-view-inheritance-between-types.md)
- [Guide pratique pour personnaliser des diagrammes de classes](how-to-customize-class-diagrams.md)
- [Affichage des types et des relations](designing-and-viewing-classes-and-types.md)
