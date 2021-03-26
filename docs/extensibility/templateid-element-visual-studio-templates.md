---
title: TemplateID, élément (modèles Visual Studio) | Microsoft Docs
description: En savoir plus sur l’élément TemplateID et la façon dont il spécifie un identificateur pour un modèle d’élément qui est catégorisé en un groupe de modèles d’élément par l’élément TemplateGroupID.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e33f2d5c424e5d48cff212dc736bbc13e58801d5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056010"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID, élément (modèles Visual Studio)
Spécifie un identificateur pour un modèle d’élément qui est catégorisé en un groupe de modèles d’élément par l’élément [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) .

 \<VSTemplate> \<TemplateData>
 \<TemplateID>

## <a name="syntax"></a>Syntaxe

```
<TemplateID> ... </TemplateID>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Définit la catégorie du modèle et comment il s’affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément** .|

## <a name="text-value"></a>Valeur texte
 `string`Qui représente un identificateur pour un modèle d’élément qui est catégorisé en un groupe de modèles d’élément par l' `TemplateGroupID` élément.

## <a name="remarks"></a>Notes
 `TemplateID` est un élément facultatif.

 Si un fichier. vstemplate omet l' `TemplateID` élément, l’élément [Name](../extensibility/name-element-visual-studio-templates.md) est utilisé comme identificateur pour le modèle.

 La valeur de l' `TemplateID` élément est utilisée avec l’inscription du système de projet (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects\\ ) pour filtrer les modèles qui s’affichent dans la boîte de dialogue **Ajouter un nouvel élément** .

## <a name="see-also"></a>Voir aussi
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
