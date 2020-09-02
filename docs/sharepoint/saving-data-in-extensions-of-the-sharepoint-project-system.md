---
title: Enregistrement des données dans les extensions du système de projet SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 52b04490a646c7ced27d4a2d7f2344e27cbbae8b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62827243"
---
# <a name="save-data-in-extensions-of-the-sharepoint-project-system"></a>Enregistrer des données dans les extensions du système de projet SharePoint
  Lorsque vous étendez le système de projet SharePoint, vous pouvez enregistrer les données de chaîne qui persistent après la fermeture d’un projet SharePoint. Les données sont généralement associées à un élément de projet particulier ou au projet lui-même.

 Si vous avez des données qui n’ont pas besoin d’être rendues persistantes, vous pouvez ajouter les données à n’importe quel objet dans le modèle objet des outils SharePoint qui implémente l' <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> interface. Pour plus d’informations, consultez [associer des données personnalisées à des extensions d’outils SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

## <a name="save-data-that-is-associated-with-a-project-item"></a>Enregistrer les données associées à un élément de projet
 Quand vous avez des données qui sont associées à un élément de projet SharePoint particulier, telles que la valeur d’une propriété que vous ajoutez à un élément de projet, vous pouvez enregistrer les données dans le fichier *. les données* de l’élément de projet. Pour ce faire, utilisez la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriété d’un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objet. Les données que vous ajoutez à cette propriété sont enregistrées dans l’élément **ExtensionData** du fichier *. les données* de l’élément de projet. Pour plus d’informations, consultez [élément ExtensionData](../sharepoint/extensiondata-element.md).

 L’exemple de code suivant montre comment utiliser la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriété pour enregistrer la valeur d’une propriété de type chaîne qui est définie dans un type d’élément de projet SharePoint personnalisé. Pour voir cet exemple dans le contexte d’un exemple plus complet, consultez [Comment : ajouter une propriété à un type d’élément de projet SharePoint personnalisé](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]

## <a name="save-data-that-is-associated-with-a-project"></a>Enregistrer les données associées à un projet
 Quand vous avez des données au niveau du projet, telles que la valeur d’une propriété que vous ajoutez aux projets SharePoint, vous pouvez enregistrer les données dans le fichier projet (fichier *. csproj* ou *. vbproj* ) ou dans le fichier d’options utilisateur du projet (fichier *. csproj. User* ou *. vbproj. User* ). Le fichier dans lequel vous choisissez d’enregistrer les données dépend de la façon dont vous souhaitez utiliser les données :

- Si vous souhaitez que les données soient disponibles pour tous les développeurs qui ouvrent le projet SharePoint, enregistrez les données dans le fichier projet. Ce fichier étant toujours archivé dans les bases de données de contrôle de code source, les données de ce fichier sont disponibles pour les autres développeurs qui extrayent le projet.

- Si vous souhaitez que les données soient disponibles uniquement pour le développeur actuel qui a ouvert le projet SharePoint dans Visual Studio, enregistrez les données dans le fichier d’options utilisateur du projet. Ce fichier n’étant généralement pas archivé dans les bases de données de contrôle de code source, les données de ce fichier ne sont pas disponibles pour les autres développeurs qui extrayent le projet.

### <a name="save-data-to-the-project-file"></a>Enregistrer des données dans le fichier projet
 Pour enregistrer des données dans le fichier projet, convertissez un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objet en <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> objet, puis utilisez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> méthode. L’exemple de code suivant montre comment utiliser cette méthode pour enregistrer la valeur d’une propriété de projet dans le fichier projet. Pour voir cet exemple dans le contexte d’un exemple plus complet, consultez [Comment : ajouter une propriété à des projets SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]

 Pour plus d’informations sur <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> la conversion d’objets en d’autres types dans le modèle objet Automation Visual Studio ou le modèle objet d’intégration, consultez [conversion entre des types système de projet SharePoint et d’autres types de projets Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

### <a name="save-data-to-the-project-user-option-file"></a>Enregistrer des données dans le fichier d’options utilisateur du projet
 Pour enregistrer des données dans le fichier d’options utilisateur du projet, utilisez la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> propriété d’un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objet. L’exemple de code suivant montre comment utiliser cette propriété pour enregistrer la valeur d’une propriété de projet dans le fichier d’options utilisateur du projet. Pour voir cet exemple dans le contexte d’un exemple plus complet, consultez [Comment : ajouter une propriété à des projets SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]

## <a name="see-also"></a>Voir aussi
- [Étendre le système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Associer des données personnalisées à des extensions d’outils SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [Effectuer une conversion entre des types système de projet SharePoint et d’autres types de projets Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
