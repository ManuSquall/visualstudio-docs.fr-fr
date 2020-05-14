---
title: PreviewImage Element (Visual Studio Templates) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <PreviewImage> Element (Visual Studio Templates)
- PreviewImage Element (Visual Studio Templates)
ms.assetid: d1796f20-523b-4e0d-8ac3-ca87f3b5a9b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f20cfe5f3ef35b23a52972ef1e3b7d9d4adc5a39
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702019"
---
# <a name="previewimage-element-visual-studio-templates"></a>AperçuImage élément (modèles Visual Studio)
Spécifie l’image de prévisualisation, comme nom de fichier, pour l’image de prévisualisation qui apparaîtra dans la boîte de dialogue **New Project** ou Ajouter un **nouvel élément.**

 \<VSTemplate> \<TemplateData> \<PreviewImage>

## <a name="syntax"></a>Syntaxe

```
<PreviewImage>"filename"</PreviewImage>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs
 Aucun.

### <a name="child-elements"></a>Éléments enfants
 Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Catégorise le modèle et définit comment il est affiché dans le **nouveau projet** ou la boîte de dialogue Add **New Item.**|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Le texte doit être une chaîne qui représente un nom de fichier.

## <a name="remarks"></a>Notes
 `PreviewImage` est un élément facultatif.

## <a name="see-also"></a>Voir aussi
- [Référence de schéma de modèle de studio visuel](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projets et d’objets](../ide/creating-project-and-item-templates.md)
