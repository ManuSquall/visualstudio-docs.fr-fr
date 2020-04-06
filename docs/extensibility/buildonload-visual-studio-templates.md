---
title: Attribut et élément BuildOnLoad (Visual Studio Templates)
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3be4016822ccaaae2f1352f91ecc10f09273a889
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739953"
---
# <a name="buildonload-attribute-and-element"></a>Attribut et élément BuildOnLoad

Précise s’il faut construire le projet immédiatement après sa création. **BuildOnLoad** est à la fois un attribut et un élément.

Hiérarchie des éléments :

```xml
<VSTemplate>
  <TemplateData>
    <BuildOnLoad>
```

## <a name="element-syntax"></a>Syntaxe d’élément

```xml
<BuildOnLoad> true/false </BuildOnLoad>
```

## <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Définit la catégorie du modèle et comment il s’affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément** .|

## <a name="text-value"></a>Valeur texte

Une valeur de texte est requise pour l’élément **BuildOnLoad.** Le texte doit `true` `false`être soit ou , indiquant s’il faut construire le projet immédiatement après sa création.

## <a name="remarks"></a>Notes

**BuildOnLoad** est un attribut optionnel. La valeur par défaut est `false`.

## <a name="example"></a>Exemple

L’exemple suivant illustre les métadonnées d’un modèle Cmd lorsque **BuildOnLoad** est utilisé comme élément :

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
- [Création de modèles de projets et d’objets](../ide/creating-project-and-item-templates.md)
- [Référence de schéma de modèle de studio visuel](../extensibility/visual-studio-template-schema-reference.md)
