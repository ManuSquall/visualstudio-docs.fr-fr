---
title: Élément d’assemblage (Visual Studio Template Wizard Extension) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio Template Wizard Extension]
- <Assembly> element [Visual Studio Template Wizard Extension]
ms.assetid: 0c3dc280-1753-4ea2-a13c-d31d13b935b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 43f5adb8abc17f0509fb58263f307e5051af85dc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740066"
---
# <a name="assembly-element-visual-studio-template-wizard-extension"></a>Élément d’assemblage (Extension de l’assistant de modèle visual studio)
Spécifie le nom ou le nom `IWizard` fort de l’assemblage qui implémente l’interface.

 \<VSTemplate> \<WizardExtension> \<Assemblée>

## <a name="syntax"></a>Syntaxe

```
<Assembly>AssemblyName</Assembly>
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
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Contient les éléments d’enregistrement pour personnaliser l’assistant modèle.|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Ce texte spécifie l’assemblage qui implémente l’interface. `IWizard` Ce nom d’assemblage doit être spécifié comme nom d’assemblée complète. Par exemple : `MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11dd0a3a, Custom = null`.

## <a name="remarks"></a>Notes
 `Assembly` est un élément enfant obligatoire de `WizardExtension`.

## <a name="example"></a>Exemple
 L’exemple suivant illustre les métadonnées du [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] modèle de projet standard pour une application Windows.

```xml
<VSTemplate Version="3.0.0" Type="Item"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyTemplate</Name>
        <Description>Template using IWizard extension</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
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
    <WizardExtension>
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11dd0a3a, Custom=null</Assembly>
        <FullClassName>MyWizard.CustomWizard</FullClassName>
    </WizardExtension>
</VSTemplate>
```

## <a name="see-also"></a>Voir aussi

- [Référence de schéma de modèle de studio visuel](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projets et d’objets](../ide/creating-project-and-item-templates.md)
- [Comment: Utiliser des assistants avec des modèles de projet](../extensibility/how-to-use-wizards-with-project-templates.md)
