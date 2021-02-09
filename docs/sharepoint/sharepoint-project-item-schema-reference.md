---
title: Référence du schéma d’élément de projet SharePoint | Microsoft Docs
description: Consultez une vue d’ensemble de la référence de schéma XML de l’élément de projet SharePoint (ProjectItemModelSchema. xsd), qui est utilisée pour valider le contenu des fichiers. de données.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 466bc68ca002914b64698d7cd87f98ff276bfc0e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892279"
---
# <a name="sharepoint-project-item-schema-reference"></a>Référence du schéma d’élément de projet SharePoint
  Visual Studio utilise le schéma d’élément de projet SharePoint pour valider le contenu des fichiers *. resdonnées* . Un fichier *. resdonnées* spécifie le contenu et le comportement d’un élément de projet SharePoint. Pour plus d’informations sur le contenu des éléments de projet SharePoint, consultez [créer des modèles d’élément et des modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Le schéma d’élément de projet SharePoint est appelé ProjectItemModelSchema. xsd et est installé par défaut dans% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ Xml\Schemas.

 L’élément racine est l’élément [ProjectItem](../sharepoint/projectitem-element.md) . Le tableau suivant décrit tous les éléments définis par le schéma.

|Élément|Description|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Représente une collection d’éléments de données personnalisés associés à l’élément de projet SharePoint.|
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Représente un élément de données personnalisé associé à l’élément de projet SharePoint, au format clé/valeur. La clé et la valeur doivent être des chaînes.|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Représente une collection de valeurs de propriétés qui sont incluses avec une fonctionnalité lorsqu’elle est déployée sur SharePoint. Une fois qu’une fonctionnalité a été déployée, vous pouvez accéder aux valeurs de propriété dans votre code.|
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Représente une propriété personnalisée qui est incluse avec une fonctionnalité lorsqu’elle est déployée sur SharePoint. Une fois qu’une fonctionnalité a été déployée, vous pouvez accéder à la propriété dans votre code.|
|[Fichiers](../sharepoint/files-element.md)|Spécifie les fichiers à déployer avec l’élément de projet SharePoint, tel qu’un fichier d’élément de fonctionnalité ou la sortie d’un projet.|
|[ProjectItem](../sharepoint/projectitem-element.md)|Représente un élément de projet SharePoint.|
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Représente un fichier SharePoint, tel qu’un fichier d’élément de fonctionnalité, à inclure avec l’élément de projet lorsqu’il est déployé sur SharePoint.|
|[ProjectItemFolder,](../sharepoint/projectitemfolder-element.md)|Représente un dossier mappé.|
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Représente la sortie d’un projet à inclure avec l’élément de projet lorsqu’il est déployé sur SharePoint.|
|[SafeControl](../sharepoint/safecontrol-element.md)|Représente un contrôle ASPX ou un composant WebPart qui est désigné comme sécurisé pour tout utilisateur qui peut accéder à n’importe quelle page ASPX sur le site SharePoint.|
|[SafeControls](../sharepoint/safecontrols-element.md)|Représente une collection de contrôles ASPX et WebParts désignés comme sécurisés pour n’importe quel utilisateur à accéder à n’importe quelle page ASPX sur le site SharePoint.|

## <a name="see-also"></a>Voir aussi
- [Créer des modèles d’élément et des modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
