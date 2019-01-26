---
title: TemplateContent, élément (modèles Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent
helpviewer_keywords:
- TemplateContent element [Visual Studio project templates]
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c27f9ce239d5d82dc972186912266cea0d4f1ddf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070498"
---
# <a name="templatecontent-element-visual-studio-templates"></a>TemplateContent, élément (modèles Visual Studio)

Spécifie le contenu du modèle.

Hiérarchie de l’élément :

```xml
<VSTemplate>
  <TemplateContent>
```

## <a name="syntax"></a>Syntaxe

```xml
<TemplateContent>
    ...
</TemplateContent>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|[BuildOnLoad](../extensibility/buildonload-visual-studio-templates.md)|Spécifie s’il faut générer la solution lorsqu’un projet est créé à partir du modèle.|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie l'organisation et le contenu de modèles à plusieurs projets.|
|[Projet](../extensibility/project-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie les fichiers ou répertoires à ajouter au projet.|
|[Références](../extensibility/references-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie les références d’assembly requises pour un modèle d’élément.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Élément facultatif.<br /><br /> Spécifie un fichier contenu dans le modèle.|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie les paramètres personnalisés qui doivent être utilisées lorsqu’un projet ou un élément est créé à partir du modèle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Élément requis.<br /><br /> Contient toutes les métadonnées pour le modèle de projet, un modèle d’élément ou un starter kit.|

## <a name="remarks"></a>Notes
 `TemplateContent` un élément est requis.

## <a name="example"></a>Exemple
 L’exemple suivant montre les métadonnées d’un modèle de projet pour un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] application.

```xml
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

- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)