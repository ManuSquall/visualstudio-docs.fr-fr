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
ms.openlocfilehash: 3c669b7cc314bc2d7a999e77d5cfb95251789dd8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967368"
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
|**Espace de noms**|http:\/\/schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nom de schéma**|Schéma d’élément de projet SharePoint|
|**Fichier de validation**|ProjectItemModelSchema.xsd|
|**Peut être vide**|Non|

## <a name="see-also"></a>Voir aussi
- [Référence de schéma élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
