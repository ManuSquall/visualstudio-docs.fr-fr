---
title: Folder, élément (modèles de projet Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c066bfacea4996ab8d212ac607a3dfa3f3fad36
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342613"
---
# <a name="folder-element-visual-studio-project-templates"></a>Folder, élément (modèles de projet Visual Studio)
Spécifie un dossier qui sera ajouté au projet.

 \<VSTemplate > \<TemplateContent > \<projet > \<dossier >

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
|`TargetFolderName`|Attribut facultatif.<br /><br /> Spécifie le nom à attribuer au dossier lorsqu’un projet est créé à partir du modèle. Cet attribut est utile pour l’utilisation de remplacement de paramètres pour créer un nom de dossier ou d’affectation de noms un dossier avec une chaîne internationale qui ne peut pas être utilisée directement dans le *.zip* fichier.|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|`Folder`|Spécifie un dossier à ajouter au projet. `Folder` les éléments peuvent contenir des enfants `Folder` éléments.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Spécifie un fichier à ajouter au projet.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Projet](../extensibility/project-element-visual-studio-templates.md)|Élément enfant facultatif de [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|

## <a name="remarks"></a>Notes
 `Folder` est un enfant facultatif de `Project`.

 Vous pouvez utiliser une des méthodes suivantes pour organiser les éléments de projet dans des dossiers dans un modèle :

- Inclure les dossiers dans le modèle *.zip* de fichiers et les ajouter au projet dans le *.vstemplate* fichier en spécifiant le chemin d’accès au fichier dans le `ProjectItem` éléments, sans aucune `Folder` éléments. Il s’agit de la méthode recommandée. Exemple :

     `...`

     `<ProjectItem>\Folder\item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Inclure les dossiers dans le modèle *.zip* de fichiers et les ajouter au projet dans le *.vstemplate* de fichiers avec `Folder` éléments. Exemple :

     `...`

     `<Folder name="Folder">`

     `<ProjectItem>item.cs</ProjectItem>`

     `</Folder>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- N’incluez pas de dossiers dans le modèle *.zip* de fichier, mais ajouter des dossiers à l’aide de la `TargetFileName` attribut de la `ProjectItem` élément. Exemple :

     `...`

     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

## <a name="example"></a>Exemple
 L’exemple suivant illustre les métadonnées d’un modèle de projet pour un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] application de Windows.

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
- [Informations de référence sur les schémas de modèles Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projets et d’éléments](../ide/creating-project-and-item-templates.md)
- [ProjectItem, élément (modèles d’élément Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)