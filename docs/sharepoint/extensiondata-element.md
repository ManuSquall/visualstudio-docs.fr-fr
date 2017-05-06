---
title: "ExtensionData Element"
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
  - "ExtensionData element"
ms.assetid: caf6843b-dcf5-4688-a9eb-a424aae1beab
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# ExtensionData Element
  Représente une collection d'éléments de données personnalisés associés à l'élément de projet SharePoint.  
  
## Syntaxe  
  
```  
<ExtensionData>  
  <ExtensionDataItem.../>  
</ExtensionData>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Élément facultatif.<br /><br /> Représente un élément de données personnalisé associé à l'élément de projet SharePoint, au format clé\/valeur.  La clé et la valeur doivent être des chaînes.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Représente un élément de projet SharePoint.  Il s'agit de l'élément racine obligatoire du fichier .spdata.|  
  
## Notes  
 Lorsque vous associez des données personnalisées à un élément de projet SharePoint à l'aide de la propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> d'un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>, Visual Studio enregistre les données sur l'élément **ExtensionData** dans le fichier .spdata pour l'élément de projet.  Pour plus d'informations, consultez [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## Informations sur les éléments  
  
|||  
|-|-|  
|**Espace de noms**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Nom du schéma**|Schéma d'élément de projet SharePoint|  
|**Fichier de validation**|ProjectItemModelSchema.xsd|  
|**Peut être vide**|Non|  
  
## Voir aussi  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  