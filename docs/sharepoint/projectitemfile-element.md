---
title: Élément ProjectItemFile | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFile element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d1c9814498d74a5d1a6533576f1071b4bf7deb57
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539852"
---
# <a name="projectitemfile-element"></a>ProjectItemFile (élément)
  Représente un fichier SharePoint, tel qu’un fichier d’élément de fonctionnalité, à inclure avec l’élément de projet lorsqu’il est déployé sur SharePoint.

## <a name="syntax"></a>Syntaxe

```xml
<ProjectItemFile Source = "Name of the file"
    Target = "Deployment path of the file"
    Type = "Type of deployment for the file" />
```

## <a name="type"></a>Type
 **ProjectItemFileType**

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|**Source**|Attribut **XS : String** requis.<br /><br /> Nom du fichier à déployer avec l’élément de projet.|
|**Cible**|Attribut **XS : String** facultatif.<br /><br /> Chemin d’accès où le fichier sera déployé sur SharePoint, par rapport au dossier racine de déploiement. Le dossier racine de déploiement est déterminé par le type de déploiement spécifié par l’attribut **type** . Si l’attribut **cible** n’est pas spécifié, le fichier est déployé dans un dossier portant le nom spécifié dans l’attribut **source** .<br /><br /> Pour plus d’informations, consultez les descriptions des propriétés du **chemin de déploiement** et de la **racine de déploiement** des éléments de projet SharePoint dans [développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md).|
|**Type**|Attribut **XS : String** requis.<br /><br /> Type de déploiement du fichier. Pour plus d’informations sur les valeurs possibles, consultez la description de la propriété **type de déploiement** des éléments de projet SharePoint dans [développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Éléments enfants
 Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Fichiers](../sharepoint/files-element.md)|Spécifie les fichiers à inclure dans l’élément de projet SharePoint lorsqu’il est déployé sur SharePoint.|

## <a name="remarks"></a>Remarques
 Les fichiers SharePoint qui sont généralement référencés dans les éléments **ProjectItemFile** incluent des fichiers d’éléments de fonctionnalité (*Elements.xml*), des fichiers de schéma pour les définitions de listes (*Schema.xml*) et des fichiers de définition de composant WebPart pour composants WebPart (*. WebPart*).

## <a name="element-information"></a>Informations sur les éléments

|Propriété|Valeur|
|-|-|
|**Espace de noms**|http : \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nom du schéma**|Schéma d’élément de projet SharePoint|
|**Fichier de validation**|ProjectItemModelSchema. xsd|
|**Peut être vide**|Non|

## <a name="see-also"></a>Voir aussi
- [Référence du schéma d’élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
