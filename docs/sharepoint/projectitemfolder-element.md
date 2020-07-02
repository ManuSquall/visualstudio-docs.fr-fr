---
title: Élément ProjectItemFolder, | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 38f8f70cc6480554441809e33c4083735600fbbb
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539813"
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
|**Cible**|Attribut **XS : String** requis.<br /><br /> Chemin d’accès du dossier de l’installation SharePoint auquel correspond le dossier mappé, relatif au dossier racine de déploiement. Le dossier racine de déploiement est déterminé par le type de déploiement spécifié par l’attribut **type** .<br /><br /> Pour plus d’informations, consultez les descriptions des propriétés du **chemin de déploiement** et de la **racine de déploiement** des éléments de projet SharePoint dans [développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md).|
|**Type**|Attribut **XS : String** requis.<br /><br /> Type de déploiement du dossier mappé. Pour plus d’informations sur les valeurs possibles, consultez la description de la propriété **type de déploiement** des éléments de projet SharePoint dans [développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Éléments enfants
 Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Représente un élément de projet SharePoint. Cet élément est l’élément racine requis du fichier *. les données* .|

## <a name="remarks"></a>Remarques
 Pour plus d’informations sur les dossiers mappés, consultez [procédure : ajouter et supprimer des dossiers mappés](../sharepoint/how-to-add-and-remove-mapped-folders.md).

## <a name="element-information"></a>Informations sur les éléments

|Propriété|Valeur|
|-|-|
|**Espace de noms**|http : \/ \/ schemas.Microsoft.com/VisualStudio/2010/<br>SharePointTools/SharePointProjectItemModel|
|**Nom du schéma**|Schéma d’élément de projet SharePoint|
|**Fichier de validation**|ProjectItemModelSchema. xsd|
|**Peut être vide**|Non|

## <a name="see-also"></a>Voir aussi
- [Référence du schéma d’élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Procédure : ajouter et supprimer des dossiers mappés](../sharepoint/how-to-add-and-remove-mapped-folders.md)
