---
title: Extension des outils SharePoint dans Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f360982f26cf2eb9ffe26678743bb514d9606ae7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890671"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>Étendre les outils SharePoint dans Visual Studio
  Les outils SharePoint dans Visual Studio répondent aux exigences de nombreux scénarios de développement d’application. Toutefois, vous pouvez découvrir les cas où ils ne fournissent pas de fonctionnalité nécessitant vous ou autres développeurs. Dans ce cas, vous pouvez étendre les outils SharePoint pour créer les fonctionnalités dont vous avez besoin.

## <a name="how-to-extend-the-sharepoint-tools"></a>Comment étendre les outils SharePoint
 Vous pouvez étendre le système de projet SharePoint et le **connexions SharePoint** nœud dans le **Explorateur de serveurs** fenêtre.

### <a name="extend-the-sharepoint-project-system"></a>Étendre le système de projet SharePoint
 Visual Studio inclut un ensemble de modèles de projet et modèles d’élément que vous pouvez utiliser pour créer des solutions SharePoint. Par exemple, il existe des modèles pour les récepteurs d’événements, les définitions de listes, les workflows et les composants WebPart. Toutefois, vous pouvez également définir vos propres types d’éléments de projet SharePoint pour la création de composants SharePoint tels que des champs ou des actions personnalisées. Vous pouvez également créer des extensions pour les types d’éléments de projet SharePoint qui sont déjà installés dans Visual Studio, et vous pouvez créer des extensions pour les projets SharePoint.

 Pour plus d’informations, consultez [étendre le système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Étendre le nœud Connexions SharePoint dans l’Explorateur de serveurs
 Dans Visual Studio, vous pouvez utiliser la **connexions SharePoint** nœud dans le **Explorateur de serveurs** fenêtre pour afficher un grand nombre des composants d’un ou plusieurs sites SharePoint locaux dans une arborescence hiérarchique. Vous pouvez également étendre le **connexions SharePoint** nœud comme suit :

- En ajoutant vos propres nœuds. Cela est utile si vous souhaitez afficher les composants de sites SharePoint qui ne sont pas affichés par défaut.

- En étendant des nœuds existants. Par exemple, vous pouvez ajouter un nouveau nœud enfant à un nœud existant, ou vous pouvez ajouter un élément de menu contextuel à un nœud et effectuer des tâches lorsqu’un développeur clique sur l’élément de menu.

  Pour plus d’informations, consultez [étendre le nœud Connexions SharePoint dans l’Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="development-computer-requirements"></a>Exigences du développement d’ordinateur
 Pour créer des extensions pour les outils SharePoint, votre ordinateur de développement doit respecter les mêmes exigences pour la création de solutions SharePoint dans Visual Studio.

 Nous vous recommandons également d’installer le [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Le SDK inclut des modèles de projet et des outils que vous pouvez utiliser pour étendre Visual Studio. En particulier, le Kit de développement logiciel inclut un modèle de projet que vous pouvez utiliser pour créer facilement un package d’Extension Visual Studio (VSIX). Les packages VSIX constituent la meilleure façon de déployer des extensions Visual Studio dans Visual Studio. Toutes les extensions d’outils SharePoint doivent être déployées à l’aide de packages VSIX. Toutes les procédures pas à pas dans cette documentation supposent que vous avez le [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] installé.

 Pour installer le SDK Visual Studio, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md). Pour plus d’informations sur les extensions Visual Studio, consultez [commencer à développer des Extensions Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="see-also"></a>Voir aussi

- [Extensions d’outils de la vue d’ensemble du modèle de programmation de SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Étendre le système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Étendre le nœud Connexions SharePoint dans l’Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Concepts de programmation et les fonctionnalités des extensions d’outils SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Référence &#40;extensibilité des outils SharePoint&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Déboguer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [Déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)