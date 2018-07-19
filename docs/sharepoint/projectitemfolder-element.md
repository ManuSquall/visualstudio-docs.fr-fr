---
title: ProjectItemFolder, élément | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 54d47165117b88041346e9b666db8db17a20ddb9
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119230"
---
# <a name="projectitemfolder-element"></a>ProjectItemFolder (élément)
  Représente un dossier mappé.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"  
    Type = "Type of deployment for the mapped folder" />  
```  
  
## <a name="type"></a>Type  
 **ProjectItemFolderType**  
  
## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|**Target**|Requis **xs : string** attribut.<br /><br /> Le chemin d’accès du dossier dans l’installation de SharePoint que le dossier mappé correspond, relatif au dossier racine de déploiement. Le dossier racine de déploiement est déterminé par le type de déploiement spécifié par le **Type** attribut.<br /><br /> Pour plus d’informations, consultez les descriptions pour le **Deployment Path** et **Deployment Root** propriétés de SharePoint éléments de projet des [SharePoint de développer des solutions](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Requis **xs : String** attribut.<br /><br /> Le type de déploiement pour le dossier mappé. Pour plus d’informations sur les valeurs possibles, consultez la description de la **Type de déploiement** propriété des éléments de projet SharePoint dans [SharePoint de développer des solutions](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Éléments enfants
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents
  
|Élément|Description|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Représente un élément de projet SharePoint. Cet élément est l’élément racine requis de la *.spdata* fichier.|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur les dossiers mappés, consultez [Comment : ajouter et supprimer des dossiers mappés](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
## <a name="element-information"></a>Informations sur les éléments
  
|||  
|-|-|  
|**Espace de noms**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/2010/<br>SharePointTools/SharePointProjectItemModel|  
|**Nom de schéma**|Schéma d’élément de projet SharePoint|  
|**Fichier de validation**|ProjectItemModelSchema.xsd|  
|**Peut être vide**|Non|  
  
## <a name="see-also"></a>Voir aussi
 [Référence de schéma élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Comment : ajouter et supprimer des dossiers mappés](../sharepoint/how-to-add-and-remove-mapped-folders.md)  
  
