---
title: 'Procédure : ajouter un nœud SharePoint personnalisé à Explorateur de serveurs | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 26a2ea6a7ccbfcc80275b55f9230f1a3152ab545
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86017047"
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>Procédure : ajouter un nœud SharePoint personnalisé à Explorateur de serveurs
  Vous pouvez ajouter des nœuds personnalisés sous le nœud **Connexions SharePoint** dans **Explorateur de serveurs**. Cela est utile lorsque vous souhaitez afficher des composants SharePoint supplémentaires qui ne s’affichent pas dans **Explorateur de serveurs** par défaut. Pour plus d’informations, consultez [étendre le nœud Connexions SharePoint dans Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

 Pour ajouter un nœud personnalisé, commencez par créer une classe qui définit le nouveau nœud. Créez ensuite une extension qui ajoute le nœud en tant qu’enfant d’un nœud existant.

### <a name="to-define-the-new-node"></a>Pour définir le nouveau nœud

1. Créez un projet de bibliothèque de classes.

2. Ajoutez des références aux assemblys suivants :

    - Microsoft. VisualStudio. SharePoint

    - Microsoft. VisualStudio. SharePoint. Explorer. extensions

    - System.ComponentModel.Composition

    - System.Drawing

3. Définissez une classe qui implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.

4. Ajoutez les attributs suivants à la classe :

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Cet attribut permet à Visual Studio de découvrir et de charger votre <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> implémentation. Transmettez le <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> type au constructeur d’attribut.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>. Dans une définition de nœud, cet attribut spécifie l’identificateur de chaîne pour le nouveau nœud. Nous vous recommandons d’utiliser le format *nom*de l’entreprise. *nom du nœud* pour vous assurer que tous les nœuds ont un identificateur unique.

5. Dans votre implémentation de la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> méthode, utilisez les membres du paramètre *TypeDefinition* pour configurer le comportement du nouveau nœud. Ce paramètre est un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> objet qui fournit l’accès aux événements définis dans l' <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> interface.

     L’exemple de code suivant montre comment définir un nouveau nœud. Cet exemple suppose que votre projet contient une icône nommée CustomChildNodeIcon en tant que ressource incorporée.

     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#6)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#6)]

### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>Pour ajouter le nouveau nœud en tant qu’enfant d’un nœud existant

1. Dans le même projet que votre définition de nœud, créez une classe qui implémente l' <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interface.

2. Appliquez l’attribut <xref:System.ComponentModel.Composition.ExportAttribute> à la classe. Cet attribut permet à Visual Studio de découvrir et de charger votre <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> implémentation. Transmettez le <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> type au constructeur d’attribut.

3. Appliquez l’attribut <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> à la classe. Dans une extension de nœud, cet attribut spécifie l’identificateur de chaîne pour le type de nœud que vous souhaitez étendre.

     Pour spécifier les types de nœuds intégrés fournis par Visual Studio, transmettez l’une des valeurs d’énumération suivantes au constructeur d’attribut :

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Utilisez ces valeurs pour spécifier les nœuds de connexion de site (nœuds qui affichent les URL de site), les nœuds de site ou tous les autres nœuds parents dans **Explorateur de serveurs**.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Utilisez ces valeurs pour spécifier l’un des nœuds intégrés qui représentent un composant individuel sur un site SharePoint, tel qu’un nœud qui représente une liste, un champ ou un type de contenu.

4. Dans votre implémentation de la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> méthode, gérez l' <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> événement du <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> paramètre.

5. Dans le <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> Gestionnaire d’événements, ajoutez le nouveau nœud à la collection de nœuds enfants de l' <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> objet exposé par le paramètre d’arguments d’événement.

     L’exemple de code suivant montre comment ajouter le nouveau nœud en tant qu’enfant du nœud de site SharePoint dans **Explorateur de serveurs**.

     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#7)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#7)]

## <a name="complete-example"></a>Exemple complet
 L’exemple de code suivant fournit le code complet permettant de définir un nœud simple et de l’ajouter en tant qu’enfant du nœud de site SharePoint dans **Explorateur de serveurs**.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#5)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#5)]

## <a name="compiling-the-code"></a>Compilation du code
 Cet exemple suppose que votre projet contient une icône nommée CustomChildNodeIcon en tant que ressource incorporée. Cet exemple nécessite également des références aux assemblys suivants :

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

- System.Drawing

## <a name="deploy-the-extension"></a>Déployer l’extension
 Pour déployer l’extension de **Explorateur de serveurs** , créez un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Étendre le nœud Connexions SharePoint dans Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Procédure : étendre un nœud SharePoint dans Explorateur de serveurs](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Procédure pas à pas : étendre Explorateur de serveurs pour afficher des composants WebPart](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
