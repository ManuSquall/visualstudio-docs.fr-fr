---
title: Élément ExtensionData | Microsoft Docs
description: Affichez les informations de référence sur l’élément ExtensionData, qui est un élément dans le schéma d’élément de projet SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionData element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3131aca3664e37198b0a32bdc0ade0499c12a1e6
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672533"
---
# <a name="extensiondata-element"></a>ExtensionData (élément)
  Représente une collection d’éléments de données personnalisés associés à l’élément de projet SharePoint.

## <a name="syntax"></a>Syntaxe

```xml
<ExtensionData>
  <ExtensionDataItem.../>
</ExtensionData>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs
 Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Élément facultatif.<br /><br /> Représente un élément de données personnalisé associé à l’élément de projet SharePoint, au format clé/valeur. La clé et la valeur doivent être des chaînes.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Représente un élément de projet SharePoint. Cet élément est l’élément racine requis du `.spdata` fichier.|

## <a name="remarks"></a>Remarques
 Lorsque vous associez des données personnalisées à un élément de projet SharePoint à l’aide <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> de la propriété d’un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objet, Visual Studio enregistre les données dans l’élément **ExtensionData** dans le `.spdata` fichier de l’élément de projet. Pour plus d’informations, consultez [enregistrer des données dans les extensions du système de projet SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="element-information"></a>Informations sur les éléments

|Propriété|Valeur|
|-|-|
|**Espace de noms**|http : \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nom du schéma**|Schéma d’élément de projet SharePoint|
|**Fichier de validation**|ProjectItemModelSchema. xsd|
|**Peut être vide**|Non|

## <a name="see-also"></a>Voir aussi
- [Référence du schéma d’élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
