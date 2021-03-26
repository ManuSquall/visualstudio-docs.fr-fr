---
title: Élément SDKReference (modèles Visual Studio) | Microsoft Docs
description: En savoir plus sur l’élément SDKReference et sur la façon dont il spécifie que le modèle d’élément utilise une référence SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 72c8b352-0b7a-42b3-ba5d-2a2d1e90c34b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5ea070cf466782a1da09e1ba48d08a6965fd041a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063706"
---
# <a name="sdkreference-element-visual-studio-templates"></a>Élément SDKReference (modèles Visual Studio)
Spécifie que le modèle d’élément utilise une référence SDK.

## <a name="syntax"></a>Syntaxe

```xml
<VSTemplate>
    <TemplateContent>
        <References>
            <Reference>
                <SDKReference>SDKname</SDKReference>
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
|[Référence](../extensibility/reference-element-visual-studio-templates.md)|Spécifie la référence d’assembly à ajouter quand l’élément est ajouté à un projet.|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

## <a name="remarks"></a>Notes
 Ce texte spécifie la référence SDK à ajouter à un projet quand le modèle d’élément est instancié.

```xml
<VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
    <TemplateData> . . . </TemplateData>
    <TemplateContent>
        <References>
            <Reference>
                <SDKReference>Microsoft Visual C++ Runtime Package, Version=11.0.0.0</SDKReference>
...
```

## <a name="see-also"></a>Voir aussi
- [Élément References (modèles Visual Studio)](../extensibility/references-element-visual-studio-templates.md)
- [Élément Reference (modèles Visual Studio)](../extensibility/reference-element-visual-studio-templates.md)
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
