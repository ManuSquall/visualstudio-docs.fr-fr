---
title: "Comment : créer une Extension d’élément de projet SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: d4a5aa0b7e40ddca0281ce92c3bbf9946238403e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>Comment : créer une extension d’élément de projet SharePoint
  Créer une extension d’élément de projet lorsque vous souhaitez ajouter des fonctionnalités à un élément de projet SharePoint est déjà installé dans Visual Studio. Pour plus d’informations, consultez [étendre des éléments de projet SharePoint](../sharepoint/extending-sharepoint-project-items.md).  
  
### <a name="to-create-a-project-item-extension"></a>Pour créer une extension d’élément de projet  
  
1.  Créez un projet de bibliothèque de classes.  
  
2.  Ajoutez des références aux assemblys suivants :  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Définissez une classe qui implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>.  
  
4.  Ajoutez les attributs suivants à la classe :  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. Cet attribut permet à Visual Studio de découvrir et de charger votre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implémentation. Passez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> type au constructeur d’attribut.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Dans une extension d’élément de projet, cet attribut identifie l’élément de projet que vous souhaitez étendre. Passez l’ID de l’élément de projet au constructeur d’attribut. Pour obtenir la liste des ID des éléments de projet sont inclus dans Visual Studio, consultez [étendre des éléments de projet SharePoint](../sharepoint/extending-sharepoint-project-items.md).  
  
5.  Dans votre implémentation de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> (méthode), utilisez les membres de la *projectItemType* paramètre pour définir le comportement de votre extension. Ce paramètre est un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> objet qui fournit l’accès aux événements définis dans le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> et <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> interfaces. Pour accéder à une instance spécifique du type d’élément de projet vous étendez, gérez <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> événements tels que <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> et <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment créer une simple extension pour l’élément de projet récepteur d’événements. Chaque fois que l’utilisateur ajoute un élément de projet de récepteur d’événements à un projet SharePoint, cette extension écrit un message à la **sortie** fenêtre et **liste d’erreurs** fenêtre.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb#1)]  
  
 Cet exemple utilise le service de projet SharePoint pour écrire le message à la **sortie** fenêtre et **liste d’erreurs** fenêtre. Pour plus d’informations, consultez [à l’aide du Service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Déploiement de l’Extension  
 Pour déployer l’extension, créez un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déploiement d’Extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Étendre des éléments de projet SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Procédure pas à pas : extension d’un type d’élément de projet SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  