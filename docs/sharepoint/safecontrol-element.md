---
title: SafeControl (élément) | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControl element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5e507d83a1f1f75e346ccbab1858d797dc7b7518
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34691841"
---
# <a name="safecontrol-element"></a>SafeControl, élément
  Représente un contrôle ASPX ou un WebPart désigné comme sécurisé pour tout utilisateur d’accéder sur n’importe quelle page ASPX sur le site SharePoint.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
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
|**Name**|Facultatif **xs : String** attribut.<br /><br /> Le nom de cette entrée de contrôle sécurisé dans la collection.|  
|**Espace de noms**|Facultatif **xs : String** attribut.<br /><br /> L’espace de noms de contrôle ASPX ou du WebPart.|  
|**Nom de type**|Facultatif **xs : String** attribut.<br /><br /> Le nom de type de contrôle ASPX ou du WebPart.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Représente une collection de contrôles ASPX et les composants WebPart qui sont désignés comme sécurisés pour tout utilisateur d’accéder sur n’importe quelle page ASPX sur le site SharePoint.|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur les contrôles sécurisés, consultez [fournissant l’empaquetage et du déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Informations sur les éléments  
  
|||  
|-|-|  
|**Espace de noms**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**Nom du schéma**|Schéma d’élément de projet SharePoint|  
|**Fichier de validation**|ProjectItemModelSchema.xsd|  
|**Peut être vide.**|Non|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du schéma élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Fourniture d’informations de création de packages et de déploiement dans des éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  