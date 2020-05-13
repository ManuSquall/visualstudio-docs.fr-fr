---
title: ProjectSubType Element (Visual Studio Templates) Microsoft Docs
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
ms.openlocfilehash: 27396ad1bcc4e181b2b8cecd6ca863db2412630d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701830"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>Élément ProjectSubType (modèles Visual Studio)
Classifie le modèle en une sous-catégorie de `ProjectType` la valeur spécifiée dans l’élément.

 \<VSTemplate> \<TemplateData> \<ProjectSubType>

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

## <a name="remarks"></a>Notes
 `ProjectSubType` est un élément enfant facultatif de `TemplateData`.

 L’élément `ProjectSubType` fournit une sous-catégorie à l’élément [ProjectType.](../extensibility/projecttype-element-visual-studio-templates.md) Cette valeur peut inclure :

- `SmartDevice-NETCFv1`: Spécifie que [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] le modèle cible la version 1.0.

- `SmartDevice-NETCFv2`: Spécifie que [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] le modèle cible la version 2.0.

  Si un modèle `ProjectType` contient un `Web`élément `ProjectSubType` avec une valeur de , l’élément spécifie le langage de programmation du modèle. Cet élément peut avoir les valeurs suivantes :

- `CSharp`: Spécifie que [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] le modèle crée un projet Web ou un élément.

- `VisualBasic`: Spécifie que [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] le modèle crée un projet Web ou un élément.

## <a name="example"></a>Exemple
 L’exemple suivant montre les métadonnées [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] d’un [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] modèle de projet pour une application d’appareil ciblant la version 2.0.

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
- [Référence de schéma de modèle de studio visuel](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projets et d’objets](../ide/creating-project-and-item-templates.md)
- [Élément ProjectType (modèles Visual Studio)](../extensibility/projecttype-element-visual-studio-templates.md)
