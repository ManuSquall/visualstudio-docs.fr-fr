---
title: 'Comment : ajouter et supprimer des dépendances de fonctionnalités | Microsoft Docs'
description: Consultez Comment ajouter et supprimer des dépendances de fonctionnalités à votre solution SharePoint à l’aide du concepteur de fonctionnalités dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW
- VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5011db32123e77e9bf60c99459125302b2bf8264
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915360"
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>Comment : ajouter et supprimer des dépendances de fonctionnalités
  Votre fonctionnalité SharePoint peut dépendre d’autres fonctionnalités de fonctionnalités ou de données. Dans ce cas, vous pouvez marquer ces autres fonctionnalités en tant que dépendances de votre fonctionnalité. De cette façon, le serveur SharePoint s’assure que les fonctionnalités dépendantes sont activées avant que votre fonctionnalité soit activée.

## <a name="add-dependencies"></a>Ajout de dépendances
 Vous pouvez ajouter d’autres fonctionnalités de votre solution en tant que dépendances. De cette façon, vous pouvez vous assurer que les fonctionnalités requises sont installées et activées avant l’installation de votre fonctionnalité.

#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>Pour ajouter une dépendance à une fonctionnalité dans la solution

1. Ouvrez le concepteur de fonctionnalités, développez le nœud **dépendances d’activation des fonctionnalités** , puis cliquez sur le bouton **Ajouter** .

2. Dans la boîte de dialogue **Ajouter des dépendances d’activation de fonctionnalité** , sélectionnez la case d’option **Ajouter une dépendance aux fonctionnalités dans la solution** , choisissez le titre de la fonctionnalité que vous souhaitez ajouter en tant que dépendance, puis cliquez sur le bouton **Ajouter** .

     Vous pouvez ajouter plusieurs fonctionnalités en choisissant plusieurs titres tout en appuyant sur la touche **CTRL** .

## <a name="addi-custom-dependencies"></a>Dépendances personnalisées addi
 Vous pouvez ajouter des fonctionnalités qui sont déjà déployées sur un serveur SharePoint en tant que dépendance. De cette façon, le processus d’activation de SharePoint s’assure que toutes les fonctionnalités dépendantes sont activées avant l’installation de votre fonctionnalité.

#### <a name="to-add-a-dependency-by-the-feature-id"></a>Pour ajouter une dépendance à l’aide de l’ID de fonctionnalité

1. Ouvrez le concepteur de fonctionnalités, développez le nœud **dépendances d’activation des fonctionnalités** , puis cliquez sur le bouton **Ajouter** .

2. Dans la boîte de dialogue **Ajouter des dépendances d’activation de fonctionnalité** , choisissez la case d’option **Ajouter une dépendance personnalisée** .

3. Dans la zone de texte **ID de fonctionnalité** , entrez le GUID de la fonctionnalité que vous souhaitez marquer comme dépendance d’activation, puis cliquez sur le bouton **Ajouter** .

## <a name="edit-custom-dependencies"></a>Modifier les dépendances personnalisées
 Vous pouvez modifier les dépendances personnalisées que vous avez ajoutées précédemment. Toutefois, les fonctionnalités dépendantes qui se trouvent dans votre solution ne peuvent être supprimées et non modifiées.

#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>Pour modifier une dépendance sur une fonctionnalité dans la solution

1. Ouvrez le concepteur de fonctionnalités, puis développez le nœud **dépendances d’activation de fonctionnalité** .

2. Choisissez le nom de la fonctionnalité que vous souhaitez modifier, puis cliquez sur le bouton **modifier** .

3. Dans la boîte de dialogue **modifier la dépendance d’activation de fonctionnalité personnalisée** , modifiez le titre, l’ID de la fonctionnalité ou la description, puis choisissez le bouton **Envoyer** .

## <a name="remove-dependencies"></a>Supprimer les dépendances

#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>Pour supprimer une dépendance sur une fonctionnalité dans la solution

1. Dans le concepteur de fonctionnalités, développez le nœud **dépendances d’activation des fonctionnalités** , choisissez le nom de la fonctionnalité que vous souhaitez supprimer, puis choisissez le bouton **supprimer** .

## <a name="see-also"></a>Voir aussi
- [Créer des fonctionnalités SharePoint](../sharepoint/creating-sharepoint-features.md)
- [Comment : personnaliser une fonctionnalité SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Comment : ajouter et supprimer des éléments dans des fonctionnalités SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
