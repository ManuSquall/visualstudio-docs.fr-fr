---
title: Élément ProjectOutputFile | Microsoft Docs
description: Obtenir des informations de référence sur l’élément ProjectOutputFile, qui représente la sortie d’un projet distinct dans la référence de schéma XML d’élément de projet SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectOutputFile element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ffe6f95bdfd7795c837aaaa25ec7ef2a35a7ae76
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442026"
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile (élément)
  Représente la sortie d’un projet distinct à inclure avec l’élément de projet lorsqu’il est déployé sur SharePoint.

## <a name="syntax"></a>Syntaxe

```xml
<ProjectOutputFile ProjectId = "GUID of the project"
    ProjectPath = "Relative path of the project"
    Target = "Deployment path of the project output"
    Type = "Type of deployment for the project output" />
```

## <a name="type"></a>Type
 **ProjectOutputFileType**

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|**ProjectId**|Attribut **XS : String** requis.<br /><br /> GUID du projet dépendant qui a la sortie que vous souhaitez inclure. Cela correspond à l’élément **ProjectGuid** dans le fichier projet dépendant.|
|**ProjectPath**|Attribut **XS : String** requis.<br /><br /> Chemin d’accès relatif, y compris le nom du fichier projet, du projet dépendant qui a la sortie que vous souhaitez inclure. Ce chemin d’accès est relatif au dossier racine du projet SharePoint qui contient l’élément de projet SharePoint.|
|**Cible**|Attribut **XS : String** facultatif.<br /><br /> Chemin d’accès où la sortie de projet dépendante doit être déployée sur le serveur SharePoint, par rapport au dossier racine de déploiement. Le dossier racine de déploiement est déterminé par le type de déploiement spécifié par l’attribut **type** .<br /><br /> Pour plus d’informations, consultez les descriptions des propriétés du **chemin de déploiement** et de la **racine de déploiement** des éléments de projet SharePoint dans [développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md).|
|**Type**|Attribut **XS : String** requis.<br /><br /> Type de déploiement à utiliser pour la sortie du projet dépendant. Pour plus d’informations sur les valeurs possibles, consultez la description de la propriété **type de déploiement** des éléments de projet SharePoint dans [développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Éléments enfants
 Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Fichiers](../sharepoint/files-element.md)|Spécifie les fichiers à inclure dans l’élément de projet SharePoint lorsqu’il est déployé sur SharePoint.|

## <a name="remarks"></a>Notes
 Utilisez l’élément **ProjectOutputFile** pour inclure la sortie d’un projet dans le déploiement de l’élément de projet SharePoint. Vous pouvez spécifier un projet différent ou le même projet qui contient l’élément de projet. Pour plus d’informations, consultez [fournir des informations sur l’empaquetage et le déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Informations sur les éléments

|Propriété|Valeur|
|-|-|
|**Espace de noms**|http : \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nom du schéma**|Schéma d’élément de projet SharePoint|
|**Fichier de validation**|ProjectItemModelSchema. xsd|
|**Peut être vide**|Non|

## <a name="see-also"></a>Voir aussi
- [Référence du schéma d’élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Fournir des informations d’empaquetage et de déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
