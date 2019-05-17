---
title: 'Procédure : Sélectionner des fichiers dans une build | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, including files
- Include attribute [MSBuild]
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0968dd8914b99e8d47ef1364231059175aaf73fe
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437904"
---
# <a name="how-to-select-the-files-to-build"></a>Procédure : Sélectionner des fichiers dans une build
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quand vous générez un projet contenant plusieurs fichiers, vous pouvez lister chaque fichier un à un dans le fichier projet ou utiliser des caractères génériques pour inclure tous les fichiers d’un répertoire ou d’un ensemble imbriqué de répertoires.  
  
## <a name="specifying-inputs"></a>Spécification des entrées  
 Les éléments représentent les entrées d’une build. Pour plus d’informations sur les éléments, consultez [Éléments](../msbuild/msbuild-items.md).  
  
 Pour inclure des fichiers d’une build, vous devez les ajouter à une liste d’éléments dans le fichier projet [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Plusieurs fichiers peuvent être ajoutés aux listes d’éléments : soit un à un, soit à l’aide de caractères génériques.  
  
#### <a name="to-declare-items-individually"></a>Pour déclarer des éléments un à un  
  
- Utilisez les attributs `Include` de la façon suivante :  
  
     `<CSFile Include="form1.cs"/>`  
  
     – ou –  
  
     `<VBFile Include="form1.vb"/>`  
  
    > [!NOTE]
    > Si les éléments d’une collection d’éléments ne sont pas dans le même répertoire que le fichier projet, vous devez spécifier le chemin complet ou relatif de l’élément. Par exemple : `Include="..\..\form2.cs"`.  
  
#### <a name="to-declare-multiple-items"></a>Pour déclarer plusieurs éléments  
  
- Utilisez les attributs `Include` de la façon suivante :  
  
     `<CSFile Include="form1.cs;form2.cs"/>`  
  
     – ou –  
  
     `<VBFile Include="form1.vb;form2.vb"/>`  
  
## <a name="specifying-inputs-with-wildcards"></a>Spécification des entrées avec des caractères génériques  
 Vous pouvez aussi utiliser des caractères génériques pour inclure tous les fichiers de manière récursive ou n’inclure que certains fichiers des sous-répertoires comme entrées d’une build. Pour plus d’informations sur les caractères génériques, consultez [Éléments](../msbuild/msbuild-items.md).  
  
 Les exemples suivants s’appuient sur un projet qui contient des fichiers graphiques dans les répertoires et sous-répertoires suivants, avec le fichier projet situé dans le répertoire Project :  
  
 Project\Images\BestJpgs  
  
 Project\Images\ImgJpgs  
  
 Project\Images\ImgJpgs\Img1  
  
#### <a name="to-include-all-jpg-files-in-the-images-directory-and-subdirectories"></a>Pour inclure tous les fichiers .jpg du répertoire Images et de ses sous-répertoires  
  
- Utilisez l’attribut `Include` suivant :  
  
     `Include="Images\**\*.jpg"`  
  
#### <a name="to-include-all-jpg-files-starting-with-img"></a>Pour inclure tous les fichiers .jpg commençant par « img »  
  
- Utilisez l’attribut `Include` suivant :  
  
     `Include="Images\**\img*.jpg"`  
  
#### <a name="to-include-all-files-in-directories-with-names-ending-in-jpgs"></a>Pour inclure tous les fichiers figurant dans des répertoires dont les noms se terminent par « jpgs »  
  
- Utilisez l’un des attributs `Include` suivants :  
  
     `Include="Images\**\*jpgs\*.*"`  
  
     – ou –  
  
     `Include="Images\**\*jpgs\*"`  
  
## <a name="passing-items-to-a-task"></a>Passage d’éléments à une tâche  
 Dans un fichier projet, vous pouvez utiliser la notation @() dans les tâches pour spécifier une liste complète d’éléments comme entrée d’une build. Vous pouvez utiliser cette notation, que vous listiez tous les fichiers un à un ou que vous utilisiez des caractères génériques.  
  
#### <a name="to-use-all-visual-c-or-visual-basic-files-as-inputs"></a>Pour utiliser tous les fichiers Visual C# ou Visual Basic comme entrées  
  
- Utilisez les attributs `Include` de la façon suivante :  
  
     `<CSC Sources="@(CSFile)">...</CSC>`  
  
     – ou –  
  
     `<VBC Sources="@(VBFile)">...</VBC>`  
  
> [!NOTE]
> Vous devez utiliser des caractères génériques avec des éléments pour spécifier les entrées d’une build ; vous ne pouvez pas spécifier les entrées à l’aide de l’attribut `Sources` dans les tâches [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], telles que [Csc](../msbuild/csc-task.md) ou [Vbc](../msbuild/vbc-task.md). L’exemple suivant n’est pas valide dans un fichier projet :  
>   
> `<CSC Sources="*.cs">...</CSC>`  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant affiche un projet qui inclut séparément tous les fichiers d’entrée.  
  
```  
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
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant utilise un caractère générique pour inclure tous les fichiers .cs.  
  
```  
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
 [Guide pratique pour Exclure des fichiers de la Build](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Éléments](../msbuild/msbuild-items.md)
