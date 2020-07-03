---
title: Création et modification des configurations de build
description: Cet article décrit la création de configurations de build dans Visual Studio pour Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: CC1B72D6-12FF-4CCC-A9D4-00F2DC14589F
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: eb3ceed624e3bbba67564bb8f7c359841c0e496d
ms.sourcegitcommit: 2ce59c2ffeba5ba7f628c2e6c75cba4731deef8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85939180"
---
# <a name="creating-and-editing-build-configurations"></a>Création et modification des configurations de build

Les configurations de build vous permettent de contrôler précisément une build, ce qui vous permet de créer des configurations pour répondre à différentes situations de test et de distribution. Vous pouvez créer des configurations de build pour des projets individuels ou à l’échelle d’une solution.

Vous pouvez créer des configurations et modifier celles qui existent déjà pour les projets et les solutions à l’aide de la boîte de dialogue Options du projet.

>[!NOTE]
>Cette rubrique s’applique à Visual Studio pour Mac. Pour Visual Studio sur Windows, consultez [Comment : créer et modifier des configurations](/visualstudio/ide/how-to-create-and-edit-configurations).

## <a name="creating-a-project-build-configuration"></a>Création d’une configuration de build de projet

Pour créer une configuration de build de projet, procédez comme suit :

1. Cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Options**. Vous pouvez également double-cliquer sur le nœud du projet pour afficher la boîte de dialogue Options du projet.

2. Dans la boîte de dialogue Options du projet, sélectionnez **Build > Configurations** :

    ![Gestionnaire de configurations dans les options du projet](media/create-and-edit-configurations-image2.png)

3. Sélectionnez **Ajouter** pour créer une nouvelle configuration. Vous pouvez également copier n’importe quelle configuration existante.

Une fois que vous avez créé la configuration, vous pouvez utiliser la section **Build** dans les options de projet pour adapter les propriétés appropriées à votre configuration :

![Configurer les options de build](media/create-and-edit-configurations-image3.png)

## <a name="creating-a-solution-build-configuration"></a>Création d’une configuration de build de solution

Pour créer une configuration de build de solution, procédez comme suit :

1. Cliquez avec le bouton droit sur le nœud de la solution et sélectionnez **options**. Vous pouvez également double-cliquer sur le nœud de la solution pour afficher la boîte de dialogue Options de la solution.

2. Dans la boîte de dialogue Options de la solution, sélectionnez **Build > Configurations** :

    ![Gestionnaire de configurations dans les options de la solution](media/create-and-edit-configurations-image1.png)

3. Sélectionnez **Ajouter** pour créer une nouvelle configuration. Vous pouvez également copier n’importe quelle configuration existante.

Une fois que vous avez créé la configuration, vous pouvez utiliser la section **générer** de la boîte de dialogue Options du projet pour chacun de vos projets afin d’adapter les propriétés appropriées à votre configuration :

![Configurer les options de build](media/create-and-edit-configurations-image3.png)

## <a name="renaming-a-build-configuration"></a>Attribution d’un nouveau nom à une configuration de build

Pour renommer une configuration, sélectionnez-la dans la liste Configuration en accédant à **générer > configurations** dans les options du projet ou de la solution :

![liste des configurations](media/create-and-edit-configurations-image4.png)

Sélectionnez le bouton **Renommer**.

![boîte de dialogue Renommer](media/create-and-edit-configurations-image5.png)

Cliquez ensuite sur **OK** pour confirmer.

## <a name="related-video"></a>Vidéo associée

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Launch-Multiple-Projects/player]

## <a name="see-also"></a>Voir aussi

- [Créer et modifier des configurations de build (Visual Studio sur Windows)](/visualstudio/ide/how-to-create-and-edit-configurations)