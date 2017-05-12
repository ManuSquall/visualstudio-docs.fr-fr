---
title: "FeatureProperty Element"
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
ms.assetid: 36a771a6-98d0-4a40-a278-d76baea82452
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# FeatureProperty Element
  Représente une propriété personnalisée incluse avec une fonctionnalité lors de son déploiement sur SharePoint.  Après avoir déployé une fonctionnalité, vous pouvez accéder à la propriété dans votre code.  
  
## Syntaxe  
  
```  
<FeatureProperty Key = "Key of the property value"  
    Value = "Property value" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|**Key**|Attribut **xs:string** requis.<br /><br /> Clé utilisée pour stocker et récupérer la valeur de propriété.  Chaque propriété doit avoir une clé qui est unique dans la fonctionnalité.|  
|**Value**|Attribut **xs:string** requis.<br /><br /> Valeur de la propriété.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Représente une collection de valeurs de propriété incluses avec une fonctionnalité lors de son déploiement sur SharePoint.|  
  
## Notes  
 Pour plus d'informations sur ces propriétés des fonctionnalités, consultez [Fourniture d'informations de création de packages et de déploiement dans des éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
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
  
  