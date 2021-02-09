---
title: Vue d’ensemble des outils de conception de modèle BDC | Microsoft Docs
description: Lisez une vue d’ensemble des outils de conception à utiliser avec un modèle de connectivité de données métiers (BDC). En savoir plus sur le concepteur BDC, la fenêtre Détails de la méthode BDC et l’Explorateur BDC.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Method_Details
- VS.SharePointTools.BDC.Explorer
- VS.SharePointTools.BDC.Diagram
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], method details
- Business Data Connectivity service [SharePoint development in Visual Studio], designer
- Business Data Connectivity service [SharePoint development in Visual Studio], method details
- BDC [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], designer
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b398d9c00caf3a4fa2ca58bafa3273673a305859
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851684"
---
# <a name="bdc-model-design-tools-overview"></a>Vue d’ensemble des outils de conception de modèle BDC
  Vous pouvez concevoir un modèle de connectivité de données métiers (BDC) à l’aide du concepteur BDC, de la fenêtre Détails de la **méthode BDC** et de l' **Explorateur BDC**.

 L' **Explorateur BDC** vous permet de parcourir le modèle, de rechercher le modèle et de définir des descripteurs de type.

## <a name="bdc-designer"></a>Concepteur BDC
 Le concepteur BDC vous permet de définir les entités dans votre modèle et d’organiser visuellement leurs relations les unes avec les autres. Utilisez le concepteur BDC pour effectuer les tâches suivantes :

- Ajoutez des entités au modèle.

- Supprimer des entités du modèle.

- Définir des relations entre des entités.

  Pour ouvrir le concepteur BDC, double-cliquez sur le fichier de modèle dans votre projet, ou ouvrez le menu contextuel du fichier de modèle, puis choisissez **ouvrir**. Ajoutez une entité au modèle en faisant glisser ou en copiant une **entité** de la **boîte à outils** vers le concepteur. Pour créer une association entre deux entités, choisissez le contrôle d' **Association** dans la **boîte à outils**, choisissez la première entité, puis choisissez la deuxième entité.

## <a name="bdc-method-details-window"></a>Fenêtre Détails de la méthode BDC
 Utilisez la fenêtre Détails de la **méthode BDC** pour définir les paramètres, les instances et les descripteurs de filtre d’une méthode.

 Vous pouvez générer rapidement des méthodes de recherche, de recherche, de création, de mise à jour et de suppression spécifiques dans la fenêtre Détails de la **méthode BDC** . Quand vous générez ces méthodes, Visual Studio ajoute des métadonnées, telles que des paramètres, des instances et des descripteurs de type, à la méthode. Vous pouvez modifier ces métadonnées pour répondre à votre scénario spécifique.

 Pour ouvrir la fenêtre Détails de la **méthode BDC** , dans la barre de menus, choisissez **Afficher**  >  **les autres** détails de la  >  **méthode BDC** Windows.

 Pour afficher les méthodes dans la fenêtre **Détails de méthode BDC** , choisissez l’entité dans le concepteur BDC. Les méthodes de l’entité sélectionnée s’affichent dans la fenêtre Détails de la **méthode BDC** . Si vous ne choisissez pas une entité dans le concepteur BDC, la fenêtre Détails de la **méthode BDC** n’affiche aucune information.

 Développez ou réduisez des nœuds dans la fenêtre Détails de la **méthode BDC** pour définir des paramètres, des instances et des descripteurs de filtre. Utilisez l' **Explorateur BDC** pour définir des descripteurs de type.

## <a name="bdc-explorer"></a>explorateur BDC
 L' **Explorateur BDC** affiche les éléments qui composent le modèle. Pour ouvrir l' **Explorateur BDC**, dans la barre de menus, choisissez **Afficher**  >  **autre**  >  **Explorateur BDC** Windows. Pour parcourir le modèle, développez les nœuds dans l' **Explorateur BDC**. Chaque nœud représente un élément dans le XML du fichier de modèle.

 Lorsque vous choisissez des nœuds dans l' **Explorateur BDC**, les propriétés de chaque nœud que vous choisissez s’affichent dans la fenêtre **Propriétés** . La plupart de ces propriétés correspondent aux attributs du fichier de modèle. Vous pouvez effectuer une recherche dans le modèle à l’aide de la zone de recherche située en haut de l' **Explorateur BDC**.

> [!NOTE]
> L' **Explorateur BDC** n’affiche pas les identificateurs, les propriétés personnalisées, les chaînes localisées, les groupes d’associations, les actions, les descripteurs de filtre, les listes de contrôle d’action et les valeurs de paramètre par défaut.

### <a name="define-type-descriptors"></a>Définir des descripteurs de type
 Utilisez l' **Explorateur BDC** pour définir des descripteurs de type. L’Explorateur BDC vous permet de définir un descripteur de type une fois, puis de réutiliser ce descripteur de type à un autre emplacement de votre modèle. Pour ce faire, copiez un descripteur de type et collez-le dans tout autre paramètre ou descripteur de type.

> [!NOTE]
> Les modifications apportées à un descripteur de type d’origine n’affectent pas les copies de ce descripteur de type.

 Pour plus d’informations, consultez [Comment : définir le descripteur de type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>Voir aussi
- [Comment : créer un modèle BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Comment : ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)
- [Comment : ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Comment : ajouter une méthode Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)
- [Comment : ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)
- [Créer une association entre des entités](../sharepoint/creating-an-association-between-entities.md)
- [Procédure pas à pas : création d’une liste externe dans SharePoint à l’aide de données d’entreprise](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
- [Intégrer des données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
- [Création d’un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Conception d’un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)
