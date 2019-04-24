---
title: 'Procédure : Générer les mêmes fichiers sources avec des options différentes | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- source files, building with different options
- MSBuild, properties
- project properties, modifying
- Hello World example [Visual Studio]
ms.assetid: d14f1212-ddd9-434f-b138-f840011b0fb2
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3bce742d4ce0374cb7270b964354d65a03e917d0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045601"
---
# <a name="how-to-build-the-same-source-files-with-different-options"></a>Procédure : Générer les mêmes fichiers sources avec des options différentes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque vous générez des projets, vous compilez fréquemment les mêmes composants avec des options de génération différentes. Par exemple, vous pouvez créer une version Debug avec des informations de symbole ou une version Release sans informations de symbole, mais avec les optimisations activées. Vous pouvez également générer un projet pour qu’il s’exécute sur une plateforme spécifique, par exemple x86 ou [!INCLUDE[vcprx64](../includes/vcprx64-md.md)]. Dans toutes ces situations, la plupart des options de génération restent identiques ; seules quelques options sont modifiées pour contrôler la configuration de build. Avec [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], vous utiliser des propriétés et des conditions pour créer les différentes configurations de build.  
  
## <a name="using-properties-to-modify-projects"></a>Utilisation des propriétés pour modifier des projets  
 L’élément `Property` définit une variable qui est référencée plusieurs fois dans un fichier projet, par exemple l’emplacement d’un répertoire temporaire, ou définit les valeurs des propriétés qui sont utilisées dans plusieurs configurations, comme une version Debug et une version Release. Pour plus d’informations sur les propriétés, consultez l’article [Propriétés MSBuild](msbuild-properties1.md).  
  
 Les propriétés permettent de modifier la configuration de votre build sans avoir à modifier le fichier projet. L’attribut `Condition` des éléments `Property` et `PropertyGroup` vous permet de modifier la valeur des propriétés. Pour plus d’informations sur les conditions [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], consultez l’article [Conditions (Conditions MSBuild)](../msbuild/msbuild-conditions.md).  
  
#### <a name="to-set-a-group-of-properties-based-on-another-property"></a>Pour définir un groupe de propriétés en fonction d’une autre propriété  
  
- Utilisez un attribut `Condition` dans un élément `PropertyGroup` semblable à ce qui suit :  
  
    ```  
    <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">  
        <DebugType>full</DebugType>  
        <Optimize>no</Optimize>  
    </PropertyGroup>  
    ```  
  
#### <a name="to-define-a-property-based-on-another-property"></a>Pour définir une propriété en fonction d’une autre propriété  
  
- Utilisez un attribut `Condition` dans un élément `Property` semblable à ce qui suit :  
  
    ```  
    <DebugType Condition="'$(Flavor)'=='DEBUG'">full</DebugType>  
    ```  
  
## <a name="specifying-properties-on-the-command-line"></a>Spécification de propriétés sur la ligne de commande  
 Une fois que votre fichier projet est écrit pour accepter plusieurs configurations, vous devez être en mesure de modifier ces configurations à chaque fois que vous générez votre projet. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] vous en donne la possibilité en permettant de spécifier des propriétés sur la ligne de commande à l’aide du commutateur **/property** ou **/p**.  
  
#### <a name="to-set-a-project-property-at-the-command-line"></a>Pour définir une propriété de projet dans la ligne de commande  
  
- Utilisez le commutateur **/property** avec la propriété et la valeur de la propriété. Exemple :  
  
    ```  
    msbuild file.proj /property:Flavor=Debug  
    ```  
  
     - ou  
  
    ```  
    Msbuild file.proj /p:Flavor=Debug  
    ```  
  
#### <a name="to-specify-more-than-one-project-property-at-the-command-line"></a>Pour spécifier plusieurs propriétés de projet dans la ligne de commande  
  
- Utilisez le commutateur **/property** ou **/p** plusieurs fois avec la propriété et les valeurs de propriétés, ou utilisez un commutateur **/property** ou **/p** et séparez plusieurs propriétés avec des points-virgules (;). Exemple :  
  
  ```  
  msbuild file.proj /p:Flavor=Debug;Platform=x86  
  ```  
  
   - ou  
  
  ```  
  msbuild file.proj /p:Flavor=Debug /p:Platform=x86  
  ```  
  
  Les variables d’environnement sont également considérées comme des propriétés et sont automatiquement intégrées par [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Pour plus d’informations sur l’utilisation des variables d’environnement, consultez [Guide pratique pour Utiliser des Variables d’environnement dans une génération](../msbuild/how-to-use-environment-variables-in-a-build.md).  
  
  La valeur de propriété spécifiée sur la ligne de commande est prioritaire sur toute valeur qui est définie pour la même propriété dans le fichier projet, et cette valeur du fichier projet est prioritaire sur la valeur d’une variable d’environnement.  
  
  Vous pouvez changer ce comportement à l’aide de l’attribut `TreatAsLocalProperty` dans une balise de projet. Pour les noms de propriété répertoriés avec cet attribut, la valeur de propriété qui est spécifiée sur la ligne de commande n’est pas prioritaire sur la valeur indiquée dans le fichier projet. Vous en trouverez un exemple plus loin dans cette rubrique.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant, le projet « Hello World », contient deux nouveaux groupes de propriétés qui peuvent être utilisés pour créer une version Debug et une version Release.  
  
 Pour générer la version Debug de ce projet, tapez :  
  
```  
msbuild consolehwcs1.proj /p:flavor=debug  
```  
  
 Pour générer la version commerciale de ce projet, tapez :  
  
```  
msbuild consolehwcs1.proj /p:flavor=retail  
```  
  
```  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <!-- Sets the default flavor of an environment variable called   
    Flavor is not set or specified on the command line -->  
    <PropertyGroup>  
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>  
    </PropertyGroup>  
  
    <!-- Define the DEBUG settings -->  
    <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">  
        <DebugType>full</DebugType>  
        <Optimize>no</Optimize>  
    </PropertyGroup>  
  
    <!-- Define the RETAIL settings -->  
    <PropertyGroup Condition="'$(Flavor)'=='RETAIL'">  
        <DebugType>pdbonly</DebugType>  
        <Optimize>yes</Optimize>  
    </PropertyGroup>  
  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>HelloWorldCS</appname>  
    </PropertyGroup>  
  
    <!-- Specify the inputs by type and file name -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input files  
        of type CSFile -->  
        <CSC  Sources = "@(CSFile)"  
            DebugType="$(DebugType)"  
            Optimize="$(Optimize)"  
            OutputAssembly="$(appname).exe" >  
  
            <!-- Set the OutputAssembly attribute of the CSC  
            task to the name of the executable file that is   
            created -->  
            <Output TaskParameter="OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser l’attribut `TreatAsLocalProperty`. La propriété `Color` a la valeur `Blue` dans le fichier projet et la valeur `Green` dans la ligne de commande. Avec `TreatAsLocalProperty="Color"` dans la balise de projet, la propriété de ligne de commande (`Green`) ne remplace pas la propriété qui est définie dans le fichier projet (`Blue`).  
  
 Pour générer le projet, entrez la commande suivante :  
  
```  
msbuild colortest.proj /t:go /property:Color=Green  
```  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
ToolsVersion="4.0" TreatAsLocalProperty="Color">  
  
    <PropertyGroup>  
        <Color>Blue</Color>  
    </PropertyGroup>  
  
    <Target Name="go">  
        <Message Text="Color: $(Color)" />  
    </Target>  
</Project>  
  
<!--  
  Output with TreatAsLocalProperty="Color" in project tag:  
     Color: Blue  
  
  Output without TreatAsLocalProperty="Color" in project tag:  
     Color: Green  
-->  
```  
  
## <a name="see-also"></a>Voir aussi  
[MSBuild](msbuild.md)  
 [Concepts MSBuild](../msbuild/msbuild-concepts.md)   
 [Référence MSBuild](../msbuild/msbuild-reference.md)   
 [Project, élément (MSBuild)](../msbuild/project-element-msbuild.md)
