---
title: 'Procédure : Utiliser des caractères XML réservés dans les fichiers projet | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9943378043c7ddd5787d32b331334555b27cd947
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54780638"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Procédure : Utiliser des caractères XML réservés dans les fichiers projet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Lorsque vous créez des fichiers projet, vous devrez peut-être utiliser des caractères XML réservés, par exemple, dans les valeurs de propriétés ou dans les valeurs de paramètres de tâche. Toutefois, certains caractères réservés doivent être remplacés par une entité nommée afin que le fichier projet puisse être analysé.  
  
## <a name="using-reserved-characters"></a>Utilisation de caractères réservés  
 Le tableau suivant décrit les caractères XML réservés qui doivent être remplacés par l’entité nommée correspondante afin que le fichier projet puisse être analysé.  
  
|Caractère réservé|Entité nommée|  
|------------------------|------------------|  
|\<|&lt;|  
|>|&gt;|  
|&|&amp;|  
|"|&quot;|  
|'|&apos;|  
  
#### <a name="to-use-double-quotes-in-a-project-file"></a>Pour utiliser des guillemets doubles dans un fichier projet  
  
-   Remplacez les guillemets doubles par l’entité nommée correspondante, &quot;. Par exemple, pour placer des guillemets doubles autour de la liste d’éléments `EXEFile`, tapez :  
  
    ```  
    <Message Text="The output file is "@(EXEFile)"."/>  
    ```  
  
## <a name="example"></a>Exemple  
 Dans l’exemple de code suivant, des guillemets doubles sont utilisés pour mettre en surbrillance le nom de fichier dans le message qui est sorti par le fichier projet.  
  
```  
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
        <Message Text="The output file is "@(EXEFile)"."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence MSBuild](../msbuild/msbuild-reference.md) [MSBuild](msbuild.md)
