---
title: 'Comment : générer plusieurs configurations'
ms.date: 05/13/2020
ms.technology: vs-ide-compile
ms.topic: how-to
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7820d56bcb266e8361f36cb5350475f31445800
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284760"
---
# <a name="how-to-build-multiple-configurations-in-a-single-build-request"></a>Comment : générer plusieurs configurations dans une demande de build unique

Vous pouvez générer la plupart des types de projets avec plusieurs ou même tous leurs configurations de build avec une action de l’IDE à l’aide de la boîte de dialogue **générer par lot** . Toutefois, vous ne pouvez pas générer les types de projets suivants dans plusieurs configurations de build en même temps :

1. Applications du [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] générées pour Windows à l'aide de JavaScript.

2. Tous les projets Visual Basic.

3. Projets CMake.

Si une solution contient un projet de ces deux types de projets, la **génération de lots** n’est pas disponible pour cette solution. Dans ce cas, la commande n’apparaît pas dans le menu **générer** .

   Pour plus d’informations sur les configurations de build, consultez [Présentation des configurations de build](../ide/understanding-build-configurations.md).

## <a name="to-build-a-project-in-multiple-build-configurations"></a>Pour générer un projet dans plusieurs configurations de build

1. Dans la barre de menus, choisissez **générer**  >  **génération de lots**. Ou appuyez sur **CTRL** + **Q** pour ouvrir la zone de recherche, puis recherchez `Batch Build` .

2. Dans la colonne **Build**, cochez les cases correspondant aux configurations dans lesquelles vous souhaitez générer un projet.

    > [!TIP]
    > Pour modifier ou créer une configuration de build pour une solution, choisissez **générer**  >  **Configuration Manager** dans la barre de menus pour ouvrir la boîte de dialogue **Configuration Manager** . Après avoir modifié une configuration de build pour une solution, choisissez le bouton **Régénérer** dans la boîte de dialogue **Générer en tâche de fond** pour mettre à jour toutes les configurations de build pour les projets de la solution.

3. Choisissez le bouton **Build** ou **Régénérer** pour générer le projet avec les configurations que vous avez spécifiées.

## <a name="see-also"></a>Voir aussi

- [Comment : créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md)
- [Présentation des configurations de build](../ide/understanding-build-configurations.md)
- [Générer plusieurs projets en parallèle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)