---
title: SafeControls, élément | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControls element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fe8b3c026b7386d89ef04d0a966eccad425f1629
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119219"
---
# <a name="safecontrols-element"></a>SafeControls (élément)
  Une collection de contrôles ASPX et les composants WebPart qui sont désignés comme sécurisé pour un utilisateur d’accéder sur n’importe quelle page ASPX du site SharePoint.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<SafeControls>  
  <SafeControl.../>  
</SafeControls>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants
  
|Élément|Description|  
|-------------|-----------------|  
|[SafeControl](../sharepoint/safecontrol-element.md)|Élément facultatif.<br /><br /> Représente un contrôle ASPX ou un composant WebPart qui est désigné comme sécurisé pour un utilisateur d’accéder sur n’importe quelle page ASPX du site SharePoint.|  
  
### <a name="parent-elements"></a>Éléments parents
  
|Élément|Description|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Représente un élément de projet SharePoint. Cet élément de l’élément racine requis de la *.spdata* fichier.|  
  
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
  
