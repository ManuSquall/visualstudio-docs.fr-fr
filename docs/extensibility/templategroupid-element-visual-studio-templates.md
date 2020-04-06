---
title: Élément TemplateGroupID (Modèles de studio visuel) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: affc324418e3745f85fb0b91a0ef7abda0ab28b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699076"
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID, élément (modèles Visual Studio)
Spécifie le genre de projet dans lequel les modèles d'élément doivent s'afficher. Cet élément est significatif lorsque [ShowByDefault (Visual Studio Templates)](../extensibility/showbydefault-visual-studio-templates.md) est configuré à `false`. Lorsque [ShowByDefault (Visual Studio Templates)](../extensibility/showbydefault-visual-studio-templates.md) est configuré, `true`un modèle d’article est disponible dans tous les types de projets.

 \<VSTemplate> \<TemplateData> \<TemplateGroupID>

## <a name="syntax"></a>Syntaxe

```
<TemplateGroupID> ... </TemplateGroupID>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Définit la catégorie du modèle et comment il s’affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément** .|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Le texte spécifie un identificateur pour une catégorie de modèles d'élément.

## <a name="remarks"></a>Notes
 `TemplateGroupID` est un élément.

 La valeur `TemplateGroupID` de l’élément est utilisée avec l’enregistrement du système de\\projet*\<(numéro *de version\\HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio>'Projets ' pour filtrer les modèles qui apparaissent dans la boîte de dialogue **Add New Item.**

|Valeur Visual C++|Signification|
|------------------------|-------------|
|VC-Native|Utilisé pour les projets natifs. Correspond également à la valeur par défaut, s'il est impossible de déterminer un type de projet.|
|VC-Managed|Utilisé pour les projets managés (/clr)|
|VC-Windows|Utilisé pour tous les projets qui ciblent la plateforme Windows (natifs/managés/Store)|
|WinRT-Native-UAP|Utilisé pour les projets de Store Windows 10|
|CodeSharing-Native|Utilisé pour les projets d'éléments partagés|
|WinRT-Native-6.3|Utilisé pour les projets de Store Windows 8.1|
|WinRT-Native-Phone-6.3|Utilisé pour les projets Windows Phone 8.1|
|WinRT-Native|Utilisé pour les projets de Store Windows 8.0|
|VC-Android|Utilisé pour les projets Android|

## <a name="see-also"></a>Voir aussi
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
