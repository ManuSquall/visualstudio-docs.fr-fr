---
title: "Comment : obtenir des données pour un nœud SharePoint intégré dans l’Explorateur de serveurs | Documents Microsoft"
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
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
ms.assetid: 86d04e0a-c114-427e-9945-da5fa339fda4
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: fa518bf566671dda2b54489fa37460840365bc70
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>Comment : obtenir des données pour un nœud SharePoint intégré dans l'Explorateur de serveurs
  Pour chaque nœud SharePoint intégré dans **l’Explorateur de serveurs**, vous pouvez obtenir des données pour le composant SharePoint sous-jacent que le nœud représente. Pour plus d’informations, consultez [extension du nœud Connexions SharePoint dans l’Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
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
  
  