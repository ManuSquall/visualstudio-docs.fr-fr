---
title: Élément WizardData (modèles Visual Studio) | Microsoft Docs
description: En savoir plus sur l’élément WizardData et sur la façon dont il spécifie un XML personnalisé.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardData
helpviewer_keywords:
- WizardData element [Visual Studio Templates]
- <WizardData> element [Visual Studio Templates]
ms.assetid: d0403a16-5d07-4fe5-b474-19ae3d9fd3ab
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6839a4ac8e53ec70fc88d23525985e8d1b7cccd7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904520"
---
# <a name="wizarddata-element-visual-studio-templates"></a>WizardData, élément (modèles Visual Studio)

Spécifie le code XML personnalisé

```xml
\<VSTemplate>
\<WizardData>
```

## <a name="syntax"></a>Syntaxe

```xml
<WizardData>
    <!-- XML to pass to the custom wizard extension -->
    ...
</WizardData>
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
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Élément requis.<br /><br /> Contient toutes les métadonnées pour le modèle de projet, le modèle d’élément ou le starter kit.|

## <a name="text-value"></a>Valeur texte

Une valeur texte est facultative.

Ce texte spécifie le code XML personnalisé à transmettre à l’extension d’Assistant personnalisée spécifiée dans l’élément [WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md) .

## <a name="remarks"></a>Notes

Tout code XML peut être spécifié dans cet élément. Le XML est passé en tant que paramètre à l’extension d’Assistant personnalisée, ce qui permet à l’extension d’utiliser le contenu de cet élément. Aucune validation n’est effectuée sur ces données.

Le contenu de l’élément **WizardData** est passé, inchangé, en tant que paramètre dans le dictionnaire de chaînes de paramètres dans la `IWizard.RunStarted` méthode. La clé du dictionnaire est nommée `$wizarddata$` .

## <a name="example"></a>Exemple

L’exemple suivant illustre les métadonnées pour le modèle de projet standard pour une application Windows C#.

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
    <WizardData>
        <!-- XML to pass to the custom wizard extension -->
    </WizardData>
</VSTemplate>
```

## <a name="see-also"></a>Voir aussi

- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
- [Élément WizardExtension (modèles Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Comment : utiliser des Assistants avec des modèles de projet](../extensibility/how-to-use-wizards-with-project-templates.md)
