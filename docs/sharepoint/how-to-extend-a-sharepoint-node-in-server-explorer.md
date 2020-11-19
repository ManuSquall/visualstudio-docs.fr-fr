---
title: 'Procédure : étendre un nœud SharePoint dans Explorateur de serveurs | Microsoft Docs'
description: Découvrez comment étendre un nœud SharePoint dans Explorateur de serveurs à l’aide du nœud Connexions SharePoint.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: bad90701d19f97036ecba55bb2901739ad30b200
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903544"
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>Procédure : étendre un nœud SharePoint dans Explorateur de serveurs
  Vous pouvez étendre des nœuds sous le nœud **Connexions SharePoint** dans **Explorateur de serveurs**. Cela est utile lorsque vous souhaitez ajouter de nouveaux nœuds enfants, des éléments de menu contextuel ou des propriétés à un nœud existant. Pour plus d’informations, consultez [étendre le nœud Connexions SharePoint dans Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>Pour étendre un nœud SharePoint dans Explorateur de serveurs

1. Créez un projet de bibliothèque de classes.

2. Ajoutez des références aux assemblys suivants :

    - Microsoft. VisualStudio. SharePoint

    - Microsoft. VisualStudio. SharePoint. Explorer. extensions

    - System.ComponentModel.Composition

3. Définissez une classe qui implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.

4. Appliquez l’attribut <xref:System.ComponentModel.Composition.ExportAttribute> à la classe. Cet attribut permet à Visual Studio de découvrir et de charger votre <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> implémentation. Transmettez le <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> type au constructeur d’attribut.

5. Appliquez l’attribut <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> à la classe. Cet attribut spécifie l’identificateur de chaîne pour le type de nœud que vous souhaitez étendre.

     Pour spécifier les types de nœuds intégrés fournis par Visual Studio, transmettez l’une des valeurs d’énumération suivantes au constructeur d’attribut :

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Utilisez ces valeurs pour spécifier les nœuds de connexion de site (nœuds qui affichent les URL de site), les nœuds de site ou tous les autres nœuds parents dans **Explorateur de serveurs**.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Utilisez ces valeurs pour spécifier l’un des nœuds intégrés qui représentent un composant individuel sur un site SharePoint, tel qu’un nœud qui représente une liste, un champ ou un type de contenu.

6. Dans votre implémentation de la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> méthode, utilisez les membres du paramètre *NodeType* pour ajouter des fonctionnalités au nœud. Ce paramètre est un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> objet qui fournit l’accès aux événements définis dans l' <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> interface. Par exemple, vous pouvez gérer les événements suivants :

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: Gérer cet événement pour ajouter de nouveaux nœuds enfants au nœud. Pour plus d’informations, consultez [procédure : ajouter un nœud SharePoint personnalisé à Explorateur de serveurs](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: Gérer cet événement pour ajouter un élément de menu contextuel personnalisé au nœud.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: Gérer cet événement pour ajouter des propriétés personnalisées au nœud. Les propriétés s’affichent dans le **propriétés** fenêtre lorsque le nœud est sélectionné.

## <a name="example"></a>Exemple
 L’exemple de code suivant montre comment créer deux types d’extensions de nœuds différents :

- Extension qui ajoute un élément de menu contextuel aux nœuds de site SharePoint. Lorsque vous cliquez sur l’élément de menu, il affiche le nom du nœud sur lequel l’utilisateur a cliqué.

- Extension qui ajoute une propriété personnalisée nommée **ContosoExampleProperty** à chaque nœud qui représente un champ nommé **Body**.

  [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs#9)]
  [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb#9)]

  Cette extension ajoute une propriété de chaîne modifiable aux nœuds. Vous pouvez également créer des propriétés personnalisées qui affichent des données en lecture seule à partir du serveur SharePoint. Pour obtenir un exemple qui montre comment procéder, consultez [procédure pas à pas : étendre Explorateur de serveurs pour afficher des WebParts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple nécessite des références aux assemblys suivants :

- Microsoft. VisualStudio. SharePoint

- Microsoft. VisualStudio. SharePoint. Explorer. extensions

- System.ComponentModel.Composition

- System.Windows.Forms

## <a name="deploy-the-extension"></a>Déployer l’extension
 Pour déployer l’extension de **Explorateur de serveurs** , créez un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Procédure : ajouter un nœud SharePoint personnalisé à Explorateur de serveurs](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [Étendre le nœud Connexions SharePoint dans Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Procédure pas à pas : étendre Explorateur de serveurs pour afficher des composants WebPart](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Associer des données personnalisées à des extensions d’outils SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
