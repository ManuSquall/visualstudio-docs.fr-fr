---
title: FeatureProperties, élément | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperties element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f9b893ce699dd86f309a05fad83560cc42439551
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619366"
---
# <a name="featureproperties-element"></a>FeatureProperties (élément)
  Collection de valeurs de propriété qui sont incluses avec une fonctionnalité lorsqu’elle est déployée vers SharePoint. Après le déployée d’une fonctionnalité, vous pouvez accéder les valeurs de propriété dans votre code.

## <a name="syntax"></a>Syntaxe

```xml
<FeatureProperties>
  <FeatureProperty.../>
</FeatureProperties>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs
 Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Élément facultatif.<br /><br /> Représente une propriété personnalisée, au format clé/valeur.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Représente un élément de projet SharePoint. Cet élément de l’élément racine requis de le `.spdata` fichier.|

## <a name="remarks"></a>Notes
 Pour plus d’informations sur les propriétés de fonctionnalité, consultez [fournissent des informations d’empaquetage et de déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Informations sur les éléments

|Élément|Description|
|-------------|-----------------|
|**Espace de noms**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nom de schéma**|Schéma d’élément de projet SharePoint|
|**Fichier de validation**|ProjectItemModelSchema.xsd|
|**Peut être vide**|Aucune|

## <a name="see-also"></a>Voir aussi
- [Référence de schéma élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Fournir des informations d’empaquetage et de déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
