---
title: Élément CustomDataSignature (modèles Visual Studio) | Microsoft Docs
description: En savoir plus sur l’élément CustomDataSignature et sur la façon dont il spécifie la signature de texte pour localiser les données personnalisées.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <CustomDataSignature> Element (Visual Studio Templates)
- CustomDataSignature Element (Visual Studio Templates)
ms.assetid: 8c3db51d-7014-4484-802a-15aa1353dbdb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e5f42b3c5fe1dc5b9ab9697275876509eb0f8509
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946057"
---
# <a name="customdatasignature-element-visual-studio-templates"></a>Élément CustomDataSignature (modèles Visual Studio)
Spécifie la signature du texte pour localiser les données personnalisées.

 \<VSTemplate> \<TemplateData>
 \<CustomDataSignature>

## <a name="syntax"></a>Syntaxe

```
<CustomDataSignature>"string"</CustomDataSignature>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Classe le modèle et définit son mode d’affichage dans la boîte de dialogue **nouveau projet** ou **Ajouter un nouvel élément** .|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Le texte est une chaîne qui possède la signature de texte requise pour localiser les données personnalisées.

## <a name="remarks"></a>Notes
 `CustomDataSignature` est un élément facultatif.

## <a name="see-also"></a>Voir aussi
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
