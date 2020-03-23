---
title: Guide pratique pour générer plusieurs configurations simultanément
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33cd217a08f62b4919af6d72017176c110cf5e5a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77904085"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Guide pratique pour générer plusieurs configurations simultanément

Vous pouvez générer simultanément la plupart des types de projets avec une partie ou même l’ensemble de leurs configurations de build à l’aide de la boîte de dialogue **Générer en tâche de fond**. Toutefois, vous ne pouvez pas générer les types de projets suivants dans plusieurs configurations de build en même temps :

1. Applications du [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] générées pour Windows à l'aide de JavaScript.

2. Tous les projets Visual Basic.

Si une solution contient un projet de ces deux types de projet, alors **Batch Build** n’est pas disponible pour cette solution. Dans ce cas, la commande n’apparaît pas sur le menu **Build.**

   Pour plus d’informations sur les configurations de build, consultez [Présentation des configurations de build](../ide/understanding-build-configurations.md).

## <a name="to-build-a-project-in-multiple-build-configurations"></a>Pour générer un projet dans plusieurs configurations de build

1. Sur la barre de menu, choisissez **Build** > **Batch Build**. Ou, appuyez sur **Ctrl**+**Q** pour `Batch Build`ouvrir la boîte de recherche, et la recherche de .

2. Dans la colonne **Build**, cochez les cases correspondant aux configurations dans lesquelles vous souhaitez générer un projet.

    > [!TIP]
    > Pour modifier ou créer une configuration de build pour une solution, choisissez **Build** > **Configuration Manager** sur la barre de menu pour ouvrir la boîte de dialogue Configuration **Manager.** Après avoir modifié une configuration de build pour une solution, choisissez le bouton **Régénérer** dans la boîte de dialogue **Générer en tâche de fond** pour mettre à jour toutes les configurations de build pour les projets de la solution.

3. Choisissez le bouton **Build** ou **Régénérer** pour générer le projet avec les configurations que vous avez spécifiées.

## <a name="see-also"></a>Voir aussi

- [Comment : Créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md)
- [Présentation des configurations de build](../ide/understanding-build-configurations.md)
- [Construire plusieurs projets en parallèle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)