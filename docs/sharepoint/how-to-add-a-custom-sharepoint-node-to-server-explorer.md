---
title: "Comment : ajouter un nœud SharePoint personnalisé à l’Explorateur de serveurs | Documents Microsoft"
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
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
ms.assetid: b992a192-f926-45e6-9416-85ddfe1061d0
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7aa3ccbeaae231b0abf4885c592addc586ccfb28
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>Comment : ajouter un nœud SharePoint personnalisé à l'Explorateur de serveurs
  Vous pouvez ajouter des nœuds personnalisés sous le **connexions SharePoint** nœud **l’Explorateur de serveurs**. Cela est utile lorsque vous souhaitez afficher des composants SharePoint supplémentaires qui ne sont pas affichés dans **l’Explorateur de serveurs** par défaut. Pour plus d’informations, consultez [extension du nœud Connexions SharePoint dans l’Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
 Pour ajouter un nœud personnalisé, tout d’abord créer une classe qui définit le nouveau nœud. Créez ensuite une extension qui ajoute le nœud en tant qu’enfant d’un nœud existant.  
  
### <a name="to-define-the-new-node"></a>Pour définir le nouveau nœud  
  
1.  Créez un projet de bibliothèque de classes.  
  
2.  Ajoutez des références aux assemblys suivants :  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
    -   System.Drawing  
  
3.  Définissez une classe qui implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.  
  
4.  Ajoutez les attributs suivants à la classe :  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. Cet attribut permet à Visual Studio de découvrir et de charger votre <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> implémentation. Passez le <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> type au constructeur d’attribut.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>. Dans une définition de nœud, cet attribut spécifie l’identificateur de chaîne pour le nouveau nœud. Nous vous recommandons d’utiliser le format *nom de la société*. *nom du nœud* pour vous assurer que tous les nœuds ont un identificateur unique.  
  
5.  Dans votre implémentation de la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> (méthode), utilisez les membres de la *typeDefinition* paramètre pour configurer le comportement du nouveau nœud. Ce paramètre est un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> objet qui fournit l’accès aux événements définis dans le <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> interface.  
  
     L’exemple de code suivant montre comment définir un nouveau nœud. Cet exemple suppose que votre projet contient une icône nommée CustomChildNodeIcon en tant que ressource incorporée.  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#6)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#6)]  
  
### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>Pour ajouter le nouveau nœud en tant qu’enfant d’un nœud existant  
  
1.  Dans le même projet que votre définition de nœud, créez une classe qui implémente le <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interface.  
  
2.  Ajouter le <xref:System.ComponentModel.Composition.ExportAttribute> à la classe d’attributs. Cet attribut permet à Visual Studio de découvrir et de charger votre <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> implémentation. Passez le <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> type au constructeur d’attribut.  
  
3.  Ajouter le <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> à la classe d’attributs. Dans une extension de nœud, cet attribut spécifie l’identificateur de chaîne pour le type de nœud que vous souhaitez étendre.  
  
     Pour spécifier les types de nœuds intégrés fournis par Visual Studio, passez l’une des valeurs d’énumération suivantes au constructeur d’attribut :  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: À utiliser ces valeurs pour spécifier des nœuds de connexion de site (nœuds qui affichent les URL de site), nœuds de site ou tous les autres nœuds parents dans **l’Explorateur de serveurs**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Utilisez ces valeurs pour spécifier un des nœuds intégrés qui représentent un composant individuel sur un site SharePoint, tel qu’un nœud qui représente une liste, un champ ou un type de contenu.  
  
4.  Dans votre implémentation de la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> méthode, gérez le <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> l’événement de la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> paramètre.  
  
5.  Dans le <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> Gestionnaire d’événements, ajoutez le nouveau nœud à la collection de nœuds enfants de la <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> objet exposé par le paramètre arguments d’événement.  
  
     L’exemple de code suivant montre comment ajouter le nouveau nœud en tant qu’enfant du nœud de site SharePoint dans **l’Explorateur de serveurs**.  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#7)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#7)]  
  
## <a name="complete-example"></a>Exemple complet  
 L’exemple de code suivant fournit le code complet pour définir un nœud simple et l’ajouter en tant qu’enfant du nœud de site SharePoint dans **l’Explorateur de serveurs**.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#5)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#5)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple suppose que votre projet contient une icône nommée CustomChildNodeIcon en tant que ressource incorporée. Cet exemple nécessite également des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
-   System.Drawing  
  
## <a name="deploying-the-extension"></a>Déploiement de l’Extension  
 Pour déployer le **l’Explorateur de serveurs** extension, créez un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déploiement d’Extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Extension du nœud Connexions SharePoint dans l’Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Comment : étendre un nœud SharePoint dans l’Explorateur de serveurs](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Procédure pas à pas : extension de l’Explorateur de serveurs pour afficher des composants WebPart](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  