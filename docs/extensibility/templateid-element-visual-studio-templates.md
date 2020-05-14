---
title: Élément TemplateID (Modèles de studio visuel) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8eb5abac9c837b3022354d6da743ac8f21d5e41d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699065"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID, élément (modèles Visual Studio)
Spécifie un identifiant pour un modèle d’élément qui est classé dans un groupe de modèles d’éléments par l’élément [TemplateGroupID.](../extensibility/templategroupid-element-visual-studio-templates.md)

 \<VSTemplate> \<TemplateData> \<TemplateID>

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
 Un `string` qui représente un identifiant pour un modèle d’élément qui `TemplateGroupID` est classé dans un groupe de modèles d’élément par l’élément.

## <a name="remarks"></a>Notes
 `TemplateID` est un élément facultatif.

 Si un fichier .vstemplate `TemplateID` omet l’élément, l’élément [Nom](../extensibility/name-element-visual-studio-templates.md) est utilisé comme identifiant pour le modèle.

 La valeur `TemplateID` de l’élément est utilisée avec l’enregistrement du système de projet (HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-11.0-Projets\\) pour filtrer les modèles qui apparaissent dans la boîte de dialogue Add New **Item.**

## <a name="see-also"></a>Voir aussi
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
