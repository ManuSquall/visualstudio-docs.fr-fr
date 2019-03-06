---
title: ExtensionData, élément | Microsoft Docs
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
ms.openlocfilehash: dbbd291888c9df1875afed64de034ab070ce8ef6
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608316"
---
# <a name="extensiondata-element"></a>ExtensionData (élément)
  Représente une collection d’éléments de données personnalisés qui sont associés à l’élément de projet SharePoint.

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
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Élément facultatif.<br /><br /> Représente un élément de données personnalisé qui est associé à l’élément de projet SharePoint, au format clé/valeur. La clé et la valeur doivent être des chaînes.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Représente un élément de projet SharePoint. Cet élément de l’élément racine requis de le `.spdata` fichier.|

## <a name="remarks"></a>Notes
 Lorsque vous associez des données personnalisées à un élément de projet SharePoint à l’aide de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriété d’un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> de l’objet, Visual Studio enregistre les données à la **ExtensionData** élément dans le `.spdata` fichier pour le projet élément. Pour plus d’informations, consultez [enregistrer les données dans les extensions du système de projet SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="element-information"></a>Informations sur les éléments

|||
|-|-|
|**Espace de noms**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nom de schéma**|Schéma d’élément de projet SharePoint|
|**Fichier de validation**|ProjectItemModelSchema.xsd|
|**Peut être vide**|Aucune|

## <a name="see-also"></a>Voir aussi
- [Référence de schéma élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
