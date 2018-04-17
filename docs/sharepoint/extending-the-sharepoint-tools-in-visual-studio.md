---
title: Extension des outils SharePoint dans Visual Studio | Documents Microsoft
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
ms.openlocfilehash: 7d5ad6f27574fcb7bd8a859bcd21ac65e159596e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="extending-the-sharepoint-tools-in-visual-studio"></a>Extension des outils SharePoint dans Visual Studio
  Les outils SharePoint dans Visual Studio répond aux exigences de nombreux scénarios de développement d’application. Toutefois, vous pouvez découvrir les cas où elles ne fournissent pas de fonctionnalités qui nécessitent de vous ou autres développeurs. Dans ce cas, vous pouvez étendre les outils SharePoint pour créer les fonctionnalités dont vous avez besoin.  
  
## <a name="how-to-extend-the-sharepoint-tools"></a>Comment étendre les outils SharePoint  
 Vous pouvez étendre le système de projet SharePoint et le **connexions SharePoint** nœud dans le **l’Explorateur de serveurs** fenêtre.  
  
### <a name="extending-the-sharepoint-project-system"></a>Extension du système de projet SharePoint  
 Visual Studio comprend un ensemble de modèles de projet et modèles d’élément que vous pouvez utiliser pour créer des solutions SharePoint. Par exemple, il existe des modèles pour les récepteurs d’événements, les définitions de listes, les workflows et les composants WebPart. Toutefois, vous pouvez également définir vos propres types d’éléments de projet SharePoint pour la création de composants SharePoint tels que des champs ou des actions personnalisées. Vous pouvez également créer des extensions pour les types d’éléments de projet SharePoint qui sont déjà installés dans Visual Studio, et vous pouvez créer des extensions pour les projets SharePoint.  
  
 Pour plus d’informations, consultez [extension du système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
### <a name="extending-the-sharepoint-connections-node-in-server-explorer"></a>Extension du nœud Connexions SharePoint dans l'Explorateur de serveurs  
 Dans Visual Studio, vous pouvez utiliser la **connexions SharePoint** nœud dans le**l’Explorateur de serveurs** fenêtre pour afficher un grand nombre des composants d’un ou plusieurs sites SharePoint locaux dans une arborescence hiérarchique. Vous pouvez également étendre le **connexions SharePoint** nœud comme suit :  
  
-   En ajoutant vos propres nœuds. Cela est utile si vous souhaitez afficher les composants de sites SharePoint qui ne sont pas affichés par défaut.  
  
-   En étendant des nœuds existants. Par exemple, vous pouvez ajouter un nouveau nœud enfant à un nœud existant, ou vous pouvez ajouter un élément de menu contextuel à un nœud et effectuer des tâches lorsqu’un développeur clique sur l’élément de menu.  
  
 Pour plus d'informations, consultez [Extension du nœud Connexions SharePoint dans l'Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## <a name="development-computer-requirements"></a>Spécifications d’ordinateur de développement  
 Pour créer des extensions pour les outils SharePoint, votre ordinateur de développement doit respecter les mêmes spécifications pour la création de solutions SharePoint dans Visual Studio. Pour plus d’informations, consultez [configuration requise pour le développement de Solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
 Nous recommandons également d’installer le [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Le kit SDK inclut des modèles de projet et des outils que vous pouvez utiliser pour étendre Visual Studio. En particulier, le kit SDK inclut un modèle de projet que vous permet de facilement créer un package d’Extension Visual Studio (VSIX). Les packages VSIX constituent la meilleure façon de déployer des extensions Visual Studio dans Visual Studio. Toutes les extensions d’outils SharePoint doivent être déployées à l’aide de packages VSIX. Toutes les procédures pas à pas dans cette documentation supposent que vous avez le [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] installé.  
  
 Pour installer le Kit de développement logiciel Visual Studio, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md). Pour plus d’informations sur les extensions Visual Studio, consultez [commencer à développer des Extensions Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du modèle de programmation de SharePoint les Extensions d’outils](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Extension du système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Extension du nœud Connexions SharePoint dans l’Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Concepts de programmation et les fonctionnalités des Extensions des outils SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Référence &#40;extensibilité des outils SharePoint&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)   
 [Déboguer des Extensions pour les outils SharePoint dans Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)   
 [Déploiement d’extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  