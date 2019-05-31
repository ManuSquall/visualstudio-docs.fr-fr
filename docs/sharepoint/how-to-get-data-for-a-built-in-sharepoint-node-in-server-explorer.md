---
title: Obtenir des données pour un nœud SharePoint intégré dans l’Explorateur de serveurs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b90582c9b8d352f95d3d5abb3bbb7fb69283b06b
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401421"
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>Procédure : Obtenir des données pour un nœud SharePoint intégré dans l’Explorateur de serveurs
  Pour chaque nœud SharePoint intégré dans **Explorateur de serveurs**, vous pouvez obtenir des données pour le composant SharePoint sous-jacent que le nœud représente. Pour plus d’informations, consultez [étendre le nœud Connexions SharePoint dans l’Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="example"></a>Exemple
 L’exemple de code suivant montre comment obtenir des données pour la liste SharePoint sous-jacente qui représente un nœud de liste **Explorateur de serveurs**. Par défaut, les nœuds de liste ont une **afficher dans le navigateur** élément de menu contextuel que vous pouvez cliquer pour ouvrir les listes dans un navigateur Web. Cet exemple étend les nœuds de la liste en ajoutant un **affichage dans Visual Studio** élément de menu contextuel qui s’ouvre les listes directement dans Visual Studio. Le code accède à des données de liste pour le nœud obtenir l’URL de la liste pour l’ouvrir dans Visual Studio.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]

 Cet exemple utilise le service de projet SharePoint pour obtenir le <xref:EnvDTE.DTE> répertorie d’objet qui sert à ouvrir dans Visual Studio. Pour plus d’informations sur le service de projet SharePoint, consultez [utiliser le service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

 Pour plus d’informations sur les tâches de base pour créer une extension pour un nœud SharePoint, consultez [Comment : Étendre un nœud SharePoint dans l’Explorateur de serveurs](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple nécessite des références aux assemblys suivants :

- EnvDTE

- Microsoft.VisualStudio.SharePoint

- Microsoft.VisualStudio.SharePoint.Explorer.Extensions

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Déployer l’extension
 Pour déployer le **Explorateur de serveurs** extension, créez un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Étendre le nœud Connexions SharePoint dans l’Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Guide pratique pour Étendre un nœud SharePoint dans l’Explorateur de serveurs](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Utiliser le service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
