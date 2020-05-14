---
title: Guide pratique pour sélectionner des fichiers dans une build | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, including files
- Include attribute [MSBuild]
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0566078c7f90faf204c35024e2c308b5ef881c01
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633809"
---
# <a name="how-to-select-the-files-to-build"></a>Guide pratique pour sélectionner des fichiers dans une build

Quand vous générez un projet contenant plusieurs fichiers, vous pouvez lister chaque fichier un à un dans le fichier projet ou utiliser des caractères génériques pour inclure tous les fichiers d’un répertoire ou d’un ensemble imbriqué de répertoires.

## <a name="specify-inputs"></a>Spécifier les entrées

Les éléments représentent les entrées d’une build. Pour plus d’informations sur les éléments, consultez [Éléments](../msbuild/msbuild-items.md).

Pour inclure les fichiers pour une build, ils doivent être inclus dans une liste d’éléments dans le fichier du projet MSBuild. Plusieurs fichiers peuvent être ajoutés aux listes d’éléments : soit un à un, soit à l’aide de caractères génériques.

#### <a name="to-declare-items-individually"></a>Pour déclarer des éléments un à un

- Utilisez les attributs `Include` de la façon suivante :

    `<CSFile Include="form1.cs"/>`

    or

    `<VBFile Include="form1.vb"/>`

    > [!NOTE]
    > Si les éléments d’une collection d’éléments ne sont pas dans le même répertoire que le fichier projet, vous devez spécifier le chemin complet ou relatif de l’élément. Par exemple : `Include="..\..\form2.cs"`.

#### <a name="to-declare-multiple-items"></a>Pour déclarer plusieurs éléments

- Utilisez les attributs `Include` de la façon suivante :

    `<CSFile Include="form1.cs;form2.cs"/>`

    or

    `<VBFile Include="form1.vb;form2.vb"/>`

## <a name="specify-inputs-with-wildcards"></a>Spécifier les entrées avec des caractères génériques

Vous pouvez aussi utiliser des caractères génériques pour inclure tous les fichiers de manière récursive ou n’inclure que certains fichiers des sous-répertoires comme entrées d’une build. Pour plus d’informations sur les caractères génériques, consultez [Éléments](../msbuild/msbuild-items.md).

Les exemples suivants s’appuient sur un projet qui contient des fichiers graphiques dans les répertoires et sous-répertoires suivants, avec le fichier projet situé dans le répertoire *Project* :

*Project\Images\BestJpgs*

*Project\Images\ImgJpgs*

*Project\Images\ImgJpgs\Img1*

#### <a name="to-include-all-jpg-files-in-the-images-directory-and-subdirectories"></a>Pour inclure tous les fichiers *.jpg* dans le répertoire *Images* et ses sous-répertoires

- Utilisez l’attribut `Include` suivant :

    `Include="Images\**\*.jpg"`

#### <a name="to-include-all-jpg-files-starting-with-img"></a>Pour inclure tous les fichiers *.jpg* commençant par *img*

- Utilisez l’attribut `Include` suivant :

    `Include="Images\**\img*.jpg"`

#### <a name="to-include-all-files-in-directories-with-names-ending-in-jpgs"></a>Pour inclure tous les fichiers figurant dans des répertoires dont les noms se terminent par *jpgs*

- Utilisez l’un des attributs `Include` suivants :

    `Include="Images\**\*jpgs\*.*"`

    or

    `Include="Images\**\*jpgs\*"`

## <a name="pass-items-to-a-task"></a>Passer des éléments à une tâche

Dans un fichier projet, vous pouvez utiliser la notation @() dans les tâches pour spécifier une liste complète d’éléments comme entrée d’une build. Vous pouvez utiliser cette notation, que vous listiez tous les fichiers un à un ou que vous utilisiez des caractères génériques.

#### <a name="to-use-all-visual-c-or-visual-basic-files-as-inputs"></a>Pour utiliser tous les fichiers Visual C# ou Visual Basic comme entrées

- Utilisez les attributs `Include` de la façon suivante :

    `<CSC Sources="@(CSFile)">...</CSC>`

    or

    `<VBC Sources="@(VBFile)">...</VBC>`

> [!NOTE]
> Vous devez utiliser des wildcards avec des éléments pour spécifier les entrées pour une construction; vous ne pouvez pas `Sources` spécifier les entrées en utilisant l’attribut dans les tâches MSBuild telles que [Csc](../msbuild/csc-task.md) ou [Vbc](../msbuild/vbc-task.md). L’exemple suivant n’est pas valide dans un fichier projet :
>
> `<CSC Sources="*.cs">...</CSC>`

## <a name="example"></a> Exemple

L’exemple de code suivant affiche un projet qui inclut séparément tous les fichiers d’entrée.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Builtdir>built</Builtdir>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="Form1.cs"/>
        <CSFile Include="AssemblyInfo.cs"/>

        <Reference Include="System.dll"/>
        <Reference Include="System.Data.dll"/>
        <Reference Include="System.Drawing.dll"/>
        <Reference Include="System.Windows.Forms.dll"/>
        <Reference Include="System.XML.dll"/>
    </ItemGroup>

    <Target Name="PreBuild">
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>
    </Target>

    <Target Name="Compile" DependsOnTargets="PreBuild">
        <Csc Sources="@(CSFile)"
            References="@(Reference)"
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"
            TargetType="exe" />
    </Target>
</Project>
```

## <a name="example"></a> Exemple

L’exemple de code suivant utilise un caractère générique pour inclure tous les fichiers *.cs*.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <PropertyGroup>
        <builtdir>built</builtdir>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="*.cs"/>

        <Reference Include="System.dll"/>
        <Reference Include="System.Data.dll"/>
        <Reference Include="System.Drawing.dll"/>
        <Reference Include="System.Windows.Forms.dll"/>
        <Reference Include="System.XML.dll"/>
    </ItemGroup>

    <Target Name="PreBuild">
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>
    </Target>

    <Target Name="Compile" DependsOnTargets="PreBuild">
        <Csc Sources="@(CSFile)"
            References="@(Reference)"
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"
            TargetType="exe" />
    </Target>
</Project>
```

## <a name="see-also"></a>Voir aussi

- [Comment : Exclure les fichiers de la construction](../msbuild/how-to-exclude-files-from-the-build.md)
- [Éléments](../msbuild/msbuild-items.md)
