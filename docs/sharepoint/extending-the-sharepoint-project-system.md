---
title: Extension du système de projet SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 51449003457ecd09e7dca7bc579d652c94a592e2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53891110"
---
# <a name="extend-the-sharepoint-project-system"></a>Étendre le système de projet SharePoint
  Vous pouvez créer des solutions SharePoint à l’aide d’un ensemble de modèles de projet et modèles d’élément dans Visual Studio. Ces modèles de satisfont les besoins de nombreux scénarios de développement, mais vous pouvez découvrir certains cas où ils ne fournissent pas les fonctionnalités dont vous avez besoin. Dans ce cas, vous pouvez étendre le système de projet SharePoint.  
  
## <a name="overview-of-the-sharepoint-project-system"></a>Vue d’ensemble du système de projet SharePoint
 Le système de projet SharePoint est basé sur un composant fondamental de *éléments de projet SharePoint*. Un élément de projet SharePoint représente une personnalisation SharePoint unique, comme une définition de liste, un composant WebPart ou un type de contenu.  
  
 Un projet SharePoint est un projet Visual Studio qui inclut un ou plusieurs éléments de projet SharePoint. Les projets SharePoint contiennent également des composants supplémentaires qui définissent comment les éléments de projet sont regroupés en fonctionnalités et packages pour le déploiement.  
  
 Pour plus d’informations sur le contenu des éléments de projet SharePoint et des projets SharePoint, consultez [créer des modèles de projet pour les éléments de projet SharePoint et de modèles d’élément](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## <a name="how-to-extend-the-sharepoint-project-system"></a>Comment étendre le système de projet SharePoint
 Vous pouvez étendre le système de projet SharePoint comme suit :  
  
-   Définir vos propres types d’éléments de projet SharePoint et les associer à des modèles de projet dans Visual Studio ou de nouveaux modèles d’élément. Par exemple, vous pouvez définir un type d’élément de projet SharePoint pour la création d’une action personnalisée ou un champ. Pour plus d’informations, consultez [définissent les types d’éléments de projet SharePoint personnalisés](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
-   Étendre les types d’éléments de projet SharePoint qui sont déjà installés dans Visual Studio. Par exemple, vous pouvez ajouter un élément de menu contextuel à un élément de projet dans **l’Explorateur de solutions** et personnaliser l’élément de projet lorsqu’un développeur choisit l’élément de menu. Pour plus d’informations, consultez [éléments de projet SharePoint étendre](../sharepoint/extending-sharepoint-project-items.md).  
  
-   Étendre des projets SharePoint. Par exemple, vous pouvez ajouter des gestionnaires d’événements pour effectuer des tâches spécifiques lorsque les éléments sont ajoutés ou supprimés à partir des projets SharePoint. Pour plus d’informations, consultez [projets SharePoint étendre](../sharepoint/extending-sharepoint-projects.md).  
  
-   Étendre le comportement d’empaquetage et déploiement d’éléments de projet SharePoint et des projets SharePoint. Par exemple, vous pouvez créer vos propres étapes de déploiement à exécuter lorsque vous déployez ou retirez un projet, ou vous pouvez effectuer des tâches personnalisées supplémentaires lorsque Visual Studio exécute certaines étapes de déploiement. Pour plus d’informations, consultez [SharePoint étendre empaquetage et déploiement](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
## <a name="common-development-tasks"></a>Tâches de développement courantes
 Vous pouvez effectuer les tâches courantes suivantes dans les extensions du système de projet SharePoint :  
  
-   Enregistrer les données de chaîne personnalisée avec les éléments de projet et dans plusieurs types de fichiers de projet. Pour plus d’informations, consultez [enregistrer les données dans les extensions du système de projet SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
-   Convertir un objet dans le système de projet SharePoint à un objet correspondant dans le modèle objet automation Visual Studio ou le modèle objet d’intégration, ou vice versa. Pour plus d’informations, consultez [convertir une entre les types de système de projet SharePoint et d’autres types de projet Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
## <a name="see-also"></a>Voir aussi
 [Définir les types d’éléments de projet SharePoint personnalisés](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Étendre des éléments de projet SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Étendre des projets SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Étendre le déploiement et empaquetage de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Enregistrer les données dans les extensions du système de projet SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Effectuer une conversion entre les types de système de projet SharePoint et d’autres types de projet Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Étendre les outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Concepts et fonctionnalités de programmation des extensions d’outils SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)  
