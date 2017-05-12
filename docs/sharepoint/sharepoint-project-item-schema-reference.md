---
title: "SharePoint Project Item Schema Reference"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "FeatureProperty element"
  - "SafeControls element"
  - "SafeControl element"
  - ".spdata files"
  - "ExtensionData element"
  - "FeatureProperties element"
  - "ProjectOutputFile element"
  - "Files element"
  - "ProjectItemFolder element"
  - "ProjectItemFile element"
  - "ExtensionDataItem element"
  - "ProjectItem element"
ms.assetid: 12b63cbc-bf94-4175-bfa8-2117943d00d1
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# SharePoint Project Item Schema Reference
  Visual Studio utilise le schéma d'élément de projet SharePoint pour valider le contenu de fichiers .spdata.  Un fichier .spdata spécifie le contenu et le comportement d'un élément de projet SharePoint.  Pour plus d'informations au sujet du contenu des éléments de projet SharePoint, consultez [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Le schéma d'élément de projet SharePoint est nommé ProjectItemModelSchema.xsd et est installé par défaut dans %Program Files \(x86\)%\\Microsoft Visual Studio 11.0\\Xml\\Schemas.  
  
 L'élément racine est l'élément [ProjectItem](../sharepoint/projectitem-element.md).  Le tableau suivant décrit tous les éléments définis par le schéma.  
  
|Élément|Description|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Représente une collection d'éléments de données personnalisés associés à l'élément de projet SharePoint.|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Représente un élément de données personnalisé associé à l'élément de projet SharePoint, au format clé\/valeur.  La clé et la valeur doivent être des chaînes.|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Représente une collection de valeurs de propriété incluses avec une fonctionnalité lors de son déploiement sur SharePoint.  Après avoir déployé une fonctionnalité, vous pouvez accéder aux valeurs de propriété dans votre code.|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Représente une propriété personnalisée incluse avec une fonctionnalité lors de son déploiement sur SharePoint.  Après avoir déployé une fonctionnalité, vous pouvez accéder à la propriété dans votre code.|  
|[Fichiers](../sharepoint/files-element.md)|Spécifie les fichiers à déployer avec l'élément de projet SharePoint, tels qu'un fichier d'élément de fonctionnalité ou la sortie d'un projet.|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Représente un élément de projet SharePoint.|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Représente un fichier SharePoint, tel que le fichier d'élément de fonctionnalité, à inclure avec l'élément de projet lors de son déploiement sur SharePoint.|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Représente un dossier mappé.|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Représente la sortie d'un projet à inclure avec l'élément de projet lors de son déploiement sur SharePoint.|  
|[SafeControl](../sharepoint/safecontrol-element.md)|Représente un contrôle ASPX ou un composant WebPart désigné comme sécurisé pour tout utilisateur souhaitant y accéder sur n'importe quelle page ASPX du site SharePoint.|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Représente une collection de contrôles ASPX et de composants WebPart désignés comme sécurisés pour tout utilisateur souhaitant y accéder sur n'importe quelle page ASPX du site SharePoint.|  
  
## Voir aussi  
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)  
  
  