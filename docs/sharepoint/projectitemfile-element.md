---
title: ProjectItemFile, élément | Microsoft Docs
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
ms.openlocfilehash: 57c491c79030eea1a01024235c01aec425d5994c
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2019
ms.locfileid: "58322910"
---
# <a name="projectitemfile-element"></a>ProjectItemFile (élément)
  Représente un fichier SharePoint, par exemple de fichier d’élément de fonctionnalité, à inclure avec l’élément de projet lorsqu’elle est déployée vers SharePoint.

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
|**Source**|Requis **xs : String** attribut.<br /><br /> Le nom du fichier à déployer avec l’élément de projet.|
|**Target**|Facultatif **xs : String** attribut.<br /><br /> Le chemin d’accès où le fichier sera déployé sur SharePoint, relatif au dossier racine de déploiement. Le dossier racine de déploiement est déterminé par le type de déploiement spécifié par le **Type** attribut. Si le **cible** attribut n’est pas spécifié, le fichier sera déployé dans un dossier portant le nom spécifié dans le **Source** attribut.<br /><br /> Pour plus d’informations, consultez les descriptions pour le **Deployment Path** et **Deployment Root** propriétés de SharePoint éléments de projet des [SharePoint de développer des solutions](../sharepoint/developing-sharepoint-solutions.md).|
|**Type**|Requis **xs : String** attribut.<br /><br /> Le type de déploiement pour le fichier. Pour plus d’informations sur les valeurs possibles, consultez la description de la **Type de déploiement** propriété des éléments de projet SharePoint dans [SharePoint de développer des solutions](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Éléments enfants
 Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Fichiers](../sharepoint/files-element.md)|Spécifie les fichiers à inclure avec l’élément de projet SharePoint lorsqu’elle est déployée vers SharePoint.|

## <a name="remarks"></a>Notes
 Les fichiers SharePoint qui sont en général référencés dans **ProjectItemFile** éléments incluent des fichiers d’éléments de fonctionnalité (*Elements.xml*), les fichiers de schéma pour les définitions de liste (*Schema.xml*) et les fichiers de définition de composant WebPart de composants WebPart (*.webpart*).

## <a name="element-information"></a>Informations sur les éléments

|||
|-|-|
|**Espace de noms**|http:\/\/schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nom de schéma**|Schéma d’élément de projet SharePoint|
|**Fichier de validation**|ProjectItemModelSchema.xsd|
|**Peut être vide**|Non|

## <a name="see-also"></a>Voir aussi
- [Référence de schéma élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
