---
title: PromptForSaveOnCreation, élément (modèles Visual Studio)
titleSuffix: ''
description: En savoir plus sur l’élément PromptForSaveOnCreation et sur la façon dont il spécifie si l’utilisateur est invité à entrer un emplacement d’enregistrement de projet via la boîte de dialogue Nouveau projet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#PromptForSaveOnCreation
helpviewer_keywords:
- PromptForSaveOnCreation element [Visual Studio project templates]
ms.assetid: 75174674-0c3c-4b57-b2fd-6ea8e817b67d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 5bc3c28bcfa35dac23c96d9a566b9767f8db9c1c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068641"
---
# <a name="promptforsaveoncreation-element-visual-studio-templates"></a>Élément PromptForSaveOnCreation (modèles Visual Studio)

Spécifie si l’utilisateur est invité à entrer un emplacement d’enregistrement de projet à l’aide de la boîte **de dialogue Nouveau projet** lors de la création d’un projet. Si cet élément a la valeur `true` , l’utilisateur est invité à entrer un emplacement d’enregistrement. Si `false` la condition est, les messages ne sont pas demandés (autrement dit, un projet temporaire est créé).

```xml
\<VSTemplate>
\<TemplateData>
\<PromptForSaveOnCreation>
```

## <a name="syntax"></a>Syntaxe

```xml
<PromptForSaveOnCreation> true/false </PromptForSaveOnCreation>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Définit la catégorie du modèle et comment il s’affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément** .|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Le texte doit être `true` ou `false` , `true` indiquant que l’utilisateur sera invité à entrer un emplacement d’enregistrement lors de la création d’un nouveau projet.

## <a name="remarks"></a>Notes
 `PromptForSaveOnCreation` est un élément facultatif. La valeur par défaut est `false`.

 Les projets temporaires sont des projets que vous pouvez créer et modifier sans enregistrer le contenu de ce projet sur le disque.

## <a name="example"></a>Exemple
 L’exemple suivant définit la valeur de `PromptForSaveOnCreation` égale à `false` , qui spécifie que le projet doit être créé en tant que projet temporaire.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <PromptForSaveOnCreation>false</PromptForSaveOnCreation>
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

- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
