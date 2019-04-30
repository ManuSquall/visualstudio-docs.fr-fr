---
title: Référence schéma d’élément de projet SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
- SafeControls element
- SafeControl element
- .spdata files
- ExtensionData element
- FeatureProperties element
- ProjectOutputFile element
- Files element
- ProjectItemFolder element
- ProjectItemFile element
- ExtensionDataItem element
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bc15ff5c384ec63f99ed50a5f3c700efd7ba3c18
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007717"
---
# <a name="sharepoint-project-item-schema-reference"></a>Référence de schéma élément de projet SharePoint
  Visual Studio utilise le schéma d’élément de projet SharePoint pour valider le contenu de *.spdata* fichiers. Un *.spdata* fichier Spécifie le contenu et le comportement d’un élément de projet SharePoint. Pour plus d’informations sur le contenu des éléments de projet SharePoint, consultez [créer des modèles de projet pour les éléments de projet SharePoint et de modèles d’élément](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Le schéma d’élément de projet SharePoint est nommé ProjectItemModelSchema.xsd et est installé par défaut dans %Program Files (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas.

 L’élément racine est le [ProjectItem](../sharepoint/projectitem-element.md) élément. Le tableau suivant décrit tous les éléments définis par le schéma.

|Élément|Description|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Représente une collection d’éléments de données personnalisés qui sont associés à l’élément de projet SharePoint.|
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Représente un élément de données personnalisé qui est associé à l’élément de projet SharePoint, au format clé/valeur. La clé et la valeur doivent être des chaînes.|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Représente une collection de valeurs de propriété qui sont incluses avec une fonctionnalité lorsqu’elle est déployée vers SharePoint. Après le déployée d’une fonctionnalité, vous pouvez accéder les valeurs de propriété dans votre code.|
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Représente une propriété personnalisée qui est incluse avec une fonctionnalité lorsqu’elle est déployée vers SharePoint. Après le déployée d’une fonctionnalité, vous pouvez accéder à la propriété dans votre code.|
|[Fichiers](../sharepoint/files-element.md)|Spécifie les fichiers à déployer avec l’élément de projet SharePoint, comme un fichier d’élément de fonctionnalité ou la sortie d’un projet.|
|[ProjectItem](../sharepoint/projectitem-element.md)|Représente un élément de projet SharePoint.|
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Représente un fichier SharePoint, par exemple de fichier d’élément de fonctionnalité, à inclure avec l’élément de projet lorsqu’elle est déployée vers SharePoint.|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Représente un dossier mappé.|
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Représente la sortie d’un projet à inclure avec l’élément de projet lorsqu’elle est déployée vers SharePoint.|
|[SafeControl](../sharepoint/safecontrol-element.md)|Représente un contrôle ASPX ou un composant WebPart qui est désigné comme sécurisé pour un utilisateur d’accéder sur n’importe quelle page ASPX du site SharePoint.|
|[SafeControls](../sharepoint/safecontrols-element.md)|Représente une collection de contrôles ASPX et les composants WebPart qui sont désignés comme sécurisés pour tous les utilisateurs à accéder sur n’importe quelle page ASPX du site SharePoint.|

## <a name="see-also"></a>Voir aussi
- [Créer des modèles d’élément et les modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
