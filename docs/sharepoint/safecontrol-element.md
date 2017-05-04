---
title: "SafeControl Element | Microsoft Docs"
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
  - "SafeControl element"
ms.assetid: e7c61749-fc73-412c-be30-4af5ff2a9fd2
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# SafeControl Element
  Représente un contrôle ASPX ou un composant WebPart désigné comme sécurisé pour tout utilisateur souhaitant y accéder sur n'importe quelle page ASPX du site SharePoint.  
  
## Syntaxe  
  
```  
<SafeControl Assembly = "Name of assembly that contains the safe control"  
    IsSafe = "true/false"  
    IsSafeAgainstScript = "true/false"  
    Name = "Name of this safe control entry"  
    Namespace = "Namespace of the safe control"  
    TypeName = "Type of the safe control" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|**Assembly**|Attribut **xs:string** facultatif.<br /><br /> Nom de l'assembly dans lequel le contrôle ASPX ou le WebPart est défini.  Par défaut, cet attribut utilise le paramètre remplaçable **$SharePoint.Project.AssemblyFullName$** pour le nom de l'assembly.  Pour plus d'informations, consultez [Paramètres remplaçables](../sharepoint/replaceable-parameters.md).|  
|**IsSafe**|Attribut **xs:boolean** facultatif.<br /><br /> Spécifie si le contrôle ASPX ou le WebPart est sécurisé pour l'accès des utilisateurs non fiables.|  
|**IsSafeAgainstScript**|Attribut **xs:boolean** facultatif.<br /><br /> Spécifie si les utilisateurs non fiables peuvent afficher ou modifier les propriétés du contrôle ASPX ou du WebPart.|  
|**Name**|Attribut **xs:string** facultatif.<br /><br /> Nom de cette entrée de contrôle sécurisé dans la collection.|  
|**Namespace**|Attribut **xs:string** facultatif.<br /><br /> Espace de noms du contrôle ASPX ou du WebPart.|  
|**TypeName**|Attribut **xs:string** facultatif.<br /><br /> Nom de type du contrôle ASPX ou WebPart.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Représente une collection de contrôles ASPX et de composants WebPart désignés comme sécurisés pour tout utilisateur souhaitant y accéder sur n'importe quelle page ASPX du site SharePoint.|  
  
## Notes  
 Pour plus d'informations sur les contrôles sécurisés, consultez [Fourniture d'informations de création de packages et de déploiement dans des éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
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
  
  