---
title: 'Comment : créer une extension d’élément de projet SharePoint | Microsoft Docs'
description: Passez en revue la procédure de création d’une extension d’élément de projet lorsque vous souhaitez ajouter des fonctionnalités à un élément de projet SharePoint qui est déjà installé dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0f55eb3ba06f2541bf1f4777c24927993444c6b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873604"
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>Comment : créer une extension d’élément de projet SharePoint
  Créez une extension d’élément de projet lorsque vous souhaitez ajouter des fonctionnalités à un élément de projet SharePoint qui est déjà installé dans Visual Studio. Pour plus d’informations, consultez [étendre les éléments de projet SharePoint](../sharepoint/extending-sharepoint-project-items.md).

### <a name="to-create-a-project-item-extension"></a>Pour créer une extension d’élément de projet

1. Créez un projet de bibliothèque de classes.

2. Ajoutez des références aux assemblys suivants :

    - Microsoft. VisualStudio. SharePoint

    - System.ComponentModel.Composition

3. Définissez une classe qui implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>.

4. Ajoutez les attributs suivants à la classe :

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Cet attribut permet à Visual Studio de découvrir et de charger votre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implémentation. Transmettez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> type au constructeur d’attribut.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Dans une extension d’élément de projet, cet attribut identifie l’élément de projet que vous souhaitez étendre. Transmettez l’ID de l’élément de projet au constructeur d’attribut. Pour obtenir la liste des ID des éléments de projet inclus dans Visual Studio, consultez étendre les [éléments de projet SharePoint](../sharepoint/extending-sharepoint-project-items.md).

5. Dans votre implémentation de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> méthode, utilisez les membres du paramètre *projectItemType* pour définir le comportement de votre extension. Ce paramètre est un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> objet qui fournit l’accès aux événements définis dans les <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> interfaces et. Pour accéder à une instance spécifique du type d’élément de projet que vous étendez, gérez les <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> événements tels que <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> et <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized> .

## <a name="example"></a>Exemple
 L’exemple de code suivant montre comment créer une extension simple pour l’élément de projet récepteur d’événements. Chaque fois que l’utilisateur ajoute un élément de projet de récepteur d’événements à un projet SharePoint, cette extension écrit un message dans la fenêtre **sortie** et dans la fenêtre de **liste d’erreurs** .

 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb#1)]

 Cet exemple utilise le service de projet SharePoint pour écrire le message dans la fenêtre **sortie** et dans la fenêtre de **liste d’erreurs** . Pour plus d’informations, consultez [utiliser le service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple nécessite des références aux assemblys suivants :

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Déployer l’extension
 Pour déployer l’extension, créez un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Étendre les éléments de projet SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Procédure pas à pas : étendre un type d’élément de projet SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
