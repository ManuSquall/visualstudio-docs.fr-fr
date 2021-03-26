---
title: Project, élément (modèles Visual Studio) | Microsoft Docs
description: En savoir plus sur l’élément de projet et sur la manière dont il spécifie les fichiers ou répertoires à ajouter au projet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 52bfb5f65aa9d42c46eece619a21152c51e8fa28
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068802"
---
# <a name="project-element-visual-studio-templates"></a>Élément Project (modèles Visual Studio)
Spécifie les fichiers ou répertoires à ajouter au projet.

 \<VSTemplate> \<TemplateContent>
 \<Project>

## <a name="syntax"></a>Syntaxe

```
<Project
    File="MyProject.proj"
    TargetFileName="MyTargetProject.proj"
    ReplaceParameters="true/false">
    IgnoreProjectParameter="$myCustomParameter$"
        ...
</Project>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`File`|Attribut requis.<br /><br /> Spécifie le nom du fichier projet dans le fichier *. zip* du modèle.|
|`ReplaceParameters`|Attribut facultatif.<br /><br /> Valeur booléenne qui spécifie si le fichier projet a des valeurs de paramètre qui doivent être remplacées lors de la création d’un projet à partir du modèle. La valeur par défaut est `false`.|
|`TargetFileName`|Attribut facultatif.<br /><br /> Spécifie le nom du fichier projet lorsqu’un projet est créé à partir du modèle.|
|`IgnoreProjectParameter`|Attribut facultatif.<br /><br /> Spécifie si le projet doit être ajouté à la solution actuelle. Si la valeur du paramètre personnalisé, « $*myCustomParameter*$ » existe dans le fichier de remplacement de paramètre, le projet est créé mais n’est pas ajouté dans le cadre de la solution actuellement ouverte.|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Folder](../extensibility/folder-element-visual-studio-project-templates.md)|Élément facultatif.<br /><br /> Spécifie un dossier à ajouter au projet.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|Élément facultatif.<br /><br /> Spécifie un fichier à ajouter à un projet.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Élément requis.|

## <a name="remarks"></a>Notes
 `Project` est un élément enfant facultatif de `TemplateContent`.

 L' `Project` élément est utilisé pour spécifier un projet et, par conséquent, est uniquement valide dans les modèles de projet.

 `Project` les éléments peuvent avoir des éléments enfants [Folder](../extensibility/folder-element-visual-studio-project-templates.md) ou [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) , mais pas un mélange des `Folder` `ProjectItem` éléments enfants et.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] renomme automatiquement le nom du fichier projet en fonction du nom entré par l’utilisateur dans la boîte de dialogue **nouveau projet** . Utilisez l' `TargetFileName` attribut si vous souhaitez fournir un autre nom de fichier pour les fichiers projet créés avec le modèle.

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
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
- [ProjectItem, élément (modèles de projet Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md)
- [Élément Folder (modèles de projet Visual Studio)](../extensibility/folder-element-visual-studio-project-templates.md)
