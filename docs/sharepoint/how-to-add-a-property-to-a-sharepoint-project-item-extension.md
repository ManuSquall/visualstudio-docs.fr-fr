---
title: 'Comment : ajouter une propriété à une Extension d’élément de projet SharePoint | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d80881d69addd2d1f92bdf2c9b47c6f528945d30
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>Comment : ajouter une propriété à une extension d’élément de projet SharePoint
  Vous pouvez utiliser une extension d’élément de projet pour ajouter une propriété à n’importe quel élément de projet SharePoint est déjà installé dans Visual Studio. La propriété apparaît dans le **propriétés** fenêtre lorsque l’élément de projet est sélectionné dans **l’Explorateur de solutions**.  
  
 Les étapes suivantes supposent que vous avez déjà créé une extension d’élément de projet. Pour plus d’informations, consultez [Comment : créer une Extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
### <a name="to-add-a-property-to-a-project-item-extension"></a>Pour ajouter une propriété à une extension d’élément de projet  
  
1.  Définissez une classe avec une propriété publique qui représente la propriété que vous ajoutez à un type d’élément de projet. Si vous souhaitez ajouter plusieurs propriétés à un type d’élément de projet, vous pouvez définir toutes les propriétés dans la même classe ou dans différentes classes.  
  
2.  Dans le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> méthode de votre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implémentation, gérez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> l’événement de la *projectItemType* paramètre.  
  
3.  Dans le Gestionnaire d’événements pour le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> événement, ajoutez une instance de votre classe de propriétés pour le <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> collection du paramètre d’arguments de l’événement.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment ajouter une propriété nommée **exemple de propriété** à l’élément de projet de récepteur d’événements.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]  
  
### <a name="understanding-the-code"></a>Fonctionnement du Code  
 Pour vous assurer que la même instance de la `CustomProperties` classe est utilisée chaque fois que le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> événement se produit, l’exemple de code ajoute l’objet de propriétés dans le <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriété de l’heure de l’élément du premier projet cet événement se produit. Le code récupère cet objet chaque fois que cet événement se produit à nouveau. Pour plus d’informations sur l’utilisation de la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriété à associer des données aux éléments de projet, consultez [associer des données personnalisées à des Extensions d’outils SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Pour conserver les modifications apportées à la valeur de propriété, le **définir** accesseur pour `ExampleProperty` enregistre la nouvelle valeur à la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriété de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objet associé à la propriété. Pour plus d’informations sur l’utilisation de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriété pour rendre persistantes les données avec les éléments de projet, consultez [l’enregistrement des données dans les Extensions du système de projet SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>Spécifier le comportement des propriétés personnalisées  
 Vous pouvez définir la façon dont une propriété personnalisée apparaît et se comporte de la **propriétés** fenêtre en appliquant des attributs à partir de la <xref:System.ComponentModel> la définition de propriété de l’espace de noms. Les attributs suivants sont utiles dans de nombreux scénarios :  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Spécifie le nom de la propriété qui s’affiche dans le **propriétés** fenêtre.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Spécifie la chaîne de description qui apparaît au bas de la **propriétés** fenêtre lorsque la propriété est sélectionnée.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Spécifie la valeur par défaut de la propriété.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Spécifie une conversion personnalisée entre la chaîne qui est affichée dans le **propriétés** fenêtre et une valeur de propriété de type non chaîne.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Spécifie un éditeur personnalisé à utiliser pour modifier la propriété.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Ces exemples nécessitent un projet de bibliothèque de classes avec des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Déploiement de l’Extension  
 Pour déployer l’extension, créez un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déploiement d’Extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer une Extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [Comment : ajouter un élément de Menu contextuel à une Extension d’élément de projet SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Étendre des éléments de projet SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Procédure pas à pas : extension d’un type d’élément de projet SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  