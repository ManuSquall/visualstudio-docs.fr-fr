---
title: L’utilisation du Service de projet SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4dfb7592fb2cec05da1bd72bd69a76e9a3b270db
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619977"
---
# <a name="use-the-sharepoint-project-service"></a>Utiliser le service de projet SharePoint
  Le système de projet SharePoint inclut un service de projet que vous pouvez utiliser pour effectuer des tâches liées au système de projet. Le service de projet est un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>.

 Vous pouvez accéder au service de projet SharePoint dans toute extension d'outils SharePoint. Vous pouvez également y accéder dans d’autres types d’extensions Visual Studio, comme les modules complémentaires et VSPackages. Pour plus d'informations, voir [Procédure : Récupérer le service de projet SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

## <a name="project-service-features"></a>Fonctionnalités de service de projet
 Le tableau suivant répertorie les tâches que vous pouvez effectuer à l’aide du service de projet SharePoint et la méthode ou propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> à utiliser pour effectuer chaque tâche.

|Tâche|Membre à utiliser|
|----------|-------------------|
|Accéder à un projet SharePoint ouvert dans Visual Studio.|Propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A>.|
|Accéder à tous les types d'éléments de projet SharePoint disponibles (y compris les types d'éléments de projet intégrés et personnalisés).|Propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A>.|
|Accéder à toutes les étapes de déploiement disponibles pour les projets SharePoint (y compris les étapes de déploiement intégrées et personnalisées).|Propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A>.|
|Accéder aux événements qui sont déclenchés quand un développeur refactorise le code dans un projet SharePoint.|Propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A>.|
|Exécuter un personnalisé *commande SharePoint* qui appelle le modèle d’objet de serveur SharePoint. Pour plus d’informations sur les commandes SharePoint, consultez [appeler des modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|Propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A>.|
|Convertir un type dans le système de projet SharePoint en un type dans le modèle d'objet automation Visual Studio ou le modèle d'objet d'intégration, et vice versa. Pour plus d’informations, consultez [effectuer des conversions entre types de système de projet SharePoint et d’autres types de projet Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).|Méthode<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> .|
|Écrire des messages dans la **sortie** fenêtre ou **liste d’erreurs** fenêtre dans Visual Studio.|Propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A>.|
|Accéder aux autres services qui sont disponibles dans Visual Studio.|Propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A>.|
|Récupérer le chemin d'accès au dossier d'installation du site SharePoint local qui est utilisé pour le débogage de la solution.|Propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A>.|
|Déterminer si [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] ou [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] est installé sur l'ordinateur.|Propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A>.|
|Valider une fonctionnalité ou un package dans une solution SharePoint.|Propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A>.|

## <a name="see-also"></a>Voir aussi
- [Effectuer une conversion entre les types de système de projet SharePoint et d’autres types de projet Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Guide pratique pour Récupérer le service de projet SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Étendre les outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Extensions d’outils de la vue d’ensemble du modèle de programmation de SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Guide pratique pour Obtenir un Service à partir de l’objet DTE](https://msdn.microsoft.com/library/bb166401.aspx)
