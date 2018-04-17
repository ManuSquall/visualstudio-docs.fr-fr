---
title: 'Comment : obtenir des données pour un nœud SharePoint intégré dans l’Explorateur de serveurs | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f448ec8d7cfe22495aa3f7b2ce9191f106205c33
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>Comment : obtenir des données pour un nœud SharePoint intégré dans l'Explorateur de serveurs
  Pour chaque nœud SharePoint intégré dans **l’Explorateur de serveurs**, vous pouvez obtenir des données pour le composant SharePoint sous-jacent que le nœud représente. Pour plus d'informations, consultez [Extension du nœud Connexions SharePoint dans l'Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment obtenir des données pour la liste SharePoint sous-jacente qui représente un nœud de liste **l’Explorateur de serveurs**. Par défaut, les nœuds de liste ont un **afficher dans le navigateur** élément de menu contextuel que vous pouvez cliquer pour ouvrir les listes dans un navigateur Web. Cet exemple étend les nœuds de la liste en ajoutant un **affichage dans Visual Studio** élément de menu contextuel qui s’ouvre les listes directement dans Visual Studio. Le code accède à des données de liste pour le nœud obtenir l’URL de la liste pour l’ouvrir dans Visual Studio.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]  
  
 Cet exemple utilise le service de projet SharePoint pour obtenir le <xref:EnvDTE.DTE> répertorie d’objet qui sert à ouvrir dans Visual Studio. Pour plus d’informations sur le service de projet SharePoint, consultez [à l’aide du Service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
 Pour plus d’informations sur les tâches de base pour créer une extension pour un nœud SharePoint, consultez [Comment : étendre un nœud SharePoint dans l’Explorateur de serveurs](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite des références aux assemblys suivants :  
  
-   EnvDTE  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Déploiement de l’Extension  
 Pour déployer le **l’Explorateur de serveurs** extension, créez un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déploiement d’Extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Extension du nœud Connexions SharePoint dans l’Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Comment : étendre un nœud SharePoint dans l’Explorateur de serveurs](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [L’utilisation du Service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Déploiement d’extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  