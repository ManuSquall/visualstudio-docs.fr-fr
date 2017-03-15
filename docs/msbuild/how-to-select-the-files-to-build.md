---
title: "How to: Select the Files to Build | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, wildcards"
  - "MSBuild, including files"
  - "Include attribute [MSBuild]"
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# How to: Select the Files to Build
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsque vous générez un projet contenant plusieurs fichiers, vous pouvez répertorier séparément chaque fichier dans le fichier projet, ou vous pouvez utiliser des caractères génériques pour inclure tous les fichiers d'un répertoire ou un ensemble imbriqué de répertoires.  
  
## Spécification des entrées  
 Les éléments représentent les entrées d'une génération.  Pour plus d'informations sur les éléments, consultez [Items](../msbuild/msbuild-items.md).  
  
 Les fichiers d'une génération doivent être inclus dans une liste d'éléments du fichier projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  Plusieurs fichiers peuvent être ajoutés aux listes d'éléments soit séparément soit à l'aide de caractères génériques.  
  
#### Pour déclarer les éléments séparément  
  
-   Utilisez les attributs `Include` de la façon suivante :  
  
     `<CSFile Include="form1.cs"/>`  
  
     \- ou \-  
  
     `<VBFile Include="form1.vb"/>`  
  
    > [!NOTE]
    >  Si les éléments d'une collection d'éléments ne sont pas dans le même répertoire que le fichier projet, vous devez spécifier le chemin d'accès complet ou relatif de l'élément.  Par exemple : `Include="..\..\form2.cs"`.  
  
#### Pour déclarer plusieurs éléments  
  
-   Utilisez les attributs `Include` de la façon suivante :  
  
     `<CSFile Include="form1.cs;form2.cs"/>`  
  
     \- ou \-  
  
     `<VBFile Include="form1.vb;form2.vb"/>`  
  
## Spécification des entrées avec les caractères génériques  
 Vous pouvez aussi utiliser les caractères génériques pour inclure tous les fichiers de manière récursive ou n'inclure que certains fichiers des sous\-répertoires comme entrées de la génération.  Pour plus d'informations sur les caractères génériques, consultez [Items](../msbuild/msbuild-items.md).  
  
 Les exemples suivants s'appuient sur un projet qui contient des fichiers graphiques dans les répertoires et sous\-répertoires suivants, avec le fichier projet situé dans le répertoire Project :  
  
 Project\\Images\\BestJpgs  
  
 Project\\Images\\ImgJpgs  
  
 Project\\Images\\ImgJpgs\\Img1  
  
#### Pour inclure tous les fichiers .jpg du répertoire Images et de ses sous\-répertoires  
  
-   Utilisez l'attribut `Include` suivant :  
  
     `Include="Images\**\*.jpg"`  
  
#### Pour inclure tous les fichiers .jpg qui commencent par « img »  
  
-   Utilisez l'attribut `Include` suivant :  
  
     `Include="Images\**\img*.jpg"`  
  
#### Pour inclure tous les fichiers des répertoires dont les noms se terminent par « jpgs »  
  
-   Utilisez l'un des attributs `Include` suivants :  
  
     `Include="Images\**\*jpgs\*.*"`  
  
     \- ou \-  
  
     `Include="Images\**\*jpgs\*"`  
  
## Passage d'éléments à une tâche  
 Dans un fichier projet, vous pouvez utiliser la notation @\(\) dans les tâches afin de spécifier une liste complète d'éléments comme entrée d'une génération.  Vous pouvez utiliser cette notation que vous répertoriez tous les fichiers séparément ou que vous utilisiez des caractères génériques.  
  
#### Pour utiliser tous les fichiers Visual C\# ou Visual Basic comme entrées  
  
-   Utilisez les attributs `Include` de la façon suivante :  
  
     `<CSC Sources="@(CSFile)">...</CSC>`  
  
     \- ou \-  
  
     `<VBC Sources="@(VBFile)">...</VBC>`  
  
> [!NOTE]
>  Vous devez utiliser les caractères génériques avec des éléments pour spécifier les entrées d'une génération ; vous ne pouvez pas spécifier les entrées à l'aide de l'attribut `Sources` dans les tâches [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], telles que [Csc](../msbuild/csc-task.md) ou [Vbc](../msbuild/vbc-task.md).  L'exemple suivant n'est pas valide dans un fichier projet :  
>   
>  `<CSC Sources="*.cs">...</CSC>`  
  
## Exemple  
 L'exemple de code suivant affiche un projet qui inclut séparément tous les fichiers d'entrée.  
  
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
  
## Exemple  
 L'exemple de code suivant utilise un caractère générique pour inclure tous les fichiers .cs.  
  
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
  
## Voir aussi  
 [How to: Exclude Files from the Build](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Items](../msbuild/msbuild-items.md)