---
title: "Enregistrement des données dans les Extensions du système de projet SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 56cdfb95de6f0e5f8644ea3c73daacbf90e33a97
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="saving-data-in-extensions-of-the-sharepoint-project-system"></a>Enregistrement des données dans les extensions du système de projet SharePoint
  Lorsque vous étendez le système de projet SharePoint, vous pouvez enregistrer les données de chaîne qui persiste après la fermeture d’un projet SharePoint. Les données sont généralement associé liée un élément de projet particulier ou le projet lui-même.  
  
 Si vous avez des données que vous ne souhaitez pas conserver, vous pouvez ajouter les données à n’importe quel objet dans le modèle objet des outils SharePoint qui implémente le <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> interface. Pour plus d’informations, consultez [associer des données personnalisées à des Extensions d’outils SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## <a name="saving-data-that-is-associated-with-a-project-item"></a>L’enregistrement de données qui est associé avec un élément de projet  
 Lorsque vous disposez de données qui sont associées à un élément de projet SharePoint particulier, tel que la valeur d’une propriété que vous ajoutez à un élément de projet, vous pouvez enregistrer les données dans le fichier .spdata pour l’élément de projet. Pour ce faire, utilisez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriété d’un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objet. Les données que vous ajoutez à cette propriété sont enregistrées dans le **ExtensionData** élément dans le fichier .spdata pour l’élément de projet. Pour plus d’informations, consultez [ExtensionData (élément)](../sharepoint/extensiondata-element.md).  
  
 L’exemple de code suivant montre comment utiliser le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriété pour enregistrer la valeur d’une propriété de chaîne qui est définie dans un type d’élément de projet SharePoint personnalisé. Pour voir cet exemple dans le contexte d’un exemple plus complet, consultez [Comment : ajouter une propriété à un Type d’élément de projet personnalisé SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]  
  
## <a name="saving-data-that-is-associated-with-a-project"></a>L’enregistrement de données qui est associé un projet  
 Lorsque vous disposez des données au niveau du projet, telles que la valeur d’une propriété que vous ajoutez à des projets SharePoint, vous pouvez enregistrer les données pour le fichier de projet (le fichier .csproj ou .vbproj) ou le fichier d’options utilisateur projet (la. fichier de csproj.user ou. vbproj.user fichier). Le fichier que vous choisissez d’enregistrer les données dans dépend de comment vous souhaitez que les données à utiliser :  
  
-   Si vous souhaitez que les données soient disponibles pour tous les développeurs qui ouvrent le projet SharePoint, enregistrer les données dans le fichier projet. Ce fichier est archivé toujours aux bases de données du contrôle source, par conséquent, les données de ce fichier seront disponibles à d’autres développeurs qui extraient le projet.  
  
-   Si vous souhaitez que les données soient disponibles uniquement pour le nom du développeur qui a le projet SharePoint dans Visual Studio d’ouvrir, enregistrer les données dans le fichier projet d’options utilisateur. Ce fichier est généralement désactivée aux bases de données du contrôle source, donc les données dans ce fichier ne sont pas disponibles à d’autres développeurs qui extraient le projet.  
  
### <a name="saving-data-to-the-project-file"></a>L’enregistrement de données dans le fichier de projet  
 Pour enregistrer les données dans le fichier projet, vous devez convertir un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> de l’objet à un <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> objet, puis utiliser le <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> (méthode). L’exemple de code suivant montre comment utiliser cette méthode pour enregistrer la valeur d’une propriété de projet dans le fichier projet. Pour voir cet exemple dans le contexte d’un exemple plus complet, consultez [Comment : ajouter une propriété à des projets SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]  
  
 Pour plus d’informations sur la conversion <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> à d’autres types dans le modèle objet automation Visual Studio ou le modèle objet d’intégration, voir [conversion entre système de Types de projet SharePoint et d’autres Types de projet Visual Studio ](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
### <a name="saving-data-to-the-project-user-option-file"></a>L’enregistrement des données au fichier projet utilisateur Option  
 Pour enregistrer les données au fichier projet utilisateur option, utilisez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> propriété d’un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objet. L’exemple de code suivant montre comment utiliser cette propriété pour enregistrer la valeur d’une propriété de projet dans le fichier projet d’options utilisateur. Pour voir cet exemple dans le contexte d’un exemple plus complet, consultez [Comment : ajouter une propriété à des projets SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]  
  
## <a name="see-also"></a>Voir aussi  
 [Extension du système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Associer des données personnalisées à des Extensions d’outils SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Conversion entre des types d’un système de projet SharePoint et d’autres types de projets Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)  
  
  