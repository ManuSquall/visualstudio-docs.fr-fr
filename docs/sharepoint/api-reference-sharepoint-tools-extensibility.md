---
title: Informations de référence sur les API (extensibilité des outils SharePoint) | Microsoft Docs
description: Consultez la documentation de référence sur les API pour étendre les outils SharePoint dans Visual Studio. Consultez la liste des espaces de noms connexes, tels que Microsoft. VisualStudio. SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, reference for project and tools extensibility
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ec07272ede6c957afb43c29342e8479e67d1dd0e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851717"
---
# <a name="api-reference-sharepoint-tools-extensibility"></a>Informations de référence sur les API (extensibilité des outils SharePoint)
  Cette section contient la documentation de référence sur les API permettant d’étendre les outils SharePoint dans Visual Studio.

## <a name="in-this-section"></a>Dans cette section
 <xref:Microsoft.VisualStudio.SharePoint>

 Contient les types que vous utilisez pour étendre le système de projet SharePoint. Par exemple, vous pouvez étendre les éléments de projet et les projets SharePoint intégrés, ou vous pouvez créer vos propres éléments de projet.

 <xref:Microsoft.VisualStudio.SharePoint.Commands>

 Contient des types que vous pouvez utiliser pour créer des *commandes SharePoint* personnalisées. Une commande SharePoint est une méthode qui appelle le modèle objet serveur SharePoint à partir d'une extension des outils SharePoint.

 <xref:Microsoft.VisualStudio.SharePoint.Deployment>

 Contient les types que vous utilisez pour étendre le processus de déploiement pour les projets SharePoint.

 <xref:Microsoft.VisualStudio.SharePoint.Explorer>

 Contient les types que vous utilisez pour étendre des nœuds SharePoint dans **Explorateur de serveurs** ou pour définir vos propres types de nœuds.

 <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>

 Contient des types que vous pouvez utiliser pour obtenir des informations sur les nœuds de **Explorateur de serveurs** intégrés qui représentent des composants individuels sur un site SharePoint, par exemple un nœud qui représente une liste, un champ ou un type de contenu.

 <xref:Microsoft.VisualStudio.SharePoint.Features>

 Contient les types que vous utilisez pour accéder à la définition d’une fonctionnalité dans un projet SharePoint.

 <xref:Microsoft.VisualStudio.SharePoint.Packages>

 Contient les types que vous utilisez pour accéder à la définition de package dans un projet SharePoint.

 <xref:Microsoft.VisualStudio.SharePoint.Remote.Authentication>

 Contient les types que vous utilisez pour vous authentifier et communiquer avec les applications pour SharePoint déployées sur des sites SharePoint distants.

 <xref:Microsoft.VisualStudio.SharePoint.Remote.Commands>

 Contient les types que vous utilisez pour créer des commandes distantes SharePoint, qui sont utilisées avec les applications pour SharePoint déployées sur des sites SharePoint distants.

 <xref:Microsoft.VisualStudio.SharePoint.Tasks>

 Contient les types que Visual Studio utilise comme tâches de génération pour empaqueter et déboguer des projets SharePoint, des applications pour Office et des applications pour SharePoint. Cette API prend en charge l’infrastructure Office et SharePoint et n’est pas destinée à être utilisée directement à partir de votre code.

 <xref:Microsoft.VisualStudio.SharePoint.Validation>

 Contient les types que vous utilisez pour personnaliser le comportement de validation des fonctionnalités et des packages pour un projet SharePoint.

## <a name="see-also"></a>Voir aussi
- [Référence &#40;&#41;d’extensibilité des outils SharePoint ](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Vue d’ensemble du modèle de programmation des extensions d’outils SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Étendre le système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Étendre le nœud Connexions SharePoint dans Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Étendre le déploiement et l’empaquetage SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Appeler les modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
