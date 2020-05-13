---
title: Élément SDKReference (Visual Studio Templates) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 72c8b352-0b7a-42b3-ba5d-2a2d1e90c34b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f43c813e688c1e175f1d36e6f06125f92404c48
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700161"
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
