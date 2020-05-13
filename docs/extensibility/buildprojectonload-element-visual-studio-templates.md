---
title: BuildProjectOnload Element (Visual Studio Templates) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: b07d3074-0fc9-45e1-baf5-da6bd4f3f1c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 72d1981aab67762b3ee4aa8d62e0643f4c2a8963
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739947"
---
# <a name="buildprojectonload-element-visual-studio-templates"></a>Élément BuildProjectOnload (modèles Visual Studio)
Construit uniquement de nouveaux projets au fur et à mesure que vous les créez et les ajoutez à une solution. Toute la solution n’est pas construite.

Hiérarchie des éléments :

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
|`TemplateData`|Catégorise le modèle et définit comment il apparaît à la fois dans le **nouveau projet** et dans les boîtes de dialogue Add **New Item.**|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Le texte doit `true` `false` être soit ou pour indiquer s’il ne faut construire que le nouveau projet lorsqu’il est créé à partir du modèle.

## <a name="remarks"></a>Notes
 `BuildProjectOnLoad` est un élément facultatif. La valeur par défaut est `false`.

## <a name="example"></a>Exemple
 L’exemple suivant illustre les métadonnées d’un modèle Visual C.

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

- [Attribut et élément BuildOnLoad](buildonload-visual-studio-templates.md)
- [Création de modèles de projets et d’objets](../ide/creating-project-and-item-templates.md)
- [Référence de schéma de modèle de studio visuel](../extensibility/visual-studio-template-schema-reference.md)
