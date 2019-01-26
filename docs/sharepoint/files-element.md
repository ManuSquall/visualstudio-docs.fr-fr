---
title: Fichiers d’élément | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Files element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b25bb220d3c22af280a486de115193af38c85dbe
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864525"
---
# <a name="files-element"></a>Files (élément)
  Spécifie les fichiers à déployer avec l’élément de projet SharePoint, tels que les fichiers d’élément de fonctionnalité et la sortie des projets non-SharePoint dépendants.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Files>  
  <ProjectItemFile.../>  
  <ProjectOutputFile.../>  
</Files>  
```  
  
## <a name="type"></a>Type  
 **FileCollectionType**  
  
## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants
  
|Élément|Description|  
|-------------|-----------------|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Facultatif **ProjectItemFileType** élément.<br /><br /> Représente un fichier SharePoint, par exemple de fichier d’élément de fonctionnalité, à inclure avec l’élément de projet lorsqu’elle est déployée vers SharePoint.|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Facultatif **ProjectOutputFileType** élément.<br /><br /> Représente la sortie d’un projet à inclure avec l’élément de projet lorsqu’elle est déployée vers SharePoint.|  
  
### <a name="parent-elements"></a>Éléments parents
  
|Élément|Description|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Représente un élément de projet SharePoint. Cet élément de l’élément racine requis de le `.spdata` fichier.|  
  
## <a name="element-information"></a>Informations sur les éléments
  
|||  
|-|-|  
|**Espace de noms**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**Nom de schéma**|Schéma d’élément de projet SharePoint|  
|**Fichier de validation**|ProjectItemModelSchema.xsd|  
|**Peut être vide**|Aucune|  
  
## <a name="see-also"></a>Voir aussi
 [Référence de schéma élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
