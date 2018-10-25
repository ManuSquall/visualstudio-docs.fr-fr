---
title: 'Comment : ajouter une propriété à des projets SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c956da1df5507d2efecb3ff72f034d54fb377eb5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49898408"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>Comment : ajouter une propriété à des projets SharePoint
  Vous pouvez utiliser une extension de projet pour ajouter une propriété à un projet SharePoint. La propriété apparaît dans le **propriétés** fenêtre lorsque le projet est sélectionné dans **l’Explorateur de solutions**.  
  
 Les étapes suivantes supposent que vous avez déjà créé une extension de projet. Pour plus d’informations, consultez [Comment : créer une extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### <a name="to-add-a-property-to-a-sharepoint-project"></a>Pour ajouter une propriété à un projet SharePoint  
  
1.  Définir une classe avec une propriété publique qui représente la propriété que vous ajoutez à des projets SharePoint. Si vous souhaitez ajouter plusieurs propriétés, vous pouvez définir toutes les propriétés dans la même classe ou dans différentes classes.  
  
2.  Dans le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> méthode de votre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implémentation, gérez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> événements de la *projectService* paramètre.  
  
3.  Dans le Gestionnaire d’événements pour le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> événement, ajoutez une instance de votre classe de propriétés pour le <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> collection l’arguments du paramètre d’événement.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment ajouter deux propriétés à des projets SharePoint. Une propriété conserve ses données dans le fichier projet des options utilisateur (le *. csproj.user* fichier ou *. vbproj.user* fichier). L’autre propriété conserve ses données dans le fichier projet (*.csproj* fichier ou *.vbproj* fichier).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]  
  
### <a name="understand-the-code"></a>Comprendre le code  
 Pour vous assurer que la même instance de la `CustomProjectProperties` classe est utilisée chaque fois que le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> événement se produit, l’exemple de code ajoute l’objet de propriétés pour le <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriété de la projet la première fois que cet événement se produit. Le code récupère cet objet chaque fois que cet événement se produit à nouveau. Pour plus d’informations sur l’utilisation de la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriété pour associer les données avec les projets, consultez [associer des données personnalisées à SharePoint extensions d’outils](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Pour conserver les modifications apportées aux valeurs de propriété, le **définir** accesseurs pour les propriétés utilisent les API suivantes :  
  
- `CustomUserFileProperty` utilise le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> propriété pour enregistrer sa valeur dans le fichier projet des options utilisateur.  
  
- `CustomProjectFileProperty` utilise le <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> méthode pour enregistrer sa valeur dans le fichier projet.  
  
  Pour plus d’informations sur la conservation des données dans ces fichiers, consultez [enregistrer les données dans les extensions du système de projet SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specify-the-behavior-of-custom-properties"></a>Spécifier le comportement des propriétés personnalisées  
 Vous pouvez définir la façon dont une propriété personnalisée apparaît et se comporte de la **propriétés** fenêtre en appliquant des attributs à partir de la <xref:System.ComponentModel> la définition de propriété de l’espace de noms. Les attributs suivants sont utiles dans de nombreux scénarios :  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Spécifie le nom de la propriété qui s’affiche dans le **propriétés** fenêtre.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Spécifie la chaîne de description qui apparaît dans la partie inférieure de la **propriétés** fenêtre lorsque la propriété est sélectionnée.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Spécifie la valeur par défaut de la propriété.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Spécifie une conversion personnalisée entre la chaîne qui est affichée dans le **propriétés** fenêtre et une valeur de propriété de non-chaîne.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Spécifie un éditeur personnalisé à utiliser pour modifier la propriété.  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cet exemple nécessite des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint
-    
-   Microsoft.VisualStudio.Shell
-     
-   Microsoft.VisualStudio.Shell.Interop
-     
-   Microsoft.VisualStudio.Shell.Interop.8.0
-     
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Déployer l’extension  
 Pour déployer l’extension, créez un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi
 [Étendre des projets SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Comment : créer une extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Comment : ajouter un élément de menu contextuel à des projets SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Étendre le système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  
