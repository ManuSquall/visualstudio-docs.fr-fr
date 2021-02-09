---
title: Extension du système de projet SharePoint | Microsoft Docs
description: Étendre le système de projet SharePoint. Découvrez comment étendre le système de projet SharePoint. Comprendre les tâches de développement courantes.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5a81fef67cc6816f16a074494005a61d647abeab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889679"
---
# <a name="extend-the-sharepoint-project-system"></a>Étendre le système de projet SharePoint
  Vous pouvez créer des solutions SharePoint à l’aide d’un ensemble de modèles de projet et de modèles d’élément dans Visual Studio. Ces modèles répondent aux besoins de nombreux scénarios de développement, mais vous pouvez découvrir certains cas où ils ne fournissent pas les fonctionnalités dont vous avez besoin. Dans ce cas, vous pouvez étendre le système de projet SharePoint.

## <a name="overview-of-the-sharepoint-project-system"></a>Vue d’ensemble du système de projet SharePoint
 Le système de projet SharePoint est basé sur le composant fondamental des *éléments de projet SharePoint*. Un élément de projet SharePoint représente une personnalisation SharePoint unique, telle qu’une définition de liste, un composant WebPart ou un type de contenu.

 Un projet SharePoint est un projet Visual Studio qui contient un ou plusieurs éléments de projet SharePoint. Les projets SharePoint contiennent également des composants supplémentaires qui définissent la façon dont les éléments de projet sont regroupés dans des fonctionnalités et des packages à des fins de déploiement.

 Pour plus d’informations sur le contenu des éléments de projet SharePoint et des projets SharePoint, consultez [créer des modèles d’élément et des modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

## <a name="how-to-extend-the-sharepoint-project-system"></a>Comment étendre le système de projet SharePoint
 Vous pouvez étendre le système de projet SharePoint des manières suivantes :

- Définissez vos propres types d’éléments de projet SharePoint et associez-les aux nouveaux modèles d’élément ou modèles de projet dans Visual Studio. Par exemple, vous pouvez définir un type d’élément de projet SharePoint pour la création d’une action personnalisée ou d’un champ. Pour plus d’informations, consultez [définir des types d’éléments de projet SharePoint personnalisés](../sharepoint/defining-custom-sharepoint-project-item-types.md).

- Étendez les types d’éléments de projet SharePoint qui sont déjà installés dans Visual Studio. Par exemple, vous pouvez ajouter un élément de menu contextuel à un élément de projet dans **Explorateur de solutions** et personnaliser l’élément de projet lorsqu’un développeur choisit l’élément de menu. Pour plus d’informations, consultez [étendre les éléments de projet SharePoint](../sharepoint/extending-sharepoint-project-items.md).

- Étendez les projets SharePoint. Par exemple, vous pouvez ajouter des gestionnaires d’événements pour effectuer des tâches spécifiques lorsque des éléments sont ajoutés ou supprimés dans des projets SharePoint. Pour plus d’informations, consultez [étendre des projets SharePoint](../sharepoint/extending-sharepoint-projects.md).

- Étendez le comportement de Packaging et de déploiement des éléments de projet SharePoint et des projets SharePoint. Par exemple, vous pouvez créer vos propres étapes de déploiement à exécuter lorsque vous déployez ou rétractez un projet, ou vous pouvez effectuer des tâches personnalisées supplémentaires quand Visual Studio exécute certaines étapes de déploiement. Pour plus d’informations, consultez extension de l' [empaquetage et du déploiement SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

## <a name="common-development-tasks"></a>Tâches de développement courantes
 Vous pouvez effectuer les tâches courantes suivantes dans les extensions du système de projet SharePoint :

- Enregistrer des données de chaîne personnalisées avec des éléments de projet et dans différents types de fichiers projet. Pour plus d’informations, consultez [enregistrer des données dans les extensions du système de projet SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

- Conversion d’un objet dans le système de projet SharePoint en un objet correspondant dans le modèle objet Automation Visual Studio ou le modèle objet d’intégration, ou vice versa. Pour plus d’informations, consultez Conversions [entre les types système de projet SharePoint et d’autres types de projets Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

## <a name="see-also"></a>Voir aussi
- [Définir des types d’éléments de projet SharePoint personnalisés](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Étendre les éléments de projet SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Étendre des projets SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Étendre le déploiement et l’empaquetage SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Enregistrer des données dans les extensions du système de projet SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Effectuer une conversion entre des types système de projet SharePoint et d’autres types de projets Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Étendre les outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Concepts et fonctionnalités de programmation des extensions d'outils SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
