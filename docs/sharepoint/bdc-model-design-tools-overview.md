---
title: Vue d’ensemble des outils de conception du modèle BDC | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 533a49db6e528ba75da9cbe232e7875413ed0724
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871488"
---
# <a name="bdc-model-design-tools-overview"></a>Vue d’ensemble des outils de conception de modèle BDC
  Vous pouvez concevoir un modèle de connectivité de données métiers (BDC) en utilisant le concepteur BDC, le **détails de méthode BDC** fenêtre et le **Explorateur BDC**.  
  
 Le **Explorateur BDC** vous permet de parcourir le modèle, de rechercher le modèle et de définir les descripteurs de type.  
  
## <a name="bdc-designer"></a>Concepteur BDC
 Le concepteur BDC vous permet de définir les entités dans votre modèle et regrouper visuellement leurs relations entre eux. Utilisez le concepteur BDC pour effectuer les tâches suivantes :  
  
- Ajouter des entités au modèle.  
  
- Supprimer des entités du modèle.  
  
- Définir des relations entre des entités.  
  
  Pour ouvrir le concepteur BDC, double-cliquez sur le fichier de modèle dans votre projet, ou ouvrez le menu contextuel pour le fichier de modèle, puis choisissez **ouvrir**. Ajouter une entité au modèle en faisant glisser ou en copiant un **entité** à partir de la **boîte à outils** sur le concepteur. Pour créer une association entre deux entités, choisissez le **Association** dans contrôler le **boîte à outils**, choisissez la première entité, puis la deuxième entité.  
  
## <a name="bdc-method-details-window"></a>Fenêtre Détails de méthode BDC
 Utilisez le **détails de méthode BDC** fenêtre pour définir les paramètres, les instances et descripteurs de filtre d’une méthode.  
  
 Vous pouvez générer rapidement des méthodes Finder recherche spécifique, créateur, mise à jour et suppression dans le **détails de méthode BDC** fenêtre. Lorsque vous générez ces méthodes, Visual Studio ajoute des métadonnées, telles que les paramètres, les instances et les descripteurs de type, à la méthode. Vous pouvez modifier ces métadonnées pour satisfaire votre scénario spécifique.  
  
 Pour ouvrir le **détails de méthode BDC** fenêtre, dans la barre de menus, choisissez **vue** > **Windows autres** > **détails de méthode BDC** .  
  
 Pour afficher les méthodes dans le **détails de méthode BDC** fenêtre, sélectionnez l’entité dans le concepteur BDC. Les méthodes de l’entité sélectionnée s’affichent dans le **détails de méthode BDC** fenêtre. Si vous ne choisissez pas une entité dans le concepteur BDC, le **détails de méthode BDC** fenêtre n’affiche aucune information.  
  
 Développer ou réduire des nœuds dans le **détails de méthode BDC** fenêtre pour définir des paramètres, des instances et descripteurs de filtre. Utilisez le **Explorateur BDC** pour définir les descripteurs de type.  
  
## <a name="bdc-explorer"></a>explorateur BDC
 Le **Explorateur BDC** affiche les éléments qui composent le modèle. Pour ouvrir le **Explorateur BDC**, dans la barre de menus, choisissez **vue** > **Windows autres** > **Explorateur BDC**. Pour parcourir le modèle, développez les nœuds dans le **Explorateur BDC**. Chaque nœud représente un élément dans le code XML du fichier de modèle.  
  
 Lorsque vous choisissez les nœuds dans le **Explorateur BDC**, les propriétés de chaque nœud que vous choisissez s’affichent dans le **propriétés** fenêtre. La plupart de ces propriétés correspondent aux attributs dans le fichier de modèle. Vous pouvez rechercher le modèle à l’aide de la zone de recherche en haut de la **Explorateur BDC**.  
  
> [!NOTE]  
>  Le **Explorateur BDC** n’affiche pas les identificateurs de propriétés personnalisées, les chaînes localisées, groupes d’association, actions, les descripteurs de filtre, listes de contrôle d’action et les valeurs de paramètre par défaut.  
  
### <a name="define-type-descriptors"></a>Définir les descripteurs de type
 Utilisez le **Explorateur BDC** pour définir les descripteurs de type. L’Explorateur BDC vous permet de définir un descripteur de type une seule fois et puis de le réutiliser ailleurs dans votre modèle. Pour ce faire, copiez un descripteur de type et le coller sur n’importe quel autre paramètre ou descripteur de type.  
  
> [!NOTE]  
>  Modifications apportées à un descripteur de type d’origine n’affectent pas les copies de ce descripteur de type.  
  
 Pour plus d'informations, voir [Procédure : Définir le descripteur de type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## <a name="see-also"></a>Voir aussi
 [Guide pratique pour Créer un modèle BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Guide pratique pour Ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Guide pratique pour Ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)   
 [Guide pratique pour Ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Guide pratique pour Ajouter une méthode de création](../sharepoint/how-to-add-a-creator-method.md)   
 [Guide pratique pour Ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)   
 [Guide pratique pour Ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)   
 [Créer une association entre entités](../sharepoint/creating-an-association-between-entities.md)   
 [Procédure pas à pas : Créer une liste externe dans SharePoint à l’aide de données d’entreprise](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)   
 [Intégrer des données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)   
 [Création d’un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Conception d’un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)  
