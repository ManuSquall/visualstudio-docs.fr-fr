---
title: WizardExtension Element (Visual Studio Templates) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardExtension
helpviewer_keywords:
- WizardExtension element [Visual Studio Templates]
- <WizardExtension> element [Visual Studio Templates]
ms.assetid: d54b01c1-50f5-4b65-828c-686e2321cc8c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd81b32861114d654aa794b992826589406b1df9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740374"
---
# <a name="wizardextension-element-visual-studio-templates"></a>WizardExtension, élément (modèles Visual Studio)
Contient les éléments d’enregistrement pour personnaliser l’assistant modèle.

 \<VSTemplate> ... \<> d’extension de WizardExtension

## <a name="syntax"></a>Syntaxe

```
<WizardExtension>
    <Assembly>... </Assembly>
    <FullClassName>... </FullClassName>
</WizardExtension>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs
 Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Assemblée](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)|Élément requis.<br /><br /> Spécifie le nom ou le nom fort d’une assemblée qui apparaît dans le cache d’assemblage global. Il doit y `Assembly` avoir au `WizardExtension` moins un élément dans un élément.|
|[FullClassName](../extensibility/fullclassname-element-visual-studio-template-wizard-extension.md)|Élément requis.<br /><br /> Le nom entièrement qualifié de la `IWizard` classe qui implémente l’interface. Il doit y `FullClassName` avoir au `WizardExtension` moins un élément dans un élément.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Contient toutes les métadonnées pour le modèle de projet, le modèle d’élément ou le kit de démarrage.|

## <a name="remarks"></a>Notes
 `WizardExtension` est un élément enfant facultatif de `VSTemplate`.

## <a name="example"></a>Exemple
 L’exemple suivant illustre les métadonnées du [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] modèle de projet standard pour une application Windows.

```
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
    <WizardExtension>
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>
        <FullClassName>MyWizard.CustomWizard</FullClassName>
    </WizardExtension>
</VSTemplate>
```

## <a name="see-also"></a>Voir aussi
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
- [Comment : utiliser des Assistants avec des modèles de projet](../extensibility/how-to-use-wizards-with-project-templates.md)
