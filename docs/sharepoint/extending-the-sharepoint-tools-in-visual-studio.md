---
title: Extension des outils SharePoint dans Visual Studio | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7dc0cc0d0af73d032d870629877b62c94e6b347b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016035"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>Étendre les outils SharePoint dans Visual Studio
  Les outils SharePoint dans Visual Studio répondent aux besoins de nombreux scénarios de développement d’applications. Toutefois, vous pouvez découvrir les cas où ils ne fournissent pas de fonctionnalité dont vous ou d’autres développeurs avez besoin. Dans ce cas, vous pouvez étendre les outils SharePoint pour créer les fonctionnalités dont vous avez besoin.

## <a name="how-to-extend-the-sharepoint-tools"></a>Comment étendre les outils SharePoint
 Vous pouvez étendre le système de projet SharePoint et le nœud **Connexions SharePoint** dans la fenêtre de **Explorateur de serveurs** .

### <a name="extend-the-sharepoint-project-system"></a>Étendre le système de projet SharePoint
 Visual Studio comprend un ensemble de modèles de projet et de modèles d’élément que vous pouvez utiliser pour créer des solutions SharePoint. Par exemple, il existe des modèles pour les récepteurs d’événements, les définitions de listes, les flux de travail et les composants WebPart. Toutefois, vous pouvez également définir vos propres types d’éléments de projet SharePoint pour la création de composants SharePoint, tels que des champs ou des actions personnalisées. Vous pouvez également créer des extensions pour les types d’éléments de projet SharePoint qui sont déjà installés dans Visual Studio, et vous pouvez créer des extensions pour les projets SharePoint.

 Pour plus d’informations, consultez [étendre le système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Étendre le nœud Connexions SharePoint dans Explorateur de serveurs
 Dans Visual Studio, vous pouvez utiliser le nœud **Connexions SharePoint** dans la fenêtre **Explorateur de serveurs** pour afficher un grand nombre des composants d’un ou plusieurs sites SharePoint locaux dans une arborescence hiérarchique. Vous pouvez également étendre le nœud **Connexions SharePoint** des manières suivantes :

- En ajoutant vos propres nœuds. Cela est utile si vous souhaitez afficher des composants de sites SharePoint qui ne sont pas affichés par défaut.

- En étendant les nœuds existants. Par exemple, vous pouvez ajouter un nouveau nœud enfant à un nœud existant, ou vous pouvez ajouter un élément de menu contextuel à un nœud et effectuer des tâches lorsqu’un développeur clique sur l’élément de menu.

  Pour plus d’informations, consultez [étendre le nœud Connexions SharePoint dans Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="development-computer-requirements"></a>Configuration requise pour l’ordinateur de développement
 Pour créer des extensions pour les outils SharePoint, votre ordinateur de développement doit répondre aux mêmes conditions requises pour la création de solutions SharePoint dans Visual Studio.

 Nous vous recommandons également d’installer l' [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] . Le kit de développement logiciel (SDK) comprend des modèles de projet et des outils que vous pouvez utiliser pour étendre Visual Studio. En particulier, le kit de développement logiciel (SDK) comprend un modèle de projet que vous pouvez utiliser pour créer facilement un package d’extension Visual Studio (VSIX). Les packages VSIX constituent la meilleure façon de déployer des extensions Visual Studio dans Visual Studio. Toutes les extensions des outils SharePoint doivent être déployées à l’aide de packages VSIX. Toutes les procédures pas à pas de cette documentation supposent que vous avez [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] installé.

 Pour installer le kit de développement logiciel (SDK) Visual Studio, consultez [installation du kit de développement logiciel Visual Studio](../extensibility/installing-the-visual-studio-sdk.md). Pour plus d’informations sur les extensions Visual Studio, consultez [commencer à développer des extensions Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du modèle de programmation des extensions d’outils SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Étendre le système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Étendre le nœud Connexions SharePoint dans Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Concepts et fonctionnalités de programmation pour les extensions des outils SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Référence &#40;&#41;d’extensibilité des outils SharePoint ](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Extensions de débogage pour les outils SharePoint dans Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [Déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)