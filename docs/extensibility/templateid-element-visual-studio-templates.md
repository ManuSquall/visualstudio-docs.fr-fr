---
title: TemplateID, élément (modèles Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c0e404921d1ed74db2a1f23117242f49a07206c2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718736"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID, élément (modèles Visual Studio)
Spécifie un identificateur pour un modèle d’élément qui est catégorisé en un groupe de modèles d’élément par l’élément [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) .

 \<VSTemplate > \<TemplateData > \<TemplateID >

## <a name="syntax"></a>Syntaxe

```
<TemplateID> ... </TemplateID>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs
 Aucun(e).

### <a name="child-elements"></a>Éléments enfants
 Aucun(e).

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Définit la catégorie du modèle et comment il s’affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément** .|

## <a name="text-value"></a>Valeur texte
 @No__t_0 qui représente un identificateur pour un modèle d’élément classé dans un groupe de modèles d’élément par l’élément `TemplateGroupID`.

## <a name="remarks"></a>Notes
 `TemplateID` est un élément facultatif.

 Si un fichier. vstemplate omet l’élément `TemplateID`, l’élément [Name](../extensibility/name-element-visual-studio-templates.md) est utilisé comme identificateur pour le modèle.

 La valeur de l’élément `TemplateID` est utilisée avec l’inscription du système de projet (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects \\) pour filtrer les modèles qui s’affichent dans la boîte de dialogue **Ajouter un nouvel élément** .

## <a name="see-also"></a>Voir aussi
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)