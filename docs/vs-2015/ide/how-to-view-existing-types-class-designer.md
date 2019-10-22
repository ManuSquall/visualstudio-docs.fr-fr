---
title: Guide pratique pour afficher des types existants (Concepteur de classes) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 925220d583695e0116fb5901d92626bfcfa7450f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670541"
---
# <a name="how-to-view-existing-types-class-designer"></a>Comment : afficher des types existants (Concepteur de classes)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour voir un type existant et ses membres, ajoutez sa forme à un diagramme de classes.

 Vous pouvez voir les types locaux et les types référencés. Un type local existe dans le projet actuellement ouvert et est disponible en lecture/écriture. Un type référencé existe dans un autre projet ou dans un assembly référencé et est en lecture seule.

 Pour concevoir de nouveaux types sur les diagrammes de classes, consultez [Guide pratique pour créer des types à l’aide du Concepteur de classes](../ide/how-to-create-types-by-using-class-designer.md).

### <a name="to-see-types-in-a-project-on-a-class-diagram"></a>Pour voir les types d'un projet dans un diagramme de classes

1. À partir d'un projet dans l'Explorateur de solutions, ouvrez un fichier de diagramme de classes (.cd) existant. Ou, s'il n'existe aucun diagramme de classes, ajoutez un nouveau diagramme de classes au projet. Consultez [Guide pratique pour ajouter des diagrammes de classes aux projets (Concepteur de classes)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).

2. À partir du projet dans l'Explorateur de solutions, faites glisser un fichier de code source vers le diagramme de classes.

   > [!WARNING]
   > Si votre solution contient un projet qui partage du code dans plusieurs applications, vous pouvez faire glisser des fichiers ou du code vers un diagramme de classes uniquement à partir des sources suivantes :
   >
   > - le projet d'application qui contient le schéma ;
   >   - un projet partagé importé par le projet d'application ;
   >   - un projet référencé ;
   >   - un assembly.

    Les formes représentant les types définis dans le fichier de code source apparaissent sur le diagramme à l'emplacement où vous avez fait glisser le fichier.

   Vous pouvez aussi afficher les types du projet en faisant glisser un ou plusieurs nœuds depuis le nœud du projet de l'Affichage de classes vers le diagramme de classes.

> [!TIP]
> Si l’Affichage de classes n’est pas ouvert, ouvrez-le depuis le menu **Affichage**. Pour plus d’informations sur l’affichage des classes, consultez [Affichage des classes et de leurs membres](https://msdn.microsoft.com/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333).

 Pour afficher les types à des emplacements par défaut du diagramme, sélectionnez un ou plusieurs types dans l’Affichage de classes, cliquez avec le bouton droit sur les types sélectionnés et choisissez **Afficher le diagramme de classes**.

> [!NOTE]
> Si un diagramme de classes fermé contenant le type existe déjà dans le projet, le diagramme de classes s'ouvre et affiche la forme du type. Toutefois, s'il n'existe dans le projet aucun diagramme de classes contenant le type, le Concepteur de classes crée un nouveau diagramme de classes dans le projet et l'ouvre pour afficher le type.

 Lorsque vous affichez un type sur le diagramme pour la première fois, sa forme apparaît réduite par défaut. Vous pouvez développer la forme pour afficher son contenu.

### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>Pour afficher le contenu d'un projet dans un diagramme de classes

1. Dans l’Explorateur de solutions ou dans Affichage de classes, cliquez avec le bouton droit sur le projet et choisissez **Afficher**, puis choisissez **Afficher le diagramme de classes**.

     Un diagramme de classes est alors créé et rempli automatiquement.

## <a name="see-also"></a>Voir aussi
 [Comment : afficher l’héritage entre les types (Concepteur de classes)](../ide/how-to-view-inheritance-between-types-class-designer.md) [Comment : personnaliser des diagrammes de classes (Concepteur de classes)](../ide/how-to-customize-class-diagrams-class-designer.md) [affichage des types et des relations (Concepteur de classes)](../ide/viewing-types-and-relationships-class-designer.md)
