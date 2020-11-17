---
title: ProjectSubType, élément (modèles Visual Studio) | Microsoft Docs
description: En savoir plus sur l’élément ProjectSubType et la façon dont il classe le modèle dans une sous-catégorie de la valeur spécifiée dans l’élément ProjectType.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ceecbf1bfb750244a13c641906f7a8712d01d69
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672318"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>ProjectSubType, élément (modèles Visual Studio)
Classe le modèle dans une sous-catégorie de la valeur spécifiée dans l' `ProjectType` élément.

 \<VSTemplate> \<TemplateData>
 \<ProjectSubType>

## <a name="syntax"></a>Syntaxe

```xml
<ProjectSubType> SubType </ProjectSubType>
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
 Une valeur texte est requise.

 Cette valeur spécifie la sous-catégorie du modèle.

## <a name="remarks"></a>Remarques
 `ProjectSubType` est un élément enfant facultatif de `TemplateData`.

 L' `ProjectSubType` élément fournit une sous-catégorie à l’élément [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) . Cette valeur peut inclure :

- `SmartDevice-NETCFv1`: Spécifie que le modèle cible la [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] version 1,0.

- `SmartDevice-NETCFv2`: Spécifie que le modèle cible la [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] version 2,0.

  Si un modèle contient un `ProjectType` élément avec la valeur `Web` , l' `ProjectSubType` élément spécifie le langage de programmation du modèle. Cet élément peut avoir les valeurs suivantes :

- `CSharp`: Spécifie que le modèle crée un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projet Web ou un élément.

- `VisualBasic`: Spécifie que le modèle crée un [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projet Web ou un élément.

## <a name="example"></a>Exemple
 L’exemple suivant montre les métadonnées d’un modèle de projet pour une [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] application d’appareil ciblant la [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] version 2,0.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic device template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Voir aussi
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
- [ProjectType, élément (modèles Visual Studio)](../extensibility/projecttype-element-visual-studio-templates.md)
