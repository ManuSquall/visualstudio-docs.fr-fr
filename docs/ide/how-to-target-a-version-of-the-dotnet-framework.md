---
title: Cibler une version du .NET Framework
ms.date: 03/21/2019
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- .NET Framework version [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ba8bdcade321c3660e89ab6b7cf6e0b79471b393
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58355390"
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Procédure : Cibler une version du .NET Framework

Cet article explique comment cibler une version du .NET Framework quand vous créez un projet. Il décrit également comment changer la version ciblée dans un projet Visual Basic, C#, ou F# existant.

> [!IMPORTANT]
> Pour plus d’informations sur la modification de la version cible pour les projets C++, consultez [Guide pratique pour modifier l’infrastructure cible et l’ensemble d’outils de plateforme](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

## <a name="target-a-version-when-you-create-a-project"></a>Cibler une version quand vous créez un projet

Quand vous créez un projet, les versions du .NET Framework disponibles dépendent des versions installées et du modèle de projet sélectionné.

1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet**.

1. Choisissez un modèle pour le type de projet que vous voulez créer. Entrez un nom pour le projet.

1. Dans la liste déroulante **Framework** située en bas de la boîte de dialogue, choisissez la version du .NET Framework que votre projet doit cibler.

   La liste des frameworks affiche uniquement les versions qui s’appliquent au modèle que vous avez choisi. Certains types de projets, tels que .NET Core, ne nécessitent pas .NET Framework. Dans ce cas, la liste déroulante **Framework** est masquée.

   ::: moniker range="vs-2017"

   ![Liste déroulante Framework dans la boîte de dialogue Nouveau projet](media/vside-newproject-framework.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Sélecteur de framework dans Visual Studio 2019](media/vs-2019/configure-new-project-framework.png)

   ::: moniker-end

1. Continuez avec [la création du projet](create-new-project.md).

## <a name="change-the-targeted-version"></a>Changer la version ciblée

Vous pouvez changer la version ciblée du .NET Framework dans un projet Visual Basic, C# ou F# en suivant cette procédure.

1. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du projet que vous souhaitez modifier, puis choisissez **Propriétés**.

    ![Propriétés de l'Explorateur de solutions dans Visual Studio](../ide/media/vs_slnexplorer_properties.png)

1. Dans la colonne gauche de la fenêtre **Propriétés**, choisissez l’onglet **Application**.

    ![Onglet Propriétés de la fenêtre Propriétés de l'application Visual Studio](../ide/media/vs_slnexplorer_properties_applicationtab.png)

    > [!NOTE]
    > Après avoir créé une application UWP, vous ne pouvez pas modifier la version ciblée de Windows ou du .NET Framework.

1. Dans la liste **Framework cible**, choisissez la version que vous souhaitez.

1. Dans la boîte de dialogue de vérification qui apparaît, choisissez le bouton **Oui**.

    Le projet est alors déchargé. Lorsqu'il se recharge, il cible la version du . NET Framework que vous venez de choisir.

    > [!NOTE]
    > Si votre code contient des références à une autre version du .NET Framework que celui que vous avez ciblé, des messages d'erreur peuvent s'afficher lorsque vous compilez et exécutez le code. Pour résoudre ces erreurs, vous devez modifier les références. Consultez [Résoudre les problèmes liés aux erreurs de ciblage du .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du multiciblage Visual Studio](../ide/visual-studio-multi-targeting-overview.md)
- [Résoudre les problèmes liés aux erreurs de ciblage du .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)
- [Application, page du Concepteur de projet (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Application, page du Concepteur de projet (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Guide pratique pour modifier l’infrastructure cible et l’ensemble d’outils de plateforme (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)