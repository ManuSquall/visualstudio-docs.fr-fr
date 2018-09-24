---
title: 'Comment : utiliser des caractères XML réservés dans les fichiers projet | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 647dba94840383410d06f6e5bf96ec3b0146c394
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077657"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Guide pratique pour utiliser des caractères XML réservés dans les fichiers projet
Lorsque vous créez des fichiers projet, vous devrez peut-être utiliser des caractères XML réservés, par exemple, dans les valeurs de propriétés ou dans les valeurs de paramètres de tâche. Toutefois, certains caractères réservés doivent être remplacés par une entité nommée afin que le fichier projet puisse être analysé.  
  
## <a name="use-reserved-characters"></a>Utiliser des caractères réservés  
 Le tableau suivant décrit les caractères XML réservés qui doivent être remplacés par l’entité nommée correspondante afin que le fichier projet puisse être analysé.  
  
|Caractère réservé|Entité nommée|  
|------------------------|------------------|  
|\<|&amp;lt;|  
|>|&amp;gt;|  
|&|&amp;amp;|  
|"|&amp;quot;|  
|'|&amp;apos;|  
  
#### <a name="to-use-double-quotes-in-a-project-file"></a>Pour utiliser des guillemets doubles dans un fichier projet  
  
-   Remplacez les guillemets doubles par l’entité nommée correspondante, &amp;quot;. Par exemple, pour placer des guillemets doubles autour de la liste d’éléments `EXEFile`, tapez :  
  
    ```xml  
    <Message Text="The output file is &quot;@(EXEFile)&quot;."/>  
    ```  
  
## <a name="example"></a>Exemple  
 Dans l’exemple de code suivant, des guillemets doubles sont utilisés pour mettre en surbrillance le nom de fichier dans le message qui est sorti par le fichier projet.  
  
```xml  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>"HelloWorldCS"</appname>  
    </PropertyGroup>  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs" />  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input  
        files of type CSFile -->  
        <Csc Sources = "@(CSFile)">  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the executable file that is created -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile"/>  
        </Csc>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is &quot;@(EXEFile)&quot;."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)    
 [MSBuild](../msbuild/msbuild.md)    
