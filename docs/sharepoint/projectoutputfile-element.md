---
title: "ProjectOutputFile Element | Microsoft Docs"
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
  - "ProjectOutputFile element"
ms.assetid: 52a017bf-e19c-49e4-bb8f-cbe6958195c2
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# ProjectOutputFile Element
  Représente la sortie d'un projet séparé à inclure avec l'élément de projet lorsque ce dernier est déployé vers SharePoint.  
  
## Syntaxe  
  
```  
<ProjectOutputFile ProjectId = "GUID of the project"  
    ProjectPath = "Relative path of the project"  
    Target = "Deployment path of the project output"  
    Type = "Type of deployment for the project output" />  
```  
  
## Type  
 **ProjectOutputFileType**  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|**ProjectId**|Attribut **xs:string** requis.<br /><br /> GUID du projet dépendant comportant la sortie que vous souhaitez inclure.  Cela correspond à l'élément **ProjectGuid** dans le fichier projet dépendant.|  
|**ProjectPath**|Attribut **xs:string** requis.<br /><br /> Chemin d'accès relatif, y compris le nom de fichier projet, du projet dépendant comportant la sortie que vous souhaitez inclure.  Ce chemin d'accès est relatif par rapport au dossier racine du projet SharePoint qui contient l'élément de projet SharePoint.|  
|**Target**|Attribut **xs:string** facultatif.<br /><br /> Chemin d'accès où la sortie de projet dépendant doit être déployée sur le serveur SharePoint, par rapport au dossier racine de déploiement.  Le dossier racine de déploiement est déterminé par le type de déploiement spécifié par l'attribut **Type**.<br /><br /> Pour plus d'informations, consultez les descriptions pour les propriétés **Deployment PathDeployment Root** d'éléments de projet SharePoint dans [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Attribut **xs:string** requis.<br /><br /> Le type de déploiement à utiliser pour la sortie du projet dépendant.  Pour plus d'informations sur les valeurs possibles, consultez la description pour la propriété **Deployment Type** d'éléments de projet SharePoint dans [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Fichiers](../sharepoint/files-element.md)|Spécifie les fichiers à inclure avec l'élément de projet SharePoint lorsque ce dernier est déployé vers SharePoint.|  
  
## Notes  
 Utilisez l'élément **ProjectOutputFile** pour inclure la sortie d'un projet dans le déploiement de l'élément de projet SharePoint.  Vous pouvez spécifier un projet différent, ou le même projet qui contient l'élément de projet.  Pour plus d'informations, consultez [Fourniture d'informations de création de packages et de déploiement dans des éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## Informations sur les éléments  
  
|||  
|-|-|  
|**Espace de noms**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Nom du schéma**|Schéma d'élément de projet SharePoint|  
|**Fichier de validation**|ProjectItemModelSchema.xsd|  
|**Peut être vide**|Non|  
  
## Voir aussi  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Fourniture d'informations de création de packages et de déploiement dans des éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  