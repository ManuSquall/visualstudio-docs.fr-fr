---
title: ProjectType, élément (modèles Visual Studio) | Microsoft Docs
description: Découvrez l’élément ProjectType et comment il classe le modèle de projet afin qu’il apparaisse dans la boîte de dialogue Nouveau projet ou ajouter un nouvel élément.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a90c8de2fca62ef303ce8055993d8e2f6d230493
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910894"
---
# <a name="projecttype-element-visual-studio-templates"></a>ProjectType, élément (modèles Visual Studio)
Classe le modèle de projet de manière à ce qu’il apparaisse sous le groupe spécifié dans la boîte de dialogue **nouveau projet** ou **Ajouter un nouvel élément** .

> [!WARNING]
> Les modèles de projet sont pris en charge pour C++ à partir de Visual Studio 2012. Ils ne sont pas pris en charge pour C++ dans Visual Studio 2010 et versions antérieures.

 \<VSTemplate> \<TemplateData>
 \<ProjectType>

## <a name="syntax"></a>Syntaxe

```xml
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>
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

 Cette valeur spécifie le type de projet que le modèle créera et doit contenir l’une des valeurs suivantes :

- `CSharp`: Spécifie que le modèle crée un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projet ou un élément.

- `VisualBasic`: Spécifie que le modèle crée un [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projet ou un élément.

- `Web`: Spécifie que le modèle crée un projet Web ou un élément. Si l' `ProjectType` élément contient cette valeur, le langage du projet ou de l’élément est défini dans l' [élément ProjectSubType (modèles Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md).

## <a name="remarks"></a>Notes
 `ProjectType` est un élément enfant obligatoire de `TemplateData`.

 La valeur de l' `ProjectType` élément spécifie l’emplacement du modèle dans la boîte de dialogue **nouveau projet** ou **Ajouter un nouvel élément** . Par exemple, un modèle avec `ProjectType` `CSharp` la valeur apparaît sous le nœud **Visual C#** dans la boîte de dialogue **nouveau projet** .

 Un sous-type de modèle peut être spécifié à l’aide de l’élément [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) .

## <a name="example"></a>Exemple
 L’exemple suivant montre les métadonnées d’un modèle de projet pour une [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] application.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
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
- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
- [ProjectSubType, élément (modèles Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md)
