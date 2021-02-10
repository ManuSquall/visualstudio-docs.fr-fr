---
title: 'Comment : ajouter une propriété à des projets SharePoint | Microsoft Docs'
description: Utilisez une extension de projet pour ajouter une propriété à un projet SharePoint. Une propriété apparaît dans la Fenêtre Propriétés lorsque vous sélectionnez le projet dans Explorateur de solutions.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cde9235ffb7c692240c8f16ea0e93f49c79f002e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934869"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>Comment : ajouter une propriété à des projets SharePoint
  Vous pouvez utiliser une extension de projet pour ajouter une propriété à un projet SharePoint. La propriété s’affiche dans la fenêtre **Propriétés** lorsque le projet est sélectionné dans **Explorateur de solutions**.

 Les étapes suivantes supposent que vous avez déjà créé une extension de projet. Pour plus d’informations, consultez [Comment : créer une extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

### <a name="to-add-a-property-to-a-sharepoint-project"></a>Pour ajouter une propriété à un projet SharePoint

1. Définissez une classe avec une propriété publique qui représente la propriété que vous ajoutez aux projets SharePoint. Si vous souhaitez ajouter plusieurs propriétés, vous pouvez définir toutes les propriétés dans la même classe ou dans des classes différentes.

2. Dans la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> méthode de votre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implémentation, gérez l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> événement du paramètre *ProjectService* .

3. Dans le gestionnaire d’événements pour l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> événement, ajoutez une instance de votre classe de propriétés à la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> collection du paramètre d’arguments d’événement.

## <a name="example"></a>Exemple
 L’exemple de code suivant montre comment ajouter deux propriétés aux projets SharePoint. Une propriété rend ses données persistantes dans le fichier d’options utilisateur du projet (fichier *. csproj. User* ou *. vbproj. User* ). L’autre propriété rend ses données persistantes dans le fichier projet (fichier *. csproj* ou *. vbproj* ).

 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]

### <a name="understand-the-code"></a>Comprendre le code
 Pour vous assurer que la même instance de la `CustomProjectProperties` classe est utilisée chaque fois que l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> événement se produit, l’exemple de code ajoute l’objet de propriétés à la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriété du projet la première fois que cet événement se produit. Le code récupère cet objet chaque fois que cet événement se reproduit. Pour plus d’informations sur l’utilisation <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> de la propriété pour associer des données à des projets, consultez [associer des données personnalisées à des extensions d’outils SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Pour conserver les modifications apportées aux valeurs de propriété, les accesseurs **Set** des propriétés utilisent les API suivantes :

- `CustomUserFileProperty` utilise la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> propriété pour enregistrer sa valeur dans le fichier d’options utilisateur du projet.

- `CustomProjectFileProperty` utilise la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> méthode pour enregistrer sa valeur dans le fichier projet.

  Pour plus d’informations sur la persistance des données dans ces fichiers, consultez [enregistrer des données dans les extensions du système de projet SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Spécifier le comportement des propriétés personnalisées
 Vous pouvez définir la façon dont une propriété personnalisée apparaît et se comporte dans la fenêtre **Propriétés** en appliquant des attributs de l' <xref:System.ComponentModel> espace de noms à la définition de propriété. Les attributs suivants sont utiles dans de nombreux scénarios :

- <xref:System.ComponentModel.DisplayNameAttribute>: Spécifie le nom de la propriété qui s’affiche dans la fenêtre **Propriétés** .

- <xref:System.ComponentModel.DescriptionAttribute>: Spécifie la chaîne de description qui apparaît en bas de la fenêtre **Propriétés** lorsque la propriété est sélectionnée.

- <xref:System.ComponentModel.DefaultValueAttribute>: Spécifie la valeur par défaut de la propriété.

- <xref:System.ComponentModel.TypeConverterAttribute>: Spécifie une conversion personnalisée entre la chaîne affichée dans la fenêtre **Propriétés** et une valeur de propriété qui n’est pas une chaîne.

- <xref:System.ComponentModel.EditorAttribute>: Spécifie un éditeur personnalisé à utiliser pour modifier la propriété.

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple nécessite des références aux assemblys suivants :

- Microsoft. VisualStudio. SharePoint

- Microsoft. VisualStudio. Shell

- Microsoft. VisualStudio. Shell. Interop

- Microsoft. VisualStudio. Shell. Interop. 8.0

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Déployer l’extension
 Pour déployer l’extension, créez un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Étendre des projets SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Comment : créer une extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Comment : ajouter un élément de menu contextuel à des projets SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Étendre le système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
