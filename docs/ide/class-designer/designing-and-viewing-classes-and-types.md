---
title: Utiliser le Concepteur de classes
description: Apprenez à concevoir, visualiser et refactoriser des classes et d’autres types dans votre code avec Concepteur de classes dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 05/08/2018
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.diagram
- vs.classdesigner.enum
helpviewer_keywords:
- Class Designer [Visual Studio]
- Class Designer, about Class Designer
- types [Visual Studio], viewing
- classes [Visual Studio], viewing
- class designer
ms.assetid: 40ed2c9d-0ce0-4b95-ad78-5dec2065ccea
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 85921343ac52c066735d607ce32635e953cf2e6a
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254786"
---
# <a name="design-and-view-classes-and-types-with-class-designer"></a>Concevoir et afficher des classes et des types avec le Concepteur de classes

Concevez, Visualisez et refactorisez des classes et d’autres types dans votre code avec **Concepteur de classes** dans Visual Studio. Utilisez les diagrammes de classes pour créer et modifier des classes dans votre projet C#, Visual Basic ou C++. Vous pouvez également utiliser des diagrammes de classes pour mieux comprendre la structure de votre projet ou réorganiser votre code.

>[!NOTE]
>Le Concepteur de classes n’est pas disponible dans les projets .NET Core.

## <a name="what-you-can-do-with-class-diagrams"></a>Ce que vous pouvez faire avec les diagrammes de classes

- **Concevoir** : modifiez le code de votre projet en changeant le diagramme de classes. Ajoutez de nouveaux éléments et supprimez ceux dont vous n'avez pas besoin. Vos changements sont répercutés dans le code.

- **Visualiser** : comprenez la structure de votre projet en affichant ses classes dans un diagramme. Personnalisez votre diagramme pour pouvoir vous concentrer sur les détails du projet qui vous intéressent le plus. Enregistrez votre diagramme pour pouvoir l'utiliser plus tard à des fins de démonstration ou de documentation.

- **Refactoriser** : substituez des méthodes, renommez des identificateurs, refactorisez des paramètres, et implémentez des interfaces et des classes abstraites.

## <a name="view-types-and-relationships"></a>Voir les types et les relations

Les diagrammes de classes affichent des informations détaillées sur les types, telles que leurs membres constitutifs et les relations entre eux. La visualisation de ces entités est une vue dynamique du code. Vous pouvez donc modifier les types dans le concepteur, puis visualiser vos modifications dans le code source de l’entité. De même, le diagramme de classes est constamment synchronisé avec les modifications apportées aux fichiers de code.

> [!NOTE]
> Si votre projet contient un diagramme de classes et référence un type qui se trouve dans un autre projet, le diagramme de classes n’affiche pas le type référencé tant que vous n’avez pas généré le projet pour ce type. De même, le diagramme n’affiche pas les modifications du code de l’entité externe tant que vous n’avez pas régénéré le projet pour cette entité.

## <a name="class-diagram-workflow"></a>Workflow des diagrammes de classes

Les diagrammes de classes peuvent vous aider à comprendre la structure de classe de projets. Ces projets peuvent avoir été créés par d’autres développeurs, ou vous avez simplement besoin d’un rappel sur un projet que vous avez créé vous-même. Vous pouvez utiliser les diagrammes de classes pour personnaliser, partager et présenter des informations de projet.

La première étape de la présentation des informations de projet consiste à créer un diagramme de classes qui affiche ce que vous souhaitez montrer. Pour plus d’informations, consultez [Ajouter un diagramme de classes](how-to-add-class-diagrams-to-projects.md). Vous pouvez créer plusieurs diagrammes de classes pour un projet, ce qui vous permet d'afficher une vue distincte du projet, une partie spécifique des types du projet ou une partie spécifique des membres de types.

En plus de définir le contenu affiché par chaque diagramme de classes, vous pouvez également changer la façon dont les informations sont présentées. Pour plus d’informations, consultez [Guide pratique pour personnaliser des diagrammes de classes](how-to-customize-class-diagrams.md).

Après avoir affiné un ou plusieurs diagrammes de classes, vous pouvez les copier dans des documents Microsoft Office et les imprimer, ou les exporter sous forme de fichiers image. Pour plus d’informations, consultez [Guide pratique pour copier les éléments d’un diagramme de classes vers un document Microsoft Office](how-to-copy-class-diagram-elements-to-a-microsoft-office-document.md), [Guide pratique pour imprimer des diagrammes de classes](how-to-print-class-diagrams.md) et [Guide pratique pour exporter des diagrammes de classes comme images](how-to-export-class-diagrams-as-images.md).

> [!NOTE]
> Le Concepteur de classes n'effectue pas le suivi de l'emplacement de vos fichiers sources. Ainsi, si vous changez la structure de votre projet ou si vous déplacez des fichiers sources du projet, le Concepteur de classes peut perdre la trace du type, en particulier le type source d'un typedef, les classes de base ou les types d'association. Vous pouvez obtenir une erreur telle que celle-ci : **Le Concepteur de classes n’est pas en mesure d’afficher ce type**. Dans ce cas, refaites glisser le code source modifié ou déplacé vers le diagramme de classes pour le réafficher.

## <a name="see-also"></a>Voir aussi

- [Fonctionnalités de l’éditeur de code](../writing-code-in-the-code-and-text-editor.md)
- [Mapper les dépendances à travers vos solutions](../../modeling/map-dependencies-across-your-solutions.md)
