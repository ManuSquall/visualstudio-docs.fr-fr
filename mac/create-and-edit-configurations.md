---
title: Création et modification des configurations de build
description: Cet article décrit la création de configurations de build dans Visual Studio pour Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: CC1B72D6-12FF-4CCC-A9D4-00F2DC14589F
ms.custom: video
ms.openlocfilehash: 26f6e25bfe1284fc31bcd484b905bf5d75c2ba15
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128422"
---
# <a name="creating-and-editing-build-configurations"></a>Création et modification des configurations de build

Les configurations de construction vous donnent un contrôle précis sur une build vous permettant de créer des configurations pour répondre à différentes situations de test et de distribution. Vous pouvez créer des configurations de construction pour des projets individuels ou à l’échelle d’une solution.

Vous pouvez créer de nouvelles configurations et modifier celles existantes pour des projets et des solutions à l’aide du dialogue Project Options.

>[!NOTE]
>Cette rubrique s’applique à Visual Studio pour Mac. Pour Visual Studio sur Windows, voir [Comment : Créer et modifier des configurations](/visualstudio/ide/how-to-create-and-edit-configurations).

## <a name="creating-a-project-build-configuration"></a>Création d’une configuration de construction de projet

Pour créer une configuration de construction de projet, suivez ces étapes :

1. Cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Options**. Vous pouvez également cliquer à deux clics sur le nœud du projet pour évoquer le dialogue Options de projet.

2. Dans la boîte de dialogue Options du projet, sélectionnez **Build > Configurations** :

    ![Gestionnaire de configurations dans les options du projet](media/create-and-edit-configurations-image2.png)

3. Sélectionnez **Ajouter** pour créer une nouvelle configuration. Vous pouvez également copier n’importe laquelle des configurations existantes.

Une fois que vous avez créé la configuration, vous pouvez utiliser la section **Build** dans les options de projet pour adapter les propriétés adaptées à votre configuration :

![Configurer les options de build](media/create-and-edit-configurations-image3.png)

## <a name="creating-a-solution-build-configuration"></a>Création d’une configuration de build de solution

Pour créer une configuration de construction de solution, suivez ces étapes :

1. Cliquez à droite sur le nœud de solution et sélectionnez **options**. Vous pouvez également cliquer à deux clics sur le nœud de solution pour faire monter le dialogue sur les options de solution.

2. Dans la boîte de dialogue Options de la solution, sélectionnez **Build > Configurations** :

    ![Gestionnaire de configurations dans les options de la solution](media/create-and-edit-configurations-image1.png)

3. Sélectionnez **Ajouter** pour créer une nouvelle configuration. Vous pouvez également copier n’importe laquelle des configurations existantes.

Une fois que vous avez créé la configuration, vous pouvez utiliser la section **Build** du dialogue Project Options pour chacun de vos projets afin d’adapter les propriétés adaptées à votre configuration :

![Configurer les options de build](media/create-and-edit-configurations-image3.png)

## <a name="renaming-a-build-configuration"></a>Renommer une configuration de construction

Pour renommer une configuration, sélectionnez-la dans la liste Configuration en naviguant vers **build > Configurations** dans le projet ou les options de solution :

![liste des configurations](media/create-and-edit-configurations-image4.png)

Sélectionnez le bouton **Renommer**.

![boîte de dialogue Renommer](media/create-and-edit-configurations-image5.png)

Ensuite, cliquez **sur OK** pour confirmer.

## <a name="related-video"></a>Vidéo associée

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Launch-Multiple-Projects/player]

## <a name="see-also"></a>Voir aussi

- [Créer et modifier des configurations de build (Visual Studio sur Windows)](/visualstudio/ide/how-to-create-and-edit-configurations)