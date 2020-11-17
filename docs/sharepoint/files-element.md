---
title: Élément Files | Microsoft Docs
description: Affichez les informations de référence sur l’élément Files, qui est un élément du schéma d’élément de projet SharePoint.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 03473f40bb78c866f3d93dea11a20b8747afad7b
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672806"
---
# <a name="files-element"></a>Files (élément)
  Spécifie les fichiers à déployer avec l’élément de projet SharePoint, tels que les fichiers d’élément de fonctionnalité et la sortie des projets non SharePoint dépendants.

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
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Élément **ProjectItemFileType** facultatif.<br /><br /> Représente un fichier SharePoint, tel qu’un fichier d’élément de fonctionnalité, à inclure avec l’élément de projet lorsqu’il est déployé sur SharePoint.|
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Élément **ProjectOutputFileType** facultatif.<br /><br /> Représente la sortie d’un projet à inclure avec l’élément de projet lorsqu’il est déployé sur SharePoint.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Représente un élément de projet SharePoint. Cet élément est l’élément racine requis du `.spdata` fichier.|

## <a name="element-information"></a>Informations sur les éléments

|Propriété|Valeur|
|-|-|
|**Espace de noms**|http : \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nom du schéma**|Schéma d’élément de projet SharePoint|
|**Fichier de validation**|ProjectItemModelSchema. xsd|
|**Peut être vide**|Non|

## <a name="see-also"></a>Voir aussi
- [Référence du schéma d’élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
