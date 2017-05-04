---
title: "ExtensionDataItem Element | Microsoft Docs"
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
  - "ExtensionDataItem element"
ms.assetid: 6a5fe7eb-b433-42dc-bd50-4882b780e2fb
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# ExtensionDataItem Element
  Représente un élément de données personnalisé associé à l'élément de projet SharePoint, au format clé\/valeur.  La clé et la valeur doivent être des chaînes.  
  
## Syntaxe  
  
```  
<ExtensionDataItem Key = "Key of the data item"  
    Value = "Value of the data item" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|**Key**|Attribut **xs:string** requis.<br /><br /> Clé utilisée pour stocker et récupérer l'élément de données.|  
|**Value**|Attribut **xs:string** requis.<br /><br /> Valeur de l'élément de données.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Représente une collection d'éléments de données personnalisés associés à l'élément de projet SharePoint.|  
  
## Notes  
 Lorsque vous associez des données personnalisées à un élément de projet SharePoint à l'aide de la propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> d'un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>, Visual Studio enregistre les données sur un nouvel élément **ExtensionDataItem** dans le fichier .spdata pour l'élément de projet.  Pour plus d'informations, consultez [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## Informations sur les éléments  
  
|||  
|-|-|  
|**Espace de noms**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Nom du schéma**|Schéma d'élément de projet SharePoint|  
|**Fichier de validation**|ProjectItemModelSchema.xsd|  
|**Peut être vide**|Non|  
  
## Voir aussi  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  