---
title: "Comment : ajouter une propriété à des projets SharePoint | Documents Microsoft"
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
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a4318550e74d5324195de173659d96abaf952979
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>Comment : ajouter une propriété à des projets SharePoint
  Vous pouvez utiliser une extension de projet pour ajouter une propriété à un projet SharePoint. La propriété apparaît dans le **propriétés** fenêtre lorsque le projet est sélectionné dans **l’Explorateur de solutions**.  
  
 Les étapes suivantes supposent que vous avez déjà créé une extension de projet. Pour plus d’informations, consultez [Comment : créer une Extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### <a name="to-add-a-property-to-a-sharepoint-project"></a>Pour ajouter une propriété à un projet SharePoint  
  
1.  Définissez une classe avec une propriété publique qui représente la propriété que vous ajoutez à des projets SharePoint. Si vous souhaitez ajouter plusieurs propriétés, vous pouvez définir toutes les propriétés dans la même classe ou dans différentes classes.  
  
2.  Dans le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> méthode de votre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implémentation, gérez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> l’événement de la *projectService* paramètre.  
  
3.  Dans le Gestionnaire d’événements pour le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> événement, ajoutez une instance de votre classe de propriétés pour le <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> collection du paramètre d’arguments de l’événement.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment ajouter deux propriétés à des projets SharePoint. Une propriété conserve ses données dans le fichier d’options utilisateur projet (la. les fichiers csproj.user ou. vbproj.user fichier). L’autre propriété conserve ses données dans le fichier projet (fichier .csproj ou .vbproj).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]  
  
### <a name="understanding-the-code"></a>Fonctionnement du Code  
 Pour vous assurer que la même instance de la `CustomProjectProperties` classe est utilisée chaque fois que le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> événement se produit, l’exemple de code ajoute l’objet de propriétés dans le <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriété du projet la première fois que cet événement se produit. Le code récupère cet objet chaque fois que cet événement se produit à nouveau. Pour plus d’informations sur l’utilisation de la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriété à associer des données avec les projets, consultez [associer des données personnalisées à des Extensions d’outils SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Pour conserver les modifications apportées aux valeurs de propriété, le **définir** accesseurs pour les propriétés utilisent les API suivantes :  
  
-   `CustomUserFileProperty`utilise le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> propriété à sauvegarder sa valeur dans le fichier projet d’options utilisateur.  
  
-   `CustomProjectFileProperty`utilise le <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> méthode enregistrer sa valeur dans le fichier projet.  
  
 Pour plus d’informations sur les données persistantes dans ces fichiers, consultez [l’enregistrement des données dans les Extensions du système de projet SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>Spécifier le comportement des propriétés personnalisées  
 Vous pouvez définir la façon dont une propriété personnalisée apparaît et se comporte de la **propriétés** fenêtre en appliquant des attributs à partir de la <xref:System.ComponentModel> la définition de propriété de l’espace de noms. Les attributs suivants sont utiles dans de nombreux scénarios :  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Spécifie le nom de la propriété qui s’affiche dans le **propriétés** fenêtre.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Spécifie la chaîne de description qui apparaît au bas de la **propriétés** fenêtre lorsque la propriété est sélectionnée.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Spécifie la valeur par défaut de la propriété.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Spécifie une conversion personnalisée entre la chaîne qui est affichée dans le **propriétés** fenêtre et une valeur de propriété de type non chaîne.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Spécifie un éditeur personnalisé à utiliser pour modifier la propriété.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.Shell  
  
-   Microsoft.VisualStudio.Shell.Interop  
  
-   Microsoft.VisualStudio.Shell.Interop.8.0  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Déploiement de l’Extension  
 Pour déployer l’extension, créez un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déploiement d’Extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des projets SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Comment : créer une Extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Comment : ajouter un élément de Menu contextuel à des projets SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Extension du système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  