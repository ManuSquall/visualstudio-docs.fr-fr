---
title: Élément PreviewImage (modèles Visual Studio) | Microsoft Docs
description: Découvrez l’élément PreviewImage et comment il spécifie le nom de fichier de l’image d’aperçu qui s’affichera dans la boîte de dialogue Nouveau projet ou ajouter un nouvel élément.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 326588259203224d3f70b505af8437af22930faa
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672344"
---
# <a name="previewimage-element-visual-studio-templates"></a>Élément PreviewImage (modèles Visual Studio)
Spécifie l’image d’aperçu, sous la forme d’un nom de fichier, pour l’image d’aperçu qui s’affichera dans la boîte de dialogue **nouveau projet** ou **Ajouter un nouvel élément** .

 \<VSTemplate> \<TemplateData>
 \<PreviewImage>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Classe le modèle et définit son mode d’affichage dans la boîte de dialogue **nouveau projet** ou **Ajouter un nouvel élément** .|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Le texte doit être une chaîne qui représente un nom de fichier.

## <a name="remarks"></a>Remarques
 `PreviewImage` est un élément facultatif.

## <a name="see-also"></a>Voir aussi
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
