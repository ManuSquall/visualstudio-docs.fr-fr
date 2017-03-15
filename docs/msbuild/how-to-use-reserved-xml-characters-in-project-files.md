---
title: "Comment : utiliser des caractères XML réservés dans les fichiers projet | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
caps.latest.revision: 14
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 3ba7680d46345f2b49019659c715cfb418933d39
ms.openlocfilehash: f4b909c055e6ae3734ef8d53717c119c534689df

---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Comment : utiliser des caractères XML réservés dans les fichiers projet
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
  
    ```xml  
    <Message Text="The output file is "@(EXEFile)"."/>  
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
        <Message Text="The output file is "@(EXEFile)"."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence MSBuild](../msbuild/msbuild-reference.md)
 [MSBuild](../msbuild/msbuild.md)


<!--HONumber=Feb17_HO4-->


