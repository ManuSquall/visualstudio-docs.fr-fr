---
title: "Référence du schéma élément de projet SharePoint | Documents Microsoft"
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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 99a2471919483f02a9f58a35ad164527a12a39c5
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="sharepoint-project-item-schema-reference"></a>Référence du schéma d'élément de projet SharePoint
  Visual Studio utilise le schéma d’élément de projet SharePoint pour valider le contenu des fichiers .spdata. Un fichier .spdata Spécifie le contenu et le comportement d’un élément de projet SharePoint. Pour plus d’informations sur le contenu des éléments de projet SharePoint, consultez [création de modèles d’élément et les modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Le schéma d’élément de projet SharePoint est nommé ProjectItemModelSchema.xsd et est installé par défaut dans %Program Files (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas.  
  
 L’élément racine est le [ProjectItem](../sharepoint/projectitem-element.md) élément. Le tableau suivant décrit tous les éléments définis par le schéma.  
  
|Élément|Description|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Représente une collection d’éléments de données personnalisés qui sont associés à l’élément de projet SharePoint.|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Représente un élément de données personnalisé qui est associé à l’élément de projet SharePoint, au format clé/valeur. La clé et la valeur doivent être des chaînes.|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Représente une collection de valeurs de propriété qui sont inclus avec une fonctionnalité lorsqu’elle est déployée vers SharePoint. Après le déployée d’une fonctionnalité, vous pouvez accéder les valeurs de propriété dans votre code.|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Représente une propriété personnalisée qui est incluse avec une fonctionnalité lorsqu’elle est déployée vers SharePoint. Après le déployée d’une fonctionnalité, vous pouvez accéder à la propriété dans votre code.|  
|[Fichiers](../sharepoint/files-element.md)|Spécifie les fichiers à déployer avec l’élément de projet SharePoint, par exemple un fichier d’élément de fonctionnalité ou la sortie d’un projet.|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Représente un élément de projet SharePoint.|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Représente un fichier de SharePoint, comme fichier d’élément de fonctionnalité, à inclure avec l’élément de projet lorsqu’il est déployé dans SharePoint.|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Représente un dossier mappé.|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Représente la sortie d’un projet à inclure avec l’élément de projet lorsqu’il est déployé dans SharePoint.|  
|[SafeControl](../sharepoint/safecontrol-element.md)|Représente un contrôle ASPX ou un WebPart désigné comme sécurisé pour tout utilisateur d’accéder sur n’importe quelle page ASPX sur le site SharePoint.|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Représente une collection de contrôles ASPX et les composants WebPart qui sont désignés comme sécurisés pour tout utilisateur d’accéder sur n’importe quelle page ASPX sur le site SharePoint.|  
  
## <a name="see-also"></a>Voir aussi  
 [Création de modèles d’élément et de modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)  
  
  