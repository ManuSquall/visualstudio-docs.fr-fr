---
title: 'Comment : référencer le nom ou l’emplacement du fichier projet | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dceca1e518783f405490d3f2527156bd20bf81aa
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911523"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Guide pratique pour référencer le nom ou l’emplacement du fichier projet
Vous pouvez utiliser le nom ou l’emplacement du projet dans le fichier projet sans avoir à créer votre propre propriété. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fournit des propriétés réservées qui référencent le nom du fichier projet et d’autres propriétés associées au projet. Pour plus d’informations sur les propriétés réservées, consultez [MSBuild, propriétés réservées et connues](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="use-the-project-properties"></a>Utiliser les propriétés du projet
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fournit quelques propriétés réservées que vous pouvez utiliser dans vos fichiers projet sans les définir à chaque fois. Par exemple, la propriété réservée `MSBuildProjectName` fournit une référence au nom du fichier projet. La propriété réservée `MSBuildProjectDirectory` fournit une référence à l’emplacement du fichier projet.
  
#### <a name="to-use-the-project-properties"></a>Pour utiliser les propriétés du projet
  
- Référencez la propriété dans le fichier projet avec la notation $(), comme vous le feriez avec n’importe quelle propriété. Exemple :  
  
  ```xml  
  <CSC Sources = "@(CSFile)"   
      OutputAssembly = "$(MSBuildProjectName).exe"/>  
  </CSC>  
  ```          
  
  L’un des avantages liés à l’utilisation d’une propriété réservée est que les modifications apportées au nom du fichier projet sont incorporées automatiquement. À la prochaine génération du projet, le fichier de sortie dispose du nouveau nom sans aucune intervention supplémentaire de votre part.  
  
> [!NOTE]
>  Les propriétés réservées ne peuvent pas être redéfinies dans le fichier projet.  
  
## <a name="example"></a>Exemple  
 L’exemple de fichier projet suivant référence le nom du projet en tant que propriété réservée pour spécifier le nom de la sortie.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"   
    DefaultTargets = "Compile">  
  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
     </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using  
        input files of type CSFile -->  
        <CSC Sources = "@(CSFile)"  
            OutputAssembly = "$(MSBuildProjectName).exe" >  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the project -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  

## <a name="example"></a>Exemple
 L’exemple de fichier projet suivant utilise la propriété réservée `MSBuildProjectDirectory` pour créer le chemin complet à un fichier à l’emplacement du fichier projet.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">     
    
    <!-- Build the path to a file in the root of the project -->  
    <PropertyGroup>  
        <NewFilePath>$([System.IO.Path]::Combine($(MSBuildProjectDirectory), `BuildInfo.txt`))</NewFilePath>
    </PropertyGroup>  
</Project>  
```  
  
## <a name="see-also"></a>Voir aussi  
[MSBuild](../msbuild/msbuild.md)  
[Propriétés réservées et connues de MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
