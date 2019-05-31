---
title: CreateNewFolder, élément (modèles Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CreateNewFolder
helpviewer_keywords:
- CreateNewFolder element [Visual Studio project templates]
ms.assetid: acef2016-4140-45d6-ace8-b8160eabd676
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51b7702f1b1e1c509f4f9d88d72f170d0ed765f2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341768"
---
# <a name="createnewfolder-element-visual-studio-templates"></a>CreateNewFolder, élément (modèles Visual Studio)
Détermine s'il convient de vérifier que le répertoire cible où le projet doit être créé n'existe pas. Si le répertoire existe, un nouveau répertoire peut être créé pour le projet. Ce paramètre est généralement remplacé par l'indicateur de registre `NewProjectRequiresNewFolder(VsTemplate)` (`HKEY_LOCAL_MACHINE/SOFTWARE(/Wow6432Node)/Microsoft/VisualStudio/<version number>/Projects/<project GUID>`) que tous les types de projets courants utilisent pour déterminer s'il convient de créer un nouveau projet dans un nouveau répertoire.

 \<VSTemplate> \<TemplateData> \<CreateNewFolder>

## <a name="syntax"></a>Syntaxe

```
<CreateNewFolder>
    true/false
</CreateNewFolder>
```

## <a name="type"></a>Type
 `Boolean`

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

 Le texte doit être `true` ou `false`, indiquant si un nouveau dossier conteneur doit être créé ou non quand un projet est créé à partir du modèle.

## <a name="remarks"></a>Notes
 `CreateNewFolder` est un élément facultatif. La valeur par défaut est `true`.

 La valeur spécifiée dans l'élément `CreateNewFolder` est honorée uniquement par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] si le système de projet sous-jacent la prend en charge.

## <a name="example"></a>Exemple
 L’exemple de code suivant spécifie de ne pas créer de nouveau dossier quand un projet est créé à partir du modèle.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <CreateNewFolder>false</CreateNewFolder>
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
- [Informations de référence sur les schémas de modèles Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projets et d’éléments](../ide/creating-project-and-item-templates.md)