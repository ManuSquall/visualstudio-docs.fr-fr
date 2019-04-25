---
title: Enregistrement des données dans les Extensions du système de projet SharePoint | Microsoft Docs
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60082761"
---
# <a name="save-data-in-extensions-of-the-sharepoint-project-system"></a>Enregistrer les données dans les extensions du système de projet SharePoint
  Lorsque vous étendez le système de projet SharePoint, vous pouvez enregistrer les données de chaîne qui persiste après la fermeture d’un projet SharePoint. Les données sont généralement associé à un élément de projet particulier ou le projet lui-même.

 Si vous avez des données que vous ne souhaitez pas conserver, vous pouvez ajouter les données à n’importe quel objet dans le modèle objet des outils SharePoint qui implémente le <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> interface. Pour plus d’informations, consultez [associer des données personnalisées à SharePoint extensions d’outils](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

## <a name="save-data-that-is-associated-with-a-project-item"></a>Enregistrer les données qui sont associées à un élément de projet
 Lorsque vous avez des données qui sont associées à un élément de projet SharePoint particulier, telles que la valeur d’une propriété que vous ajoutez à un élément de projet, vous pouvez enregistrer les données à la *.spdata* fichier pour l’élément de projet. Pour ce faire, utilisez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriété d’un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objet. Les données que vous ajoutez à cette propriété sont enregistrées dans le **ExtensionData** élément dans le *.spdata* fichier pour l’élément de projet. Pour plus d’informations, consultez [ExtensionData, élément](../sharepoint/extensiondata-element.md).

 L’exemple de code suivant montre comment utiliser le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriété pour enregistrer la valeur d’une propriété de chaîne qui est définie dans un type d’élément de projet SharePoint personnalisé. Pour voir cet exemple dans le contexte d’un exemple plus complet, consultez [Comment : Ajouter une propriété à un type d’élément de projet SharePoint personnalisé](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]

## <a name="save-data-that-is-associated-with-a-project"></a>Enregistrer les données qui sont associées à un projet
 Si vous avez des données au niveau du projet, telles que la valeur d’une propriété que vous ajoutez à des projets SharePoint, vous pouvez enregistrer les données dans le fichier projet (le *.csproj* fichier ou *.vbproj* fichier) ou l’option d’utilisateur de projet fichier (le *. csproj.user* fichier ou *. vbproj.user* fichier). Le fichier que vous choisissez d’enregistrer les données dans dépend de la façon dont vous souhaitez les données à utiliser :

- Si vous souhaitez que les données soient disponibles pour tous les développeurs qui ouvrent le projet SharePoint, enregistrer les données dans le fichier projet. Ce fichier est archivé toujours aux bases de données du contrôle source, par conséquent, les données dans ce fichier seront disponibles à d’autres développeurs qui extraient le projet.

- Si vous souhaitez que les données soient disponibles uniquement pour les développeurs en cours qui a le projet SharePoint ouvert dans Visual Studio, enregistrer les données dans le fichier projet des options utilisateur. Ce fichier est généralement désactivée aux bases de données du contrôle source, les données dans ce fichier n’est pas disponibles à d’autres développeurs qui extraient le projet.

### <a name="save-data-to-the-project-file"></a>Enregistrer les données dans le fichier projet
 Pour enregistrer les données dans le fichier projet, vous devez convertir un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> de l’objet à un <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> objet, puis utiliser le <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> (méthode). L’exemple de code suivant montre comment utiliser cette méthode pour enregistrer la valeur d’une propriété de projet dans le fichier projet. Pour voir cet exemple dans le contexte d’un exemple plus complet, consultez [Comment : Ajouter une propriété à des projets SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]

 Pour plus d’informations sur la conversion <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objets à d’autres types dans le modèle objet automation Visual Studio ou le modèle objet d’intégration, consultez [effectuer des conversions entre types de système de projet SharePoint et d’autres types de projet Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

### <a name="save-data-to-the-project-user-option-file"></a>Enregistrer les données dans le fichier projet des options utilisateur
 Pour enregistrer les données dans le fichier d’options de projet utilisateur, utilisez la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> propriété d’un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objet. L’exemple de code suivant montre comment utiliser cette propriété pour enregistrer la valeur d’une propriété de projet dans le fichier projet des options utilisateur. Pour voir cet exemple dans le contexte d’un exemple plus complet, consultez [Comment : Ajouter une propriété à des projets SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]

## <a name="see-also"></a>Voir aussi
- [Étendre le système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Associer des données personnalisées avec les extensions d’outils SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [Effectuer une conversion entre les types de système de projet SharePoint et d’autres types de projet Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
