---
title: "Extension du système de projet SharePoint | Documents Microsoft"
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
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
ms.assetid: 654b2973-a5c9-44be-a3d2-8bc3d15f9624
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 99380078b2fc49bcc5e1efb7a36ac7f28028a0d7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="extending-the-sharepoint-project-system"></a>Extension du système de projet SharePoint
  Vous pouvez créer des solutions SharePoint à l’aide d’un ensemble de modèles de projet et modèles d’élément dans Visual Studio. Ces modèles répondent aux exigences de nombreux scénarios de développement, mais vous pouvez découvrir certains cas où elles ne fournissent pas les fonctionnalités dont vous avez besoin. Dans ce cas, vous pouvez étendre le système de projet SharePoint.  
  
## <a name="overview-of-the-sharepoint-project-system"></a>Vue d’ensemble du système de projet SharePoint  
 Le système de projet SharePoint repose sur un composant fondamental de *éléments de projet SharePoint*. Un élément de projet SharePoint représente une personnalisation SharePoint unique, comme une définition de liste, un composant WebPart ou un type de contenu.  
  
 Un projet SharePoint est un projet Visual Studio qui inclut un ou plusieurs éléments de projet SharePoint. Les projets SharePoint contiennent également des composants supplémentaires qui définissent comment les éléments de projet sont regroupés dans des fonctionnalités et des packages de déploiement.  
  
 Pour plus d’informations sur le contenu des éléments de projet SharePoint et des projets SharePoint, consultez [création de modèles d’élément et les modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## <a name="how-to-extend-the-sharepoint-project-system"></a>Comment étendre le système de projet SharePoint  
 Vous pouvez étendre le système de projet SharePoint comme suit :  
  
-   Définir vos propres types d’éléments de projet SharePoint et les associer à des modèles de projet dans Visual Studio ou de nouveaux modèles d’élément. Par exemple, vous pouvez définir un type d’élément de projet SharePoint pour la création d’une action personnalisée ou un champ. Pour plus d’informations, consultez [Types d’éléments de projet de définition personnalisé SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
-   Étendre les types d’éléments de projet SharePoint qui sont déjà installés dans Visual Studio. Par exemple, vous pouvez ajouter un élément de menu contextuel à un élément de projet **l’Explorateur de solutions** et personnaliser l’élément de projet lorsqu’un développeur choisit l’élément de menu. Pour plus d’informations, consultez [étendre des éléments de projet SharePoint](../sharepoint/extending-sharepoint-project-items.md).  
  
-   Étendre des projets SharePoint. Par exemple, vous pouvez ajouter des gestionnaires d’événements pour effectuer des tâches spécifiques lorsque des éléments sont ajoutés ou supprimés à partir des projets SharePoint. Pour plus d’informations, consultez [étendre des projets SharePoint](../sharepoint/extending-sharepoint-projects.md).  
  
-   Étendre le comportement d’empaquetage et de déploiement des éléments de projet SharePoint et des projets SharePoint. Par exemple, vous pouvez créer vos propres étapes de déploiement à exécuter lorsque vous déployez ou retirez un projet, ou vous pouvez effectuer des tâches personnalisées supplémentaires lorsque Visual Studio exécute certaines étapes de déploiement. Pour plus d’informations, consultez [étendre un empaquetage SharePoint et déploiement](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
## <a name="common-development-tasks"></a>Tâches de développement courantes  
 Vous pouvez effectuer les tâches courantes suivantes dans les extensions du système de projet SharePoint :  
  
-   Enregistrer les données de chaîne personnalisée avec les éléments de projet et dans plusieurs types de fichiers de projet. Pour plus d’informations, consultez [l’enregistrement des données dans les Extensions du système de projet SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
-   Convertir un objet dans le système de projet SharePoint à un objet correspondant dans le modèle objet automation Visual Studio ou le modèle objet d’intégration, ou vice versa. Pour plus d’informations, consultez [conversion entre système de Types de projet SharePoint et d’autres Types de projet Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Types d’éléments de projet SharePoint personnalisé](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Étendre des éléments de projet SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Extension des projets SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Déploiement et l’extension empaquetage de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Enregistrement des données dans les Extensions du système de projet SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Conversion entre Types de système de projet SharePoint et d’autres Types de projet Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Extension des outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Concepts et fonctionnalités de programmation des extensions d’outils SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)  
  
  