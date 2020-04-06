---
title: TemplateContent Element (Visual Studio Templates) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent
helpviewer_keywords:
- TemplateContent element [Visual Studio project templates]
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 577ce71d3900947cde1de9a1e913124ab778a1ee
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699233"
---
# <a name="templatecontent-element-visual-studio-templates"></a>TemplateContent, élément (modèles Visual Studio)

Spécifie le contenu du modèle.

Hiérarchie des éléments :

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
|[BuildOnLoad](../extensibility/buildonload-visual-studio-templates.md)|Précise s’il faut construire la solution lorsqu’un projet est créé à partir du modèle.|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie l'organisation et le contenu de modèles à plusieurs projets.|
|[Projet](../extensibility/project-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie les fichiers ou les répertoires à ajouter au projet.|
|[Informations de référence](../extensibility/references-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie les références d’assemblage requises pour un modèle d’élément.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Élément facultatif.<br /><br /> Spécifie un fichier contenu dans le modèle.|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie tous les paramètres personnalisés qui doivent être utilisés lorsqu’un projet ou un élément est créé à partir du modèle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Élément requis.<br /><br /> Contient toutes les métadonnées pour le modèle de projet, le modèle d’élément ou le kit de démarrage.|

## <a name="remarks"></a>Notes
 `TemplateContent`est un élément nécessaire.

## <a name="example"></a>Exemple
 L’exemple suivant montre les métadonnées [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] d’un modèle de projet pour une application.

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
            <ProjectItem>Form1.cs</ProjectItem>
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
