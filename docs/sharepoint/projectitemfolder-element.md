---
title: "ProjectItemFolder Element"
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
  - "ProjectItemFolder element"
ms.assetid: 15b386dd-f523-4425-9fcc-517325681358
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# ProjectItemFolder Element
  Représente un dossier mappé.  
  
## Syntaxe  
  
```  
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"  
    Type = "Type of deployment for the mapped folder" />  
```  
  
## Type  
 **ProjectItemFolderType**  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|**Target**|Attribut **xs:string** requis.<br /><br /> Chemin d'accès du dossier dans l'installation SharePoint à laquelle le dossier mappé correspond, par rapport au dossier racine de déploiement.  Le dossier racine de déploiement est déterminé par le type de déploiement spécifié par l'attribut **Type**.<br /><br /> Pour plus d'informations, consultez les descriptions pour les propriétés **Deployment PathDeployment Root** d'éléments de projet SharePoint dans [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Attribut **xs:string** requis.<br /><br /> Le type de déploiement pour le dossier mappé.  Pour plus d'informations sur les valeurs possibles, consultez la description pour la propriété **Deployment Type** d'éléments de projet SharePoint dans [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Représente un élément de projet SharePoint.  Il s'agit de l'élément racine obligatoire du fichier .spdata.|  
  
## Notes  
 Pour plus d'informations sur les dossiers mappés, consultez [Comment : ajouter et supprimer des dossiers mappés](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
## Informations sur les éléments  
  
|||  
|-|-|  
|**Espace de noms**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Nom du schéma**|Schéma d'élément de projet SharePoint|  
|**Fichier de validation**|ProjectItemModelSchema.xsd|  
|**Peut être vide**|Non|  
  
## Voir aussi  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Comment : ajouter et supprimer des dossiers mappés](../sharepoint/how-to-add-and-remove-mapped-folders.md)  
  
  