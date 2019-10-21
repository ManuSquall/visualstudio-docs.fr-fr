---
title: Guide pratique pour générer plusieurs configurations simultanément | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 719b31e834b5410dd137a0c5b69cc07ae01651e3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645471"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Comment : créer plusieurs configurations simultanément
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez générer simultanément la plupart des types de projets avec une partie ou même l’ensemble de leurs configurations de build à l’aide de la boîte de dialogue **Générer en tâche de fond**. Toutefois, vous ne pouvez pas générer les types de projets suivants dans plusieurs configurations de build en même temps :

1. Applications du [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] générées pour Windows à l'aide de JavaScript.

2. Tous les projets Visual Basic.

   Pour plus d’informations sur les configurations de build, consultez [Présentation des configurations de build](../ide/understanding-build-configurations.md).

### <a name="to-build-a-project-in-multiple-build-configurations"></a>Pour générer un projet dans plusieurs configurations de build

1. Dans la barre de menus, sélectionnez **Build**, **Générer en tâche de fond**.

2. Dans la colonne **Build**, cochez les cases correspondant aux configurations dans lesquelles vous souhaitez générer un projet.

    > [!TIP]
    > Pour modifier ou créer une configuration de build pour une solution, choisissez **Build**, **Gestionnaire de configurations** dans la barre de menus pour ouvrir la boîte de dialogue **Gestionnaire de configurations**. Après avoir modifié une configuration de build pour une solution, choisissez le bouton **Régénérer** dans la boîte de dialogue **Générer en tâche de fond** pour mettre à jour toutes les configurations de build pour les projets de la solution.

3. Choisissez le bouton **Build** ou **Régénérer** pour générer le projet avec les configurations que vous avez spécifiées.

## <a name="see-also"></a>Voir aussi
 [Comment : créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md) [comprendre les configurations de build](../ide/understanding-build-configurations.md) [génération de plusieurs projets en parallèle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
