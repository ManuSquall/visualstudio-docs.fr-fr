---
title: 'Comment : afficher des types existants (Concepteur de classes)'
description: Découvrez comment voir un type existant et ses membres en ajoutant sa forme à un diagramme de classes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 6b4660c4efc7c22431b7c9f0d9180576d524a372
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901165"
---
# <a name="how-to-view-existing-types-in-class-designer"></a>Guide pratique pour afficher des types existants dans le Concepteur de classes

Pour voir un type existant et ses membres, ajoutez sa forme à un diagramme de classes.

Vous pouvez voir les types locaux et les types référencés. Un type local existe dans le projet actuellement ouvert et est disponible en lecture/écriture. Un type référencé existe dans un autre projet ou dans un assembly référencé et est en lecture seule.

Pour concevoir de nouveaux types sur des diagrammes de classes, consultez [Comment : créer des types à l’aide de concepteur de classes](how-to-create-types.md).

## <a name="to-see-types-in-a-project-on-a-class-diagram"></a>Pour voir les types d'un projet dans un diagramme de classes

1. À partir d’un projet dans **Explorateur de solutions**, ouvrez un fichier de diagramme de classes (. CD) existant. Ou, s'il n'existe aucun diagramme de classes, ajoutez un nouveau diagramme de classes au projet. Consultez [Comment : ajouter des diagrammes de classes aux projets](how-to-add-class-diagrams-to-projects.md).

2. À partir du projet dans **Explorateur de solutions**, faites glisser un fichier de code source vers le diagramme de classes.

    > [!NOTE]
    > Si votre solution contient un projet qui partage du code dans plusieurs applications, vous pouvez faire glisser des fichiers ou du code vers un diagramme de classes uniquement à partir des sources suivantes :
    >
    > - le projet d'application qui contient le schéma ;
    > - un projet partagé importé par le projet d'application ;
    > - un projet référencé ;
    > - un assembly.

    Les formes représentant les types définis dans le fichier de code source apparaissent sur le diagramme à l'emplacement où vous avez fait glisser le fichier.

Vous pouvez également afficher les types du projet en faisant glisser un ou plusieurs types du nœud de projet dans **affichage de classes** vers le diagramme de classes.

> [!TIP]
> Si **affichage de classes** n’est pas ouvert, ouvrez **affichage de classes** à partir du menu **affichage** .

Pour afficher les types à des emplacements par défaut sur le diagramme, sélectionnez un ou plusieurs types dans **affichage de classes**, cliquez avec le bouton droit sur les types sélectionnés, puis choisissez **afficher le diagramme de classes**.

> [!NOTE]
> Si un diagramme de classes fermé contenant le type existe déjà dans le projet, le diagramme de classes s'ouvre et affiche la forme du type. Toutefois, si aucun diagramme de classes contenant le type n’existe dans le projet, **Concepteur de classes** crée un nouveau diagramme de classes dans le projet et l’ouvre pour afficher le type.

Lorsque vous affichez un type sur le diagramme pour la première fois, sa forme apparaît réduite par défaut. Vous pouvez développer la forme pour afficher son contenu.

### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>Pour afficher le contenu d'un projet dans un diagramme de classes

Dans **Explorateur de solutions** ou **affichage de classes**, cliquez avec le bouton droit sur le projet et choisissez **Afficher**, puis choisissez **afficher le diagramme de classes**. Un diagramme de classes est alors créé et rempli automatiquement.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour afficher l’héritage entre des types](how-to-view-inheritance-between-types.md)
- [Comment : personnaliser des diagrammes de classes](how-to-customize-class-diagrams.md)
- [Affichage des types et des relations](designing-and-viewing-classes-and-types.md)
