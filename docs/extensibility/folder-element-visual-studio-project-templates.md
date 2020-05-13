---
title: Élément de dossier (Visual Studio Project Templates) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb256b8be0dd9ce68f193750bf3ff5a383d5f073
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711463"
---
# <a name="folder-element-visual-studio-project-templates"></a>Élément de dossier (modèles de projet Visual Studio)
Spécifie un dossier qui sera ajouté au projet.

 \<VSTemplate> \<TemplateContent> \<Project> \<Folder>

## <a name="syntax"></a>Syntaxe

```
<Folder Name="Project Folder">
    <Folder> ... </Folder>
    <ProjectItem> ... </ProjectItem>
</Folder>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`Name`|Attribut requis.<br /><br /> Le nom du dossier du projet.|
|`TargetFolderName`|Attribut facultatif.<br /><br /> Spécifie le nom pour donner le dossier quand un projet est créé à partir du modèle. Cet attribut est utile pour utiliser le remplacement des paramètres pour créer un nom de dossier ou nommer un dossier avec une chaîne internationale qui ne peut pas être utilisé directement dans le fichier *.zip.*|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|`Folder`|Spécifie un dossier à ajouter au projet. `Folder`les éléments `Folder` peuvent contenir des éléments pour enfants.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Spécifie un fichier à ajouter au projet.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Projet](../extensibility/project-element-visual-studio-templates.md)|Élément enfant facultatif de [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|

## <a name="remarks"></a>Notes
 `Folder`est un enfant `Project`optionnel de .

 Vous pouvez utiliser l’une des méthodes suivantes pour organiser les éléments du projet en dossiers dans un modèle :

- Inclure les dossiers dans le fichier *.zip* modèle, et les ajouter au projet dans le fichier `ProjectItem` *.vstemplate* en spécifiant le chemin vers le fichier dans les éléments, sans `Folder` éléments. Il s’agit de la méthode recommandée. Par exemple :

     `...`

     `<ProjectItem>\Folder\item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Inclure les dossiers dans le fichier *.zip* modèle, et les ajouter au `Folder` projet dans le fichier *.vstemplate* avec des éléments. Par exemple :

     `...`

     `<Folder name="Folder">`

     `<ProjectItem>item.cs</ProjectItem>`

     `</Folder>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- N’incluez pas les dossiers dans le fichier `TargetFileName` *.zip* du modèle, mais ajoutez des dossiers à l’aide de l’attribut de l’élément. `ProjectItem` Par exemple :

     `...`

     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

## <a name="example"></a>Exemple
 L’exemple suivant illustre les métadonnées [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] d’un modèle de projet pour une application Windows.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <Folder Name="Properties">
                <ProjectItem>AssemblyInfo.cs</ProjectItem>
                <ProjectItem>Resources.resx</ProjectItem>
                <ProjectItem>Resources.Designer.cs</ProjectItem>
                <ProjectItem>Settings.settings</ProjectItem>
                <ProjectItem>Settings.Designer.cs</ProjectItem>
            </Folder>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Voir aussi
- [Référence de schéma de modèle de studio visuel](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projets et d’objets](../ide/creating-project-and-item-templates.md)
- [Élément ProjectItem (modèles d’objets Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
