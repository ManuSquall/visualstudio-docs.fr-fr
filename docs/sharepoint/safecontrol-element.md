---
title: "SafeControl (élément) | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: SafeControl element
ms.assetid: e7c61749-fc73-412c-be30-4af5ff2a9fd2
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8d9651c320e574c8db9fcafcb6e98f13e45eac1d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="safecontrol-element"></a>SafeControl, élément
  Représente un contrôle ASPX ou un WebPart désigné comme sécurisé pour tout utilisateur d’accéder sur n’importe quelle page ASPX sur le site SharePoint.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<SafeControl Assembly = "Name of assembly that contains the safe control"  
    IsSafe = "true/false"  
    IsSafeAgainstScript = "true/false"  
    Name = "Name of this safe control entry"  
    Namespace = "Namespace of the safe control"  
    TypeName = "Type of the safe control" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|**Assembly**|Facultatif **xs : String** attribut.<br /><br /> Le nom de l’assembly dans lequel le contrôle ASPX ou un composant WebPart est défini. Par défaut, cet attribut utilise le **$SharePoint.Project.AssemblyFullName$** paramètre remplaçable pour le nom de l’assembly. Pour plus d’informations, consultez [paramètres remplaçables](../sharepoint/replaceable-parameters.md).|  
|**IsSafe**|Facultatif **xs : Boolean** attribut.<br /><br /> Spécifie si le contrôle ASPX ou un composant WebPart est sécurisé pour les utilisateurs non autorisés à accéder.|  
|**IsSafeAgainstScript**|Facultatif **xs : Boolean** attribut.<br /><br /> Spécifie si les utilisateurs non fiables peuvent afficher ou modifier les propriétés de contrôle ASPX ou du WebPart.|  
|**Nom**|Facultatif **xs : String** attribut.<br /><br /> Le nom de cette entrée de contrôle sécurisé dans la collection.|  
|**Namespace**|Facultatif **xs : String** attribut.<br /><br /> L’espace de noms de contrôle ASPX ou du WebPart.|  
|**Nom de type**|Facultatif **xs : String** attribut.<br /><br /> Le nom de type de contrôle ASPX ou du WebPart.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Représente une collection de contrôles ASPX et les composants WebPart qui sont désignés comme sécurisés pour tout utilisateur d’accéder sur n’importe quelle page ASPX sur le site SharePoint.|  
  
## <a name="remarks"></a>Remarques  
 Pour plus d’informations sur les contrôles sécurisés, consultez [fournissant l’empaquetage et du déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Informations sur les éléments  
  
|||  
|-|-|  
|**Namespace**|http://schemas.Microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nom du schéma**|Schéma d’élément de projet SharePoint|  
|**Fichier de validation**|ProjectItemModelSchema.xsd|  
|**Peut être vide.**|Non|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du schéma élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Fourniture d’informations de création de packages et de déploiement dans des éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  