---
title: "ProjectItemFile Element"
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
  - "ProjectItemFile element"
ms.assetid: 68d44d31-625a-4f02-b998-463ac0ffb2ef
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# ProjectItemFile Element
  Représente un fichier SharePoint, tel que le fichier d'élément de fonctionnalité, à inclure avec l'élément de projet lors de son déploiement sur SharePoint.  
  
## Syntaxe  
  
```  
<ProjectItemFile Source = "Name of the file"  
    Target = "Deployment path of the file"  
    Type = "Type of deployment for the file" />  
```  
  
## Type  
 **ProjectItemFileType**  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|**Source**|Attribut **xs:string** requis.<br /><br /> Nom du fichier à déployer avec l'élément de projet.|  
|**Target**|Attribut **xs:string** facultatif.<br /><br /> Chemin d'accès où le fichier sera déployé dans SharePoint, par rapport au dossier racine de déploiement.  Le dossier racine de déploiement est déterminé par le type de déploiement spécifié par l'attribut **Type**.  Si l'attribut **Target** n'est pas spécifié, le fichier sera déployé dans un dossier avec le nom spécifié dans l'attribut **Source**.<br /><br /> Pour plus d'informations, consultez les descriptions pour les propriétés **Deployment PathDeployment Root** d'éléments de projet SharePoint dans [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Attribut **xs:string** requis.<br /><br /> Le type de déploiement pour le fichier.  Pour plus d'informations sur les valeurs possibles, consultez la description pour la propriété **Deployment Type** d'éléments de projet SharePoint dans [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Fichiers](../sharepoint/files-element.md)|Spécifie les fichiers à inclure avec l'élément de projet SharePoint lorsque ce dernier est déployé vers SharePoint.|  
  
## Notes  
 Les fichiers SharePoint généralement référencés dans les éléments **ProjectItemFile** incluent des fichiers d'éléments de fonctionnalité \(Elements.xml\), des fichiers de schéma associés aux définitions de listes \(Schema.xml\) et des fichiers de définition associés aux WebParts \(.webpart\).  
  
## Informations sur les éléments  
  
|||  
|-|-|  
|**Espace de noms**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Nom du schéma**|Schéma d'élément de projet SharePoint|  
|**Fichier de validation**|ProjectItemModelSchema.xsd|  
|**Peut être vide**|Non|  
  
## Voir aussi  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  