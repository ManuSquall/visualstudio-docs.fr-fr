---
title: "ProjectItem Element"
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
  - "ProjectItem element"
ms.assetid: df588235-12a1-4798-bc56-ef81843de17f
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# ProjectItem Element
  Représente un élément de projet SharePoint.  Il s'agit de l'élément racine obligatoire du fichier .spdata.  
  
## Syntaxe  
  
```  
<ProjectItem DefaultFile = "File that opens in the editor when you open the project item"  
    FeatureReceiverClass = "Class that implements a feature receiver for the project item"  
    FeatureReceiverAssembly = "Assembly that defines a feature receiver for the project item"  
    SupportedTrustLevels = "Trust levels that the project item supports"  
    SupportedDeploymentScopes = "Deployment scopes that the project item supports"  
    Type="Identifier for the project item">  
  <Files>...</Files>  
  <ProjectItemFolder>...</ProjectItemFolder>  
  <SafeControls>...</SafeControls>  
  <FeatureProperties>...</FeatureProperties>  
  <ExtensionData>...</ExtensionData>  
</ProjectItem>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|**DefaultFile**|Attribut **xs:string** facultatif.<br /><br /> Chemin d'accès relatif, y compris le nom de fichier, du fichier qui s'affiche dans l'éditeur Visual Studio lorsque vous ouvrez l'élément de projet SharePoint dans l'**Explorateur de solutions**.  Le chemin d'accès est relatif par rapport au dossier qui contient le fichier .spdata.|  
|**FeatureReceiverClass**|Attribut **xs:string** facultatif.<br /><br /> Nom qualifié complet d'une classe de récepteur de fonctionnalité associée à cet élément de projet SharePoint.  Pour plus d'informations sur les récepteurs, consultez [Fourniture d'informations de création de packages et de déploiement dans des éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|**FeatureReceiverAssembly**|Attribut **xs:string** facultatif.<br /><br /> Spécifie le nom qualifié complet d'un assembly qui définit un récepteur de fonctionnalité pour cet élément de projet SharePoint.  Pour plus d'informations sur les récepteurs, consultez [Fourniture d'informations de création de packages et de déploiement dans des éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  Pour plus d'informations sur les noms d'assemblys qualifiés complets, consultez [Noms d'assemblys](http://msdn.microsoft.com/library/8f8c2c90-f15d-400e-87e7-a757e4f04d0e).|  
|**SupportedTrustLevels**|Attribut **xs:string** facultatif.<br /><br /> Spécifie les niveaux de confiance que cet élément de projet SharePoint prend en charge.  Cette valeur peut être l'une des chaînes suivantes : Sandboxed, FullTrust ou All.  La valeur Tout spécifie Sandboxed et FullTrust.<br /><br /> Dans un type d'élément de projet SharePoint personnalisé, la valeur de cet attribut correspond à la valeur que vous assignez à la propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> dans votre implémentation de la méthode <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>.  Si vous spécifiez une valeur différente pour cet attribut, Visual Studio remplace la valeur afin qu'elle spécifie le même niveau de confiance que celui spécifié dans la propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A>.|  
|**SupportedDeploymentScopes**|Attribut **xs:string** facultatif.<br /><br /> Spécifie les portées de déploiement que cet élément de projet SharePoint prend en charge.  Cette valeur est une chaîne délimitée par des virgules qui contient une ou plusieurs des chaînes suivantes : Farm, Site, Web, WebApplication ou Package.  Par exemple, « Web, Site ».<br /><br /> Dans un type d'élément de projet SharePoint personnalisé, la valeur de cet attribut correspond à la valeur que vous assignez à la propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> dans votre implémentation de la méthode <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>.  Si vous spécifiez une valeur différente pour cet attribut, Visual Studio remplace la valeur afin qu'elle spécifie le même niveau de confiance que celui spécifié dans la propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A>.|  
|**Type**|Attribut **xs:string** requis.<br /><br /> Identificateur de l'élément de projet SharePoint.  Dans un type d'élément de projet SharePoint personnalisé, l'identificateur est la chaîne que vous passez au <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  Pour plus d'informations, consultez [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).<br /><br /> Pour une liste des identificateurs pour les éléments de projet SharePoint intégrés inclus avec Visual Studio, consultez [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Élément facultatif.<br /><br /> Représente une collection d'éléments de données personnalisés associés à l'élément de projet SharePoint.<br /><br /> Vous ne pouvez inclure qu'un seul élément **ExtensionData**.|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Élément facultatif.<br /><br /> Représente une collection de valeurs de propriété incluses avec une fonctionnalité lors de son déploiement sur SharePoint.<br /><br /> Vous ne pouvez inclure qu'un seul élément **FeatureProperties**.|  
|[Fichiers](../sharepoint/files-element.md)|Élément **FileCollectionType** facultatif.<br /><br /> Spécifie les fichiers à déployer avec l'élément de projet SharePoint, tels que les fichiers d'éléments de fonctionnalité et la sortie des projets non\-SharePoint dépendants.<br /><br /> Vous devez inclure un élément **Files** ou **ProjectItemFolder**, mais pas les deux.|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Élément **ProjectItemFolderType** facultatif.<br /><br /> Représente un dossier mappé.<br /><br /> Vous devez inclure un élément **Files** ou **ProjectItemFolder**, mais pas les deux.|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Élément facultatif.<br /><br /> Représente une collection de contrôles ASPX et de composants WebPart désignés comme sécurisés pour tout utilisateur souhaitant y accéder sur n'importe quelle page ASPX du site SharePoint.<br /><br /> Vous ne pouvez inclure qu'un seul élément **SafeControls**.|  
  
### Éléments parents  
 Aucun  
  
## Informations sur les éléments  
  
|||  
|-|-|  
|**Espace de noms**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Nom du schéma**|Schéma d'élément de projet SharePoint|  
|**Fichier de validation**|ProjectItemModelSchema.xsd|  
|**Peut être vide**|Non|  
  
## Voir aussi  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  