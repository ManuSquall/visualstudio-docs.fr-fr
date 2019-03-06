---
title: Référence des API (extensibilité des outils SharePoint) | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, reference for project and tools extensibility
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 37639068b74b5d99864871355a8b9ef36906f6cd
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628726"
---
# <a name="api-reference-sharepoint-tools-extensibility"></a>Référence des API (extensibilité des outils SharePoint)
  Cette section contient la documentation de référence des API permettant d’étendre les outils SharePoint dans Visual Studio.

## <a name="in-this-section"></a>Dans cette section
 <xref:Microsoft.VisualStudio.SharePoint>

 Contient des types qui vous permet d’étendre le système de projet SharePoint. Par exemple, vous pouvez étendre les éléments de projet et les projets SharePoint intégrés, ou vous pouvez créer vos propres éléments de projet.

 <xref:Microsoft.VisualStudio.SharePoint.Commands>

 Contient des types que vous pouvez utiliser pour créer des *commandes SharePoint*. Une commande SharePoint est une méthode qui appelle le modèle objet serveur SharePoint à partir d’une extension des outils SharePoint.

 <xref:Microsoft.VisualStudio.SharePoint.Deployment>

 Contient des types qui vous permet d’étendre le processus de déploiement des projets SharePoint.

 <xref:Microsoft.VisualStudio.SharePoint.Explorer>

 Contient des types qui vous permettent d’étendre les nœuds SharePoint de **Explorateur de serveurs** ou pour définir vos propres types de nœuds.

 <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>

 Contient des types que vous pouvez utiliser pour obtenir des informations sur intégrée **Explorateur de serveurs** nœuds qui représentent des composants individuels d’un site SharePoint, tel qu’un nœud qui représente une liste, un champ ou un type de contenu.

 <xref:Microsoft.VisualStudio.SharePoint.Features>

 Contient des types que vous utilisez pour accéder à la définition d’une fonctionnalité dans un projet SharePoint.

 <xref:Microsoft.VisualStudio.SharePoint.Packages>

 Contient des types que vous utilisez pour accéder à la définition du package dans un projet SharePoint.

 <xref:Microsoft.VisualStudio.SharePoint.Remote.Authentication>

 Contient des types qui vous permettent d’authentifier et de communiquer avec les applications pour SharePoint qui sont déployés sur des sites SharePoint à distance.

 <xref:Microsoft.VisualStudio.SharePoint.Remote.Commands>

 Contient des types qui vous permet de créer des commandes à distance de SharePoint, qui sont utilisés avec des applications pour SharePoint qui sont déployés sur des sites SharePoint à distance.

 <xref:Microsoft.VisualStudio.SharePoint.Tasks>

 Contient des types que Visual Studio utilise comme créer des tâches pour le packaging et le débogage de projets SharePoint, des applications pour Office et des applications pour SharePoint. Cette API prend en charge l’infrastructure Office et SharePoint et n’est pas destinée à être utilisée directement à partir de votre code.

 <xref:Microsoft.VisualStudio.SharePoint.Validation>

 Contient des types qui vous permettent de personnaliser le comportement de validation de fonctionnalité et de package pour un projet SharePoint.

## <a name="see-also"></a>Voir aussi
- [Référence &#40;extensibilité des outils SharePoint&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Extensions d’outils de la vue d’ensemble du modèle de programmation de SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Étendre le système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Étendre le nœud Connexions SharePoint dans l’Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Étendre le déploiement et empaquetage de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Appeler des modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
