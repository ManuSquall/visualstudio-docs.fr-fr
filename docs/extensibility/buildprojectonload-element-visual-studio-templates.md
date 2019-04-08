---
title: Élément buildProjectOnload (modèles Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: b07d3074-0fc9-45e1-baf5-da6bd4f3f1c0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 41baf6b8405e45600050e508b7fd7523e19533ca
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55025720"
---
# <a name="buildprojectonload-element-visual-studio-templates"></a>Élément buildProjectOnload (modèles Visual Studio)
Génère les nouveaux projets uniquement quand vous créez et les ajoutez à une solution. L’ensemble de la solution n’est pas généré.

Hiérarchie de l’élément :

```xml
<VSTemplate>
  <TemplateData>
    <BuildProjectOnLoad>
```

## <a name="syntax"></a>Syntaxe

```vb
<BuildProjectOnLoad> true/false </BuildProjectOnLoad>
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
|`TemplateData`|Définit la catégorie du modèle et comment il apparaît dans les deux le **nouveau projet** et **ajouter un nouvel élément** boîtes de dialogue.|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Le texte doit être `true` ou `false` pour indiquer s’il faut générer uniquement le nouveau projet lorsqu’il est créé à partir du modèle.

## <a name="remarks"></a>Notes
 `BuildProjectOnLoad` est un élément facultatif. La valeur par défaut est `false`.

## <a name="example"></a>Exemple
 L’exemple suivant illustre les métadonnées d’un modèle Visual C#.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <BuildProjectOnload>true</BuildProjectOnLoad>
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

- [Élément et attribut de buildOnLoad](buildonload-visual-studio-templates.md)
- [Création de modèles de projets et d’éléments](../ide/creating-project-and-item-templates.md)
- [Informations de référence sur les schémas de modèles Visual Studio](../extensibility/visual-studio-template-schema-reference.md)