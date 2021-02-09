---
title: Attribut et élément BuildOnLoad (modèles Visual Studio)
titleSuffix: ''
description: En savoir plus sur l’attribut et l’élément BuildOnLoad et sur la façon dont il spécifie s’il faut générer le projet immédiatement après sa création.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#BuildOnLoad
helpviewer_keywords:
- BuildOnLoad attribute [Visual Studio Templates]
- BuildOnLoad element [Visual Studio Templates]
ms.assetid: 950f5fc1-d041-4090-9a5c-60844768a4cc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5fe0fa745ef611395abe6244c0e207271b182cb4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927325"
---
# <a name="buildonload-attribute-and-element"></a>Élément et attribut BuildOnLoad

Spécifie s’il faut générer le projet immédiatement après sa création. **BuildOnLoad** est à la fois un attribut et un élément.

Hiérarchie d’éléments :

```xml
<VSTemplate>
  <TemplateData>
    <BuildOnLoad>
```

## <a name="element-syntax"></a>Syntaxe des éléments

```xml
<BuildOnLoad> true/false </BuildOnLoad>
```

## <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Définit la catégorie du modèle et comment il s’affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément** .|

## <a name="text-value"></a>Valeur texte

Une valeur de texte est requise pour l’élément **BuildOnLoad** . Le texte doit être `true` ou `false` , indiquant s’il faut générer le projet immédiatement après sa création.

## <a name="remarks"></a>Notes

**BuildOnLoad** est un attribut facultatif. La valeur par défaut est `false`.

## <a name="example"></a>Exemple

L’exemple suivant illustre les métadonnées d’un modèle C# quand **BuildOnLoad** est utilisé en tant qu’élément :

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <BuildOnLoad>true</BuildOnLoad>
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

- [Élément BuildProjectOnload](buildprojectonload-element-visual-studio-templates.md)
- [Élément TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
