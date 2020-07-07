---
title: Obtenir des données pour le nœud SharePoint intégré dans Explorateur de serveurs
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 5bb69773bf3f031b75d63ebe8cb1f1b4a00286c9
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014892"
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>Comment : obtenir des données pour un nœud SharePoint intégré dans Explorateur de serveurs
  Pour chaque nœud SharePoint intégré dans **Explorateur de serveurs**, vous pouvez obtenir des données pour le composant SharePoint sous-jacent représenté par le nœud. Pour plus d’informations, consultez [étendre le nœud Connexions SharePoint dans Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="example"></a>Exemple
 L’exemple de code suivant montre comment obtenir des données pour la liste SharePoint sous-jacente représentée par un nœud de liste dans **Explorateur de serveurs**. Par défaut, les nœuds liste disposent d’un élément de menu contextuel **afficher dans le navigateur** sur lequel vous pouvez cliquer pour ouvrir les listes dans un navigateur Web. Cet exemple étend la liste des nœuds en ajoutant un affichage dans l’élément de menu contextuel **de Visual Studio** qui ouvre les listes directement dans Visual Studio. Le code accède aux données de liste pour le nœud afin d’obtenir l’URL de la liste à ouvrir dans Visual Studio.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]

 Cet exemple utilise le service de projet SharePoint pour obtenir l' <xref:EnvDTE.DTE> objet utilisé pour ouvrir des listes dans Visual Studio. Pour plus d’informations sur le service de projet SharePoint, consultez [utiliser le service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

 Pour plus d’informations sur les tâches de base pour créer une extension pour un nœud SharePoint, consultez [Comment : étendre un nœud SharePoint dans Explorateur de serveurs](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple nécessite des références aux assemblys suivants :

- EnvDTE

- Microsoft. VisualStudio. SharePoint

- Microsoft. VisualStudio. SharePoint. Explorer. extensions

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Déployer l’extension
 Pour déployer l’extension de **Explorateur de serveurs** , créez un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Étendre le nœud Connexions SharePoint dans Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Procédure : étendre un nœud SharePoint dans Explorateur de serveurs](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Utiliser le service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
