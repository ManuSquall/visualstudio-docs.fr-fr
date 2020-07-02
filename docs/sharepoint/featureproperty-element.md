---
title: Élément FeatureProperty | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 61eeea33c6941624ed18a00db482590590a44a8f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546521"
---
# <a name="featureproperty-element"></a>FeatureProperty (élément)
  Représente une propriété personnalisée qui est incluse avec une fonctionnalité lorsqu’elle est déployée sur SharePoint. Une fois qu’une fonctionnalité a été déployée, vous pouvez accéder à la propriété dans votre code.

## <a name="syntax"></a>Syntaxe

```xml
<FeatureProperty Key = "Key of the property value"
    Value = "Property value" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|**Clé**|Attribut **XS : String** requis.<br /><br /> Clé utilisée pour stocker et récupérer la valeur de la propriété. Chaque propriété doit avoir une clé qui est unique dans la fonctionnalité.|
|**Valeur**|Attribut **XS : String** requis.<br /><br /> Valeur de propriété.|

### <a name="child-elements"></a>Éléments enfants
 Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Représente une collection de valeurs de propriétés qui sont incluses avec une fonctionnalité lorsqu’elle est déployée sur SharePoint.|

## <a name="remarks"></a>Remarques
 Pour plus d’informations sur les propriétés de fonctionnalité, consultez [fourniture d’informations de package et de déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

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
