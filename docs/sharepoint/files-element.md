---
title: "Files Element"
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
  - "Files element"
ms.assetid: 3c611d5b-28f1-48a7-a068-63e01fa2f3aa
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Files Element
  Spécifie les fichiers à déployer avec l'élément de projet SharePoint, tels que les fichiers d'éléments de fonctionnalité et la sortie des projets non\-SharePoint dépendants.  
  
## Syntaxe  
  
```  
<Files>  
  <ProjectItemFile.../>  
  <ProjectOutputFile.../>  
</Files>  
```  
  
## Type  
 **FileCollectionType**  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Élément **ProjectItemFileType** facultatif.<br /><br /> Représente un fichier SharePoint, tel que le fichier d'élément de fonctionnalité, à inclure avec l'élément de projet lors de son déploiement sur SharePoint.|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Élément **ProjectOutputFileType** facultatif.<br /><br /> Représente la sortie d'un projet à inclure avec l'élément de projet lors de son déploiement sur SharePoint.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Représente un élément de projet SharePoint.  Il s'agit de l'élément racine obligatoire du fichier .spdata.|  
  
## Informations sur les éléments  
  
|||  
|-|-|  
|**Espace de noms**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Nom du schéma**|Schéma d'élément de projet SharePoint|  
|**Fichier de validation**|ProjectItemModelSchema.xsd|  
|**Peut être vide**|Non|  
  
## Voir aussi  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  