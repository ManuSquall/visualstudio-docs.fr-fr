---
title: SafeControl, élément | Microsoft Docs
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
ms.openlocfilehash: aded7f246d961bd3f956611ff092dfdcf8b68564
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118894"
---
# <a name="safecontrol-element"></a>SafeControl (élément)
  Représente un contrôle ASPX ou un composant WebPart qui est désigné comme sécurisé pour un utilisateur d’accéder sur n’importe quelle page ASPX du site SharePoint.  
  
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
|**Assembly**|Facultatif **xs : String** attribut.<br /><br /> Le nom de l’assembly dans lequel le contrôle ASPX ou le composant WebPart est défini. Par défaut, cet attribut utilise la **$SharePoint.Project.AssemblyFullName$** paramètre remplaçable pour le nom de l’assembly. Pour plus d’informations, consultez [paramètres remplaçables](../sharepoint/replaceable-parameters.md).|  
|**IsSafe**|Facultatif **xs : Boolean** attribut.<br /><br /> Spécifie si le contrôle ASPX ou le composant WebPart est sécurisé pour les utilisateurs non approuvés à accéder.|  
|**IsSafeAgainstScript**|Facultatif **xs : Boolean** attribut.<br /><br /> Spécifie si les utilisateurs non fiables peuvent afficher ou modifier les propriétés de contrôle ASPX ou du composant WebPart.|  
|**Name**|Facultatif **xs : String** attribut.<br /><br /> Le nom de cette entrée de contrôle sécurisé dans la collection.|  
|**Espace de noms**|Facultatif **xs : String** attribut.<br /><br /> L’espace de noms de contrôle ASPX ou du composant WebPart.|  
|**TypeName**|Facultatif **xs : String** attribut.<br /><br /> Le nom de type de contrôle ASPX ou du composant WebPart.|  
  
### <a name="child-elements"></a>Éléments enfants
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents
  
|Élément|Description|  
|-------------|-----------------|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Représente une collection de contrôles ASPX et les composants WebPart qui sont désignés comme sécurisés pour tous les utilisateurs à accéder sur n’importe quelle page ASPX du site SharePoint.|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur les contrôles sécurisés, consultez [fournissent des informations d’empaquetage et de déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Informations sur les éléments
  
|||  
|-|-|  
|**Espace de noms**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**Nom de schéma**|Schéma d’élément de projet SharePoint|  
|**Fichier de validation**|ProjectItemModelSchema.xsd|  
|**Peut être vide**|Non|  
  
## <a name="see-also"></a>Voir aussi
 [Référence de schéma élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Fournir des informations d’empaquetage et de déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
