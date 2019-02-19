---
title: 'Comment : générer un projet qui dispose de ressources | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b45d2dfedcc020a5b6206e4c419c0e4b7f9b0f02
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54803999"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Comment : générer un projet qui dispose de ressources
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Si vous générez les versions localisées d’un projet, tous les éléments de l’interface utilisateur doivent être séparés dans des fichiers de ressources correspondant aux différentes langues. Si le projet utilise uniquement des chaînes, les fichiers de ressources peuvent utiliser des fichiers texte. Vous pouvez également utiliser des fichiers .resx comme fichiers de ressources.  
  
## <a name="compiling-resources-with-msbuild"></a>Compilation des ressources avec MSBuild  
 La bibliothèque de tâches courantes qui est fournie avec [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] inclut une tâche `GenerateResource` que vous pouvez utiliser pour compiler les ressources dans des fichiers .resx ou texte. Cette tâche inclut le paramètre `Sources` pour spécifier les fichiers de ressources à compiler et le paramètre `OutputResources` pour spécifier les noms des fichiers de ressources de sortie. Pour plus d’informations sur la tâche `GenerateResource`, consultez l’article [GenerateResource Task (Tâche GenerateResource)](../msbuild/generateresource-task.md).  
  
#### <a name="to-compile-resources-with-msbuild"></a>Pour compiler des ressources avec MSBuild  
  
1.  Identifiez les fichiers de ressources du projet et transmettez-les à la tâche `GenerateResource`, en tant que listes d’éléments ou noms de fichiers.  
  
2.  Spécifiez le paramètre `OutputResources` de la tâche `GenerateResource`, qui vous permet de définir les noms des fichiers de ressources de sortie.  
  
3.  Utilisez l’élément `Output` de la tâche pour stocker la valeur du paramètre `OutputResources` dans un élément.  
  
4.  Utilisez l’élément créé à partir de l’élément `Output` en tant qu’entrée d’une autre tâche.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment l’élément `Output` spécifie que l’attribut `OutputResources` de la tâche `GenerateResource` contient les fichiers de ressources compilés `alpha.resources` et `beta.resources` et que ces deux fichiers sont placés dans la liste d’éléments `Resources`. En identifiant ces fichiers .resources comme collection d’éléments du même nom, vous pouvez les utiliser facilement comme entrées d’une autre tâche, par exemple la tâche [Csc](../msbuild/csc-task.md).  
  
 Cette tâche revient à utiliser le commutateur **/compiler** pour [Resgen.exe](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) :  
  
 `Resgen.exe /compile alpha.resx,alpha.resources /compile beta.txt,beta.resources`  
  
```  
<GenerateResource  
    Sources="alpha.resx; beta.txt"  
    OutputResources="alpha.resources; beta.resources">  
    <Output TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
## <a name="example"></a>Exemple  
 L’exemple de projet suivant contient deux tâches : la tâche `GenerateResource` permet de compiler les ressources, et la tâche `Csc` permet de compiler les fichiers de code source et les fichiers de ressources compilés. Les fichiers de ressources compilés par la tâche `GenerateResource` sont stockés dans l’élément `Resources` et transmis à la tâche `Csc`.  
  
```  
<Project DefaultTargets = "Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <Target Name="Resources">  
        <GenerateResource  
            Sources="alpha.resx; beta.txt"  
            OutputResources="alpha.resources; beta.resources">  
            <Output TaskParameter="OutputResources"  
                ItemName="Resources"/>  
        </GenerateResource>  
    </Target>  
  
    <Target Name="Build" DependsOnTargets="Resources">  
        <Csc Sources="hello.cs"  
                Resources="@(Resources)"  
                OutputAssembly="hello.exe"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Voir aussi  
[MSBuild](msbuild.md)  
 [GenerateResource Task (Tâche GenerateResource)](../msbuild/generateresource-task.md)   
 [Tâche Csc](../msbuild/csc-task.md)   
 [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4)
