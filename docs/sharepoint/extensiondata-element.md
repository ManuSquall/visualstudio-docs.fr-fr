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
ms.openlocfilehash: 192b745580ab676dab476b4dcf31c15b9095be2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967342"
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
|**Espace de noms**|http:\/\/schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nom de schéma**|Schéma d’élément de projet SharePoint|
|**Fichier de validation**|ProjectItemModelSchema.xsd|
|**Peut être vide**|Non|

## <a name="see-also"></a>Voir aussi
- [Référence de schéma élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
