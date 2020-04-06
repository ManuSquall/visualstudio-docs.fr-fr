---
title: ÉLÉMENT VSTemplate (Visual Studio Templates) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate
helpviewer_keywords:
- VSTemplate element [Visual Studio project templates]
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 651e8b6dbbe11c450b105f3185e7e987bb30da9b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697867"
---
# <a name="vstemplate-element-visual-studio-templates"></a>ÉLÉMENT VSTemplate (Visual Studio Templates)
Contient toutes les métadonnées sur le modèle de projet, le modèle d’élément ou le kit de démarrage.

## <a name="syntax"></a>Syntaxe

```csharp
<VSTemplate Type="TemplateType" Version="x.x.x">
    <TemplateData>    </TemplateData>
    <TemplateContent>    </TemplateContent>
    ...
</VSTemplate>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

| Attribut | Description |
|-----------| - |
| `Type` | Identifie le modèle comme un modèle de projet ou un modèle d’élément. Cet attribut peut avoir `Project` `Item`une valeur de ou . |
| `Version` | Spécifie un numéro de version pour le modèle. Modèles et [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] ont `Version` une valeur `3.0.0`d’attribut de . |

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Spécifie les données qui catégorisent le modèle et définissent comment il s’affiche dans la boîte de dialogue **Du nouveau projet** ou ajouter un nouvel **élément.**|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Élément requis.<br /><br /> Spécifie le contenu du modèle.|
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Élément facultatif.|
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|Élément facultatif.|

### <a name="parent-elements"></a>Éléments parents
 Aucun.

## <a name="remarks"></a>Notes
 L’élément `VSTemplate` est l’élément racine des fichiers *.vstemplate.*

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
- [Référence de schéma de modèle de studio visuel](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projets et d’objets](../ide/creating-project-and-item-templates.md)
