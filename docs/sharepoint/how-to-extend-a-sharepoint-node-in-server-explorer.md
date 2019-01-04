---
title: 'Procédure : Étendre un nœud SharePoint dans l’Explorateur de serveurs | Microsoft Docs'
ms.date: 02/02/2017
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
ms.openlocfilehash: e39d108d78782413cd120e2a00b97f85784004b7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53940425"
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>Procédure : Étendre un nœud SharePoint dans l’Explorateur de serveurs
  Vous pouvez étendre les nœuds sous le **connexions SharePoint** nœud **Explorateur de serveurs**. Cela est utile lorsque vous souhaitez ajouter des nœuds enfants, les éléments de menu contextuel ou les propriétés à un nœud existant. Pour plus d’informations, consultez [étendre le nœud Connexions SharePoint dans l’Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>Pour étendre un nœud SharePoint dans l’Explorateur de serveurs  
  
1.  Créez un projet de bibliothèque de classes.  
  
2.  Ajoutez des références aux assemblys suivants :  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
3.  Définissez une classe qui implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  
  
4.  Appliquez l’attribut <xref:System.ComponentModel.Composition.ExportAttribute> à la classe. Cet attribut permet à Visual Studio détecter et charger votre <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> implémentation. Passer le <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> type au constructeur d’attribut.  
  
5.  Appliquez l’attribut <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> à la classe. Cet attribut spécifie l’identificateur de chaîne pour le type de nœud que vous souhaitez étendre.  
  
     Pour spécifier les types de nœuds intégrés fournis par Visual Studio, passez une des valeurs d’énumération suivantes au constructeur d’attribut :  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Utilisez ces valeurs pour spécifier des nœuds de connexion de site (nœuds qui affichent les URL de site), nœuds de site ou tous les autres nœuds parents dans **Explorateur de serveurs**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Utilisez ces valeurs pour spécifier un des nœuds intégrés qui représentent un composant individuel sur un site SharePoint, tel qu’un nœud qui représente une liste, un champ ou un type de contenu.  
  
6.  Dans votre implémentation de la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> (méthode), utilisez les membres de la *nodeType* paramètre à ajouter des fonctionnalités au nœud. Ce paramètre est un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> objet qui fournit l’accès aux événements définis dans le <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> interface. Par exemple, vous pouvez gérer les événements suivants :  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: Gérez cet événement pour ajouter des nœuds enfants au nœud. Pour plus d'informations, voir [Procédure : Ajouter un nœud SharePoint personnalisé à l’Explorateur de serveurs](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: Gérez cet événement pour ajouter un élément de menu contextuel personnalisé au nœud.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: Gérez cet événement pour ajouter des propriétés personnalisées au nœud. Les propriétés s’affichent dans le **propriétés** fenêtre lorsque le nœud est sélectionné.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment créer deux types d’extensions de nœud :  
  
- Une extension qui ajoute un élément de menu contextuel aux nœuds de site SharePoint. Lorsque vous cliquez sur l’élément de menu, il affiche le nom du nœud qui a été cliqué.  
  
- Une extension qui ajoute une propriété personnalisée nommée **ContosoExampleProperty** à chaque nœud qui représente un champ nommé **corps**.  
  
  [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs#9)]
  [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb#9)]  
  
  Cette extension ajoute une propriété de chaîne modifiable pour les nœuds. Vous pouvez également créer des propriétés personnalisées qui affichent des données en lecture seule à partir du serveur SharePoint. Pour obtenir un exemple qui montre comment effectuer cette opération, consultez [procédure pas à pas : Étendre l’Explorateur de serveurs pour afficher des WebParts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cet exemple nécessite des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
-   System.Windows.Forms  
  
## <a name="deploy-the-extension"></a>Déployer l’extension  
 Pour déployer le **Explorateur de serveurs** extension, créez un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi
 [Guide pratique pour Ajouter un nœud SharePoint personnalisé à l’Explorateur de serveurs](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Étendre le nœud Connexions SharePoint dans l’Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Procédure pas à pas : Étendre l’Explorateur de serveurs pour afficher des WebParts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Associer des données personnalisées avec les extensions d’outils SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
