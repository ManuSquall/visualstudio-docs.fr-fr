---
title: "Éléments MSBuild | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MSBuild, Items
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
caps.latest.revision: "35"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bec7bd5420c16d291db2566e86dd47ba986cca37
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="msbuild-items"></a>Éléments MSBuild
Les éléments MSBuild sont des entrées du système de génération qui représentent généralement des fichiers. Les éléments sont regroupés en différents types selon leurs noms d’élément. Les types d’élément sont des listes nommées d’éléments qui peuvent être utilisés comme paramètres pour les tâches. Les tâches utilisent les valeurs d’élément pour exécuter les étapes du processus de génération.  
  
 Comme les éléments sont nommés en fonction du type d’élément dont ils font partie, les termes « élément » et « valeur d’élément » peuvent être utilisés indifféremment.  
  
 **Dans cette rubrique**  
  
-   [Création d’éléments dans un fichier projet](#BKMK_Creating1)  
  
-   [Création d’éléments lors de l’exécution](#BKMK_Creating2)  
  
-   [Référencement d’éléments dans un fichier projet](#BKMK_ReferencingItems)  
  
-   [Utilisation de caractères génériques pour spécifier des éléments](#BKMK_Wildcards)  
  
-   [Utilisation de l’attribut Exclude](#BKMK_ExcludeAttribute)  
  
-   [Métadonnées d’élément](#BKMK_ItemMetadata)  
  
    -   [Référencement des métadonnées d’élément dans un fichier projet](#BKMK_ReferencingItemMetadata)  
  
    -   [Métadonnées d’élément connues](#BKMK_WellKnownItemMetadata)  
  
    -   [Transformation des types d’élément à l’aide de métadonnées](#BKMK_Transforming)  
  
-   [Définitions d’éléments](#BKMK_ItemDefinitions)  
  
-   [Attributs des éléments d’un ItemGroup d’une cible](#BKMK_AttributesWithinTargets)  
  
    -   [Attribut Remove](#BKMK_RemoveAttribute)  
  
    -   [Attribut KeepMetadata](#BKMK_KeepMetadata)  
  
    -   [Attribut RemoveMetadata](#BKMK_RemoveMetadata)  
  
    -   [Attribut KeepDuplicates](#BKMK_KeepDuplicates)  
  
##  <a name="BKMK_Creating1"></a> Création d’éléments dans un fichier projet  
 Vous déclarez des éléments dans le fichier projet en tant qu’éléments enfants d’un élément [ItemGroup](../msbuild/itemgroup-element-msbuild.md). Le nom de l’élément enfant est le type de l’élément. L’attribut `Include` de l’élément spécifie les éléments (fichiers) à inclure avec ce type d’élément. Par exemple, le code XML suivant crée un type d’élément nommé `Compile` et composé de deux fichiers.  
  
```xml  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 L’élément « file2.cs » ne remplace pas l’élément « file1.cs ». Le nom de fichier est ajouté à la liste des valeurs correspondant au type d’élément `Compile`. Vous ne pouvez pas supprimer un élément d’un type d’élément pendant la phase d’évaluation d’une build.  
  
 Le code XML suivant crée le même type d’élément en déclarant les deux fichiers dans un attribut `Include`. Notez que les noms de fichiers sont séparés par un point-virgule.  
  
```xml  
<ItemGroup>  
    <Compile Include = "file1.cs;file2.cs"/>  
</ItemGroup>  
```  
  
##  <a name="BKMK_Creating2"></a> Création d’éléments lors de l’exécution  
 Des valeurs sont attribuées aux éléments situés en dehors des éléments [Target](../msbuild/target-element-msbuild.md) pendant la phase d’évaluation d’une génération. Pendant la phase d’exécution suivante, des éléments peuvent être créés ou modifiés en procédant comme suit :  
  
-   Une tâche peut émettre un élément. Pour émettre un élément, l’élément [Task](../msbuild/task-element-msbuild.md) doit posséder un élément [Output](../msbuild/output-element-msbuild.md) enfant pourvu d’un attribut `ItemName`.  
  
-   La tâche [CreateItem](../msbuild/createitem-task.md) peut émettre un élément. Cette utilisation est dépréciée.  
  
-   Depuis .NET Framework 3.5, les éléments `Target` peuvent contenir des éléments [ItemGroup](../msbuild/itemgroup-element-msbuild.md) qui peuvent comporter des éléments Item.  
  
##  <a name="BKMK_ReferencingItems"></a> Référencement d’éléments dans un fichier projet  
 Pour référencer des types d’éléments dans tout le fichier projet, vous devez utiliser la syntaxe @(`ItemType`). Par exemple, vous devez référencer le type d’élément dans l’exemple précédent en utilisant `@(Compile)`. À l’aide de cette syntaxe, vous pouvez transmettre des éléments aux tâches en spécifiant le type d’élément en tant que paramètre de la tâche en question. Pour plus d’informations, consultez l’article [Guide pratique pour sélectionner des fichiers dans une build](../msbuild/how-to-select-the-files-to-build.md).  
  
 Par défaut, les éléments d’un type d’élément développé sont séparés par des points-virgules (;). Vous pouvez utiliser la syntaxe @(*ItemType*, ’*separator*’) pour spécifier un séparateur autre que celui indiqué par défaut. Pour plus d’informations, consultez l’article [Comment : afficher une liste d’éléments séparés par des virgules](../msbuild/how-to-display-an-item-list-separated-with-commas.md).  
  
##  <a name="BKMK_Wildcards"></a> Utilisation de caractères génériques pour spécifier des éléments  
 Vous pouvez utiliser les caractères génériques **, \* et ? pour spécifier un groupe de fichiers comme entrées d’une génération au lieu de répertorier chaque fichier séparément.  
  
-   Le caractère générique ? correspond à un caractère unique.  
  
-   Le caractère générique * correspond à zéro ou plusieurs caractères.  
  
-   La séquence de caractères génériques ** correspond à un chemin d’accès partiel.  
  
 Par exemple, vous pouvez spécifier tous les fichiers .cs du répertoire qui contient le fichier projet à l’aide de l’élément ci-dessous contenu dans votre fichier projet.  
  
```xml  
<CSFile Include="*.cs"/>  
```  
  
 L’élément suivant permet de sélectionner tous les fichiers .vb sur le lecteur D: :  
  
```xml  
<VBFile Include="D:/**/*.vb"/>  
```  
  
 Pour plus d’informations sur les caractères génériques, consultez l’article [Guide pratique pour sélectionner des fichiers dans une build](../msbuild/how-to-select-the-files-to-build.md).  
  
##  <a name="BKMK_ExcludeAttribute"></a> Utilisation de l’attribut Exclude  
 Les éléments Item peuvent contenir l’attribut `Exclude` qui exclut des éléments spécifiques (fichiers) du type d’élément. L’attribut `Exclude` est généralement utilisé avec des caractères génériques. Par exemple, le code XML suivant ajoute tous les fichiers .cs du répertoire au type d’élément CSFile, à l’exception du fichier `DoNotBuild.cs`.  
  
```xml  
<ItemGroup>  
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>  
</ItemGroup>  
```  
  
 L’attribut `Exclude` affecte uniquement les éléments qui sont ajoutés par l’attribut `Include` dans l’élément Item qui les contient. Dans l’exemple suivant, le fichier Form1.cs, qui a été ajouté dans l’élément Item précédent n’est pas exclu.  
  
```xml  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 Pour plus d’informations, consultez l’article [Comment : exclure des fichiers de la génération](../msbuild/how-to-exclude-files-from-the-build.md).  
  
##  <a name="BKMK_ItemMetadata"></a> Métadonnées d’élément  
 Outre les informations des attributs `Include` et `Exclude`, les éléments peuvent contenir des métadonnées. Ces métadonnées peuvent être utilisées par les tâches qui requièrent plus d’informations sur les éléments ou pour traiter par lot les tâches et les cibles. Pour plus d’informations, consultez l’article [Batching (Traitement par lot MSBuild)](../msbuild/msbuild-batching.md).  
  
 Les métadonnées sont une collection de paires clé-valeur qui sont déclarées dans le fichier projet en tant qu’éléments enfants d’un élément Item. Le nom et la valeur de l’élément enfant correspondent au nom et à la valeur de la métadonnée.  
  
 La métadonnée est associée à l’élément Item qui le contient. Par exemple, le code XML suivant ajoute la métadonnée `Culture` qui a la valeur `Fr` aux éléments « one.cs » et « two.cs » du type d’élément CSFile.  
  
```xml  
<ItemGroup>  
    <CSFile Include="one.cs;two.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 Un élément peut comporter zéro ou plusieurs valeurs de métadonnées. Vous pouvez modifier des valeurs de métadonnées à tout moment. Si vous définissez une métadonnée sur une valeur vide, vous la supprimez de la génération.  
  
###  <a name="BKMK_ReferencingItemMetadata"></a> Référencement des métadonnées d’élément dans un fichier projet  
 Vous pouvez référencer des métadonnées d’élément dans tout le fichier projet à l’aide de la syntaxe %(`ItemMetadataName`). En cas d’ambiguïté, vous pouvez qualifier une référence à l’aide du nom du type d’élément. Par exemple, vous pouvez spécifier %(*ItemType.ItemMetaDataName*). Dans l’exemple suivant, la métadonnée Display permet de traiter par lot la tâche Message. Pour plus d’informations sur l’utilisation des métadonnées d’élément pour le traitement par lot, consultez l’article [Item Metadata in Task Batching (Métadonnées d’élément dans le traitement par lot des tâches)](../msbuild/item-metadata-in-task-batching.md).  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Stuff Include="One.cs" >  
            <Display>false</Display>  
        </Stuff>  
        <Stuff Include="Two.cs">  
            <Display>true</Display>  
        </Stuff>  
    </ItemGroup>  
    <Target Name="Batching">  
        <Message Text="@(Stuff)" Condition=" '%(Display)' == 'true' "/>  
    </Target>  
</Project>  
```  
  
###  <a name="BKMK_WellKnownItemMetadata"></a> Métadonnées d’élément connues  
 Lorsqu’un élément est ajouté à un type d’élément, des métadonnées connues lui sont attribuées. Par exemple, tous les éléments possèdent la métadonnée connue `%(Filename)`, dont la valeur correspond au nom de fichier de l’élément. Pour plus d’informations, consultez l’article [Well-known Item Metadata (Métadonnées d’élément connues MSBuild)](../msbuild/msbuild-well-known-item-metadata.md).  
  
###  <a name="BKMK_Transforming"></a> Transformation des types d’élément à l’aide de métadonnées  
 Vous pouvez transformer des listes d’éléments en nouvelles listes d’éléments à l’aide de métadonnées. Par exemple, vous pouvez transformer un type d’élément `CppFiles` qui contient des éléments représentant des fichiers .cpp en une liste correspondante de fichiers .obj à l’aide de l’expression `@(CppFiles -> '%(Filename).obj')`.  
  
 Le code suivant crée un type d’élément `CultureResource` qui contient des copies de tous les éléments `EmbeddedResource` comportant la métadonnée `Culture`. La valeur de la métadonnée `Culture` devient la valeur de la nouvelle métadonnée `CultureResource.TargetDirectory`.  
  
```xml  
<Target Name="ProcessCultureResources">  
    <ItemGroup>  
        <CultureResource Include="@(EmbeddedResource)"  
            Condition="'%(EmbeddedResource.Culture)' != ''">  
            <TargetDirectory>%(EmbeddedResource.Culture) </TargetDirectory>  
        </CultureResource>  
    </ItemGroup>  
</Target>  
```  
  
 Pour plus d’informations, consultez l’article [Transforms (Transformations MSBuild)](../msbuild/msbuild-transforms.md).  
  
##  <a name="BKMK_ItemDefinitions"></a> Définitions d’éléments  
 Depuis .NET Framework 3.5, vous pouvez ajouter des métadonnées par défaut à tout type d’élément à l’aide de l’[élément ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md). À l’instar des métadonnées connues, les métadonnées par défaut sont associées à tous les éléments du type d’élément que vous spécifiez. Vous pouvez remplacer les métadonnées par défaut dans une définition d’élément de façon explicite. Par exemple, le code XML suivant fournit aux éléments `Compile` « one.cs » et « three.cs » la métadonnée `BuildDay` pourvue de la valeur « Monday ». Le code donne à l’élément « two.cs » la métadonnée `BuildDay` pourvue de la valeur « Tuesday ».  
  
```xml  
<ItemDefinitionGroup>  
    <Compile>  
        <BuildDay>Monday</BuildDay>  
    </Compile>  
</ItemDefinitionGroup>  
<ItemGroup>  
    <Compile Include="one.cs;three.cs" />  
    <Compile Include="two.cs">  
        <BuildDay>Tuesday</BuildDay>  
    </Compile>  
</ItemGroup>  
```  
  
 Pour plus d’informations, consultez l’article [Item Definitions (Définitions des éléments)](../msbuild/item-definitions.md).  
  
##  <a name="BKMK_AttributesWithinTargets"></a> Attributs des éléments d’un ItemGroup d’une cible  
 Depuis .NET Framework 3.5, les éléments `Target` peuvent contenir des éléments [ItemGroup](../msbuild/itemgroup-element-msbuild.md) qui peuvent comporter des éléments Item. Les attributs de cette section sont valides s’ils sont spécifiés pour un élément d’un `ItemGroup` qui se trouve dans une `Target`.  
  
###  <a name="BKMK_RemoveAttribute"></a> Attribut Remove  
 Les éléments d’un `ItemGroup` d’une cible peuvent contenir l’attribut `Remove`, qui supprime des éléments spécifiques (fichiers) du type d’élément. (Cet attribut a été introduit dans .NET Framework 3.5).  
  
 Dans l’exemple suivant, tous les fichiers .config sont supprimés du type d’élément Compile.  
  
```xml  
<Target>  
    <ItemGroup>  
        <Compile Remove="*.config"/>  
    </ItemGroup>  
</Target>  
```  
  
###  <a name="BKMK_KeepMetadata"></a> Attribut KeepMetadata  
 Si un élément est généré au sein d’une cible, l’élément Item peut contenir l’attribut `KeepMetadata`. Si cet attribut est spécifié, seules les métadonnées qui sont spécifiées dans la liste de noms séparés par des points-virgules sont transférées de l’élément source à l’élément cible. Pour cet attribut, utiliser une valeur vide revient à ne pas le spécifier. L’attribut `KeepMetadata` a été introduit dans .NET Framework 4.5.  
  
 L’exemple suivant montre comment utiliser l’attribut `KeepMetadata`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
ToolsVersion="4.0">  
  
    <ItemGroup>  
        <FirstItem Include="rhinoceros">  
            <Class>mammal</Class>  
            <Size>large</Size>  
        </FirstItem>  
  
    </ItemGroup>  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <SecondItem Include="@(FirstItem)" KeepMetadata="Class" />  
        </ItemGroup>  
  
        <Message Text="FirstItem: %(FirstItem.Identity)" />  
        <Message Text="  Class: %(FirstItem.Class)" />  
        <Message Text="  Size:  %(FirstItem.Size)"  />  
  
        <Message Text="SecondItem: %(SecondItem.Identity)" />  
        <Message Text="  Class: %(SecondItem.Class)" />  
        <Message Text="  Size:  %(SecondItem.Size)"  />  
    </Target>  
</Project>  
  
<!--  
Output:  
  FirstItem: rhinoceros  
    Class: mammal  
    Size:  large  
  SecondItem: rhinoceros  
    Class: mammal  
    Size:   
-->  
```  
  
###  <a name="BKMK_RemoveMetadata"></a> Attribut RemoveMetadata  
 Si un élément est généré au sein d’une cible, l’élément Item peut contenir l’attribut `RemoveMetadata`. Si cet attribut est spécifié, toutes les métadonnées sont transférées de l’élément source vers l’élément cible, à l’exception des métadonnées dont les noms figurent dans la liste de noms séparés par des points-virgules. Pour cet attribut, utiliser une valeur vide revient à ne pas le spécifier. L’attribut `RemoveMetadata` a été introduit dans .NET Framework 4.5.  
  
 L’exemple suivant montre comment utiliser l’attribut `RemoveMetadata`.  
  
```xml  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <MetadataToRemove>Size;Material</MetadataToRemove>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <Item1 Include="stapler">  
            <Size>medium</Size>  
            <Color>black</Color>  
            <Material>plastic</Material>  
        </Item1>  
    </ItemGroup>  
  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <Item2 Include="@(Item1)" RemoveMetadata="$(MetadataToRemove)" />  
        </ItemGroup>  
  
        <Message Text="Item1: %(Item1.Identity)" />  
        <Message Text="  Size:     %(Item1.Size)" />  
        <Message Text="  Color:    %(Item1.Color)" />  
        <Message Text="  Material: %(Item1.Material)" />  
        <Message Text="Item2: %(Item2.Identity)" />  
        <Message Text="  Size:     %(Item2.Size)" />  
        <Message Text="  Color:    %(Item2.Color)" />  
        <Message Text="  Material: %(Item2.Material)" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Item1: stapler  
    Size:     medium  
    Color:    black  
    Material: plastic  
  Item2: stapler  
    Size:       
    Color:    black  
    Material:   
-->  
```  
  
###  <a name="BKMK_KeepDuplicates"></a> Attribut KeepDuplicates  
 Si un élément est généré au sein d’une cible, l’élément Item peut contenir l’attribut `KeepDuplicates`. `KeepDuplicates` est un attribut `Boolean` qui spécifie si un élément doit être ajouté au groupe cible si l’élément est une copie exacte d’un élément existant.  
  
 Si les éléments source et cible ont la même valeur Include, mais des métadonnées différentes, l’élément est ajouté même si l’attribut `KeepDuplicates` est défini sur `false`. Pour cet attribut, utiliser une valeur vide revient à ne pas le spécifier. L’attribut `KeepDuplicates` a été introduit dans .NET Framework 4.5.  
  
 L’exemple suivant montre comment utiliser l’attribut `KeepDuplicates`.  
  
```xml  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Item1 Include="hourglass;boomerang" />  
        <Item2 Include="hourglass;boomerang" />  
    </ItemGroup>  
  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <Item1 Include="hourglass" KeepDuplicates="false" />  
            <Item2 Include="hourglass" />  
        </ItemGroup>  
  
        <Message Text="Item1: @(Item1)" />  
        <Message Text="  %(Item1.Identity)  Count: @(Item1->Count())" />  
        <Message Text="Item2: @(Item2)" />  
        <Message Text="  %(Item2.Identity)  Count: @(Item2->Count())" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Item1: hourglass;boomerang  
    hourglass  Count: 1  
    boomerang  Count: 1  
  Item2: hourglass;boomerang;hourglass  
    hourglass  Count: 2  
    boomerang  Count: 1  
-->  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts MSBuild](../msbuild/msbuild-concepts.md)  
 [MSBuild](../msbuild/msbuild.md)   
 [Guide pratique pour sélectionner des fichiers dans une build](../msbuild/how-to-select-the-files-to-build.md)   
 [Comment : exclure des fichiers de la génération](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Comment : afficher une liste d’éléments séparés par des virgules](../msbuild/how-to-display-an-item-list-separated-with-commas.md)   
 [Item Definitions (Définitions d’éléments)](../msbuild/item-definitions.md)   
 [Traitement par lot MSBuild](../msbuild/msbuild-batching.md)   
 [Item, élément (MSBuild)](../msbuild/item-element-msbuild.md)