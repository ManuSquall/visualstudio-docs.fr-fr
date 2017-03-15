---
title: "&#201;l&#233;ments MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, éléments"
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
caps.latest.revision: 35
caps.handback.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &#201;l&#233;ments MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Éléments MSBuild sont entrées dans le système de génération, et elles représentent généralement des fichiers. Les éléments sont regroupés en types selon leurs noms d’élément. Types d’éléments sont nommés de listes d’éléments qui peuvent être utilisés comme paramètres pour les tâches. Les tâches utilisent les valeurs d’élément pour exécuter les étapes du processus de génération.  
  
 Éléments sont nommés en fonction du type d’élément auquel ils appartiennent, les termes « item » et « valeur d’élément » peuvent être utilisés indifféremment.  
  
 **Dans cette rubrique.**  
  
-   [Création d’un fichier de projet](#BKMK_Creating1)  
  
-   [Création d’éléments lors de l’exécution](#BKMK_Creating2)  
  
-   [Référencement d’éléments dans un fichier de projet](#BKMK_ReferencingItems)  
  
-   [Utilisation des caractères génériques pour spécifier des éléments](#BKMK_Wildcards)  
  
-   [À l’aide de l’attribut Exclude](#BKMK_ExcludeAttribute)  
  
-   [Métadonnées d’élément](#BKMK_ItemMetadata)  
  
    -   [Référencement des métadonnées d’éléments dans un fichier de projet](#BKMK_ReferencingItemMetadata)  
  
    -   [Métadonnées d’éléments connus](#BKMK_WellKnownItemMetadata)  
  
    -   [Transformation de Types d’éléments à l’aide de métadonnées](#BKMK_Transforming)  
  
-   [Définitions d’éléments](#BKMK_ItemDefinitions)  
  
-   [Attributs pour les éléments dans un ItemGroup d’une cible](#BKMK_AttributesWithinTargets)  
  
    -   [Supprimer l’attribut](#BKMK_RemoveAttribute)  
  
    -   [Attribut de KeepMetadata](#BKMK_KeepMetadata)  
  
    -   [Attribut de RemoveMetadata](#BKMK_RemoveMetadata)  
  
    -   [Attribut de KeepDuplicates](#BKMK_KeepDuplicates)  
  
##  <a name="a-namebkmkcreating1a-creating-items-in-a-project-file"></a><a name="BKMK_Creating1"></a> Création d’un fichier de projet  
 Vous déclarez les éléments dans le fichier projet en tant qu’enfant éléments d’un [ItemGroup](../msbuild/itemgroup-element-msbuild.md) élément. Le nom de l’élément enfant est le type de l’élément. Le `Include` attribut de l’élément spécifie les éléments (fichiers) à inclure avec ce type d’élément. Par exemple, le code XML suivant crée un type d’élément nommé `Compile`, qui inclut deux fichiers.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 L’élément « file2.cs » ne remplace pas l’élément « file1.cs » ; au lieu de cela, le nom de fichier est ajouté à la liste des valeurs pour le `Compile` type d’élément. Vous ne pouvez pas supprimer un élément à partir d’un type d’élément pendant la phase d’évaluation d’une build.  
  
 Le code XML suivant crée le même type d’élément en déclarant les deux fichiers dans un `Include` attribut. Notez que les noms de fichiers sont séparés par un point-virgule.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs;file2.cs"/>  
</ItemGroup>  
```  
  
##  <a name="a-namebkmkcreating2a-creating-items-during-execution"></a><a name="BKMK_Creating2"></a> Création d’éléments lors de l’exécution  
 Les éléments situés en dehors de [cible](../msbuild/target-element-msbuild.md) valeurs sont assignées à éléments pendant la phase d’évaluation d’une build. Pendant la phase d’exécution suivante, des éléments peuvent être créés ou modifiés comme suit :  
  
-   Une tâche peut émettre un élément. Pour émettre un élément, le [tâche](../msbuild/task-element-msbuild.md) élément doit avoir un enfant [sortie](../msbuild/output-element-msbuild.md) élément ayant une `ItemName` attribut.  
  
-   Le [CreateItem](../msbuild/createitem-task.md) tâche peut émettre un élément. Cette utilisation est déconseillée.  
  
-   À compter de .NET Framework 3.5, `Target` peuvent contenir des éléments [ItemGroup](../msbuild/itemgroup-element-msbuild.md) éléments pouvant contenir des éléments d’élément.  
  
##  <a name="a-namebkmkreferencingitemsa-referencing-items-in-a-project-file"></a><a name="BKMK_ReferencingItems"></a> Référencement d’éléments dans un fichier de projet  
 Pour faire référence à des types d’éléments dans le fichier projet, vous utilisez la syntaxe @(`ItemType`). Par exemple, vous devez référencer le type d’élément dans l’exemple précédent à l’aide de `@(Compile)`. En utilisant cette syntaxe, vous pouvez passer des éléments aux tâches en spécifiant le type d’élément en tant que paramètre de cette tâche. Pour plus d’informations, consultez [Comment : sélectionner les fichiers de Build](../msbuild/how-to-select-the-files-to-build.md).  
  
 Par défaut, les éléments d’un type d’élément sont séparés par des points-virgules ( ;) lorsqu’il est développé. Vous pouvez utiliser la syntaxe @(*ItemType*, '*séparateur*') pour spécifier un séparateur autre que la valeur par défaut. Pour plus d’informations, consultez [Comment : afficher une liste des éléments séparés par des virgules](../msbuild/how-to-display-an-item-list-separated-with-commas.md).  
  
##  <a name="a-namebkmkwildcardsa-using-wildcards-to-specify-items"></a><a name="BKMK_Wildcards"></a> Utilisation des caractères génériques pour spécifier des éléments  
 Vous pouvez utiliser le **, \*, et ? caractères génériques pour spécifier un groupe de fichiers comme entrées pour une build au lieu de répertorier chaque fichier séparément.  
  
-   La barre d’outils ? caractère générique correspond à un caractère unique.  
  
-   Les * correspond à zéro ou plusieurs caractères.  
  
-   Le ** séquence de caractères génériques correspond à un chemin d’accès partiel.  
  
 Par exemple, vous pouvez spécifier tous les fichiers .cs dans le répertoire qui contient le fichier projet à l’aide de l’élément suivant dans votre fichier projet.  
  
```  
<CSFile Include="*.cs"/>  
```  
  
 L’élément suivant sélectionne tous les fichiers .vb sur le lecteur d :  
  
```  
<VBFile Include="D:/**/*.vb"/>  
```  
  
 Pour plus d’informations sur les caractères génériques, consultez [Comment : sélectionner les fichiers de Build](../msbuild/how-to-select-the-files-to-build.md).  
  
##  <a name="a-namebkmkexcludeattributea-using-the-exclude-attribute"></a><a name="BKMK_ExcludeAttribute"></a> À l’aide de l’attribut Exclude  
 Éléments item peuvent contenir le `Exclude` attribut qui exclut des éléments (fichiers) spécifiques du type d’élément. Le `Exclude` attribut est généralement utilisé avec des caractères génériques. Par exemple, le code XML suivant ajoute chaque fichier .cs dans le répertoire pour le type d’élément CSFile, à l’exception de la `DoNotBuild.cs` fichier.  
  
```  
<ItemGroup>  
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>  
</ItemGroup>  
```  
  
 Le `Exclude` attribut affecte uniquement les éléments qui sont ajoutés par le `Include` attribut dans l’élément item qui les contient. L’exemple suivant ne seraient pas exclure le fichier Form1.cs, qui a été ajoutée dans l’élément précédent.  
  
```  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 Pour plus d’informations, consultez [Comment : exclure des fichiers de la Build](../msbuild/how-to-exclude-files-from-the-build.md).  
  
##  <a name="a-namebkmkitemmetadataa-item-metadata"></a><a name="BKMK_ItemMetadata"></a> Métadonnées d’élément  
 Les éléments peuvent contenir des métadonnées en plus des informations dans les `Include` et `Exclude` les attributs. Ces métadonnées peuvent être utilisée par les tâches qui nécessitent plus d’informations sur les éléments ou cibles et les tâches de traitement par lots. Pour plus d’informations, consultez [le traitement par lots](../msbuild/msbuild-batching.md).  
  
 Les métadonnées sont une collection de paires clé-valeur qui sont déclarés dans le fichier projet en tant qu’éléments enfants d’un élément item. Le nom de l’élément enfant est le nom des métadonnées, et la valeur de l’élément enfant est la valeur des métadonnées.  
  
 Les métadonnées sont associées à l’élément qui le contient. Par exemple, le code XML suivant ajoute `Culture` métadonnées avec la valeur `Fr` pour les éléments « one.cs » et « Two.cs » de la CSFile type d’élément.  
  
```  
<ItemGroup>  
    <CSFile Include="one.cs;two.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 Un élément peut avoir zéro ou plusieurs valeurs de métadonnées. Vous pouvez modifier les valeurs de métadonnées à tout moment. Si vous définissez des métadonnées sur une valeur vide, vous le supprimez efficacement de la build.  
  
###  <a name="a-namebkmkreferencingitemmetadataa-referencing-item-metadata-in-a-project-file"></a><a name="BKMK_ReferencingItemMetadata"></a> Référencement des métadonnées d’éléments dans un fichier de projet  
 Vous pouvez référencer les métadonnées de l’élément dans le fichier projet à l’aide de la syntaxe %(`ItemMetadataName`). En cas d’ambiguïté, vous pouvez qualifier une référence en utilisant le nom du type d’élément. Par exemple, vous pouvez spécifier %(*ItemType.ItemMetaDataName*). L’exemple suivant utilise les métadonnées Display pour la tâche de traitement par lots. Pour plus d’informations sur l’utilisation des métadonnées de l’élément pour le traitement par lots, consultez [métadonnées d’éléments dans le traitement par lot par tâche](../msbuild/item-metadata-in-task-batching.md).  
  
```  
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
  
###  <a name="a-namebkmkwellknownitemmetadataa-well-known-item-metadata"></a><a name="BKMK_WellKnownItemMetadata"></a> Métadonnées d’éléments connus  
 Lorsqu’un élément est ajouté à un type d’élément, cet élément reçoit des métadonnées connues. Par exemple, tous les éléments ont les métadonnées connues `%(Filename)`, dont la valeur est le nom de fichier de l’élément. Pour plus d’informations, consultez la page [des métadonnées d’éléments connus](../msbuild/msbuild-well-known-item-metadata.md).  
  
###  <a name="a-namebkmktransforminga-transforming-item-types-by-using-metadata"></a><a name="BKMK_Transforming"></a> Transformation de Types d’éléments à l’aide de métadonnées  
 Vous pouvez transformer des listes d’éléments en nouvelles listes d’éléments à l’aide de métadonnées. Par exemple, vous pouvez transformer un type d’élément `CppFiles` qui contient des éléments qui représentent des fichiers .cpp en une liste correspondante de fichiers .obj à l’aide de l’expression `@(CppFiles -> '%(Filename).obj')`.  
  
 Le code suivant crée un `CultureResource` d’élément de type qui contient des copies de tous les `EmbeddedResource` avec des éléments `Culture` métadonnées. Le `Culture` métadonnées devient la valeur des nouvelles métadonnées `CultureResource.TargetDirectory`.  
  
```  
<Target Name="ProcessCultureResources">  
    <ItemGroup>  
        <CultureResource Include="@(EmbeddedResource)"  
            Condition="'%(EmbeddedResource.Culture)' != ''">  
            <TargetDirectory>%(EmbeddedResource.Culture) </TargetDirectory>  
        </CultureResource>  
    </ItemGroup>  
</Target>  
```  
  
 Pour plus d’informations, consultez [transforme](../msbuild/msbuild-transforms.md).  
  
##  <a name="a-namebkmkitemdefinitionsa-item-definitions"></a><a name="BKMK_ItemDefinitions"></a> Définitions d’éléments  
 À compter de .NET Framework 3.5, vous pouvez ajouter les métadonnées par défaut à n’importe quel type d’élément à l’aide de la [ItemDefinitionGroup, élément](../msbuild/itemdefinitiongroup-element-msbuild.md). Comme les métadonnées connues, les métadonnées par défaut sont associée à tous les éléments du type d’élément que vous spécifiez. Vous pouvez substituer explicitement les métadonnées par défaut dans une définition d’élément. Par exemple, le code XML suivant donne le `Compile` éléments « one.cs » et « three.cs » les métadonnées des éléments `BuildDay` avec la valeur « Monday ». Le code donne à l’élément « two.cs » les métadonnées `BuildDay` avec la valeur « Tuesday ».  
  
```  
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
  
 Pour plus d’informations, consultez [définitions d’élément](../msbuild/item-definitions.md).  
  
##  <a name="a-namebkmkattributeswithintargetsa-attributes-for-items-in-an-itemgroup-of-a-target"></a><a name="BKMK_AttributesWithinTargets"></a> Attributs pour les éléments dans un ItemGroup d’une cible  
 À compter de .NET Framework 3.5, `Target` peuvent contenir des éléments [ItemGroup](../msbuild/itemgroup-element-msbuild.md) éléments pouvant contenir des éléments d’élément. Les attributs de cette section sont valides lorsqu’elles sont spécifiées pour un élément dans un `ItemGroup` qui se trouve dans un `Target`.  
  
###  <a name="a-namebkmkremoveattributea-remove-attribute"></a><a name="BKMK_RemoveAttribute"></a> Supprimer l’attribut  
 Les éléments dans un `ItemGroup` d’une cible peut contenir le `Remove` attribut, ce qui supprime des éléments (fichiers) spécifiques du type d’élément. Cet attribut a été introduit dans le .NET Framework 3.5.  
  
 L’exemple suivant supprime chaque fichier .config du type d’élément de compilation.  
  
```  
<Target>  
    <ItemGroup>  
        <Compile Remove="*.config"/>  
    </ItemGroup>  
</Target>  
```  
  
###  <a name="a-namebkmkkeepmetadataa-keepmetadata-attribute"></a><a name="BKMK_KeepMetadata"></a> Attribut de KeepMetadata  
 Si un élément est généré au sein d’une cible, l’élément peut contenir les `KeepMetadata` attribut. Si cet attribut est spécifié, seules les métadonnées qui sont spécifiée dans la liste délimitée par des points-virgules des noms seront transférées de la source à l’élément cible. Une valeur vide pour cet attribut revient à ne pas le spécifier. Le `KeepMetadata` attribut a été introduit dans le .NET Framework 4.5.  
  
 L’exemple suivant illustre l’utilisation de la `KeepMetadata` attribut.  
  
```  
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
  
###  <a name="a-namebkmkremovemetadataa-removemetadata-attribute"></a><a name="BKMK_RemoveMetadata"></a> Attribut de RemoveMetadata  
 Si un élément est généré au sein d’une cible, l’élément peut contenir les `RemoveMetadata` attribut. Si cet attribut est spécifié, toutes les métadonnées sont transféré à partir de l’élément source à l’élément cible, à l’exception de métadonnées dont le nom figure dans la liste délimitée par des points-virgules des noms. Une valeur vide pour cet attribut revient à ne pas le spécifier. Le `RemoveMetadata` attribut a été introduit dans le .NET Framework 4.5.  
  
 L’exemple suivant illustre l’utilisation de la `RemoveMetadata` attribut.  
  
```  
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
  
###  <a name="a-namebkmkkeepduplicatesa-keepduplicates-attribute"></a><a name="BKMK_KeepDuplicates"></a> Attribut de KeepDuplicates  
 Si un élément est généré au sein d’une cible, l’élément peut contenir les `KeepDuplicates` attribut. `KeepDuplicates` est un `Boolean` attribut qui spécifie si un élément doit être ajouté au groupe cible si l’élément est une copie exacte d’un élément existant.  
  
 Si les éléments source et cible ont la même valeur Include mais des métadonnées différentes, l’élément est ajouté même si `KeepDuplicates` a la valeur `false`. Une valeur vide pour cet attribut revient à ne pas le spécifier. Le `KeepDuplicates` attribut a été introduit dans le .NET Framework 4.5.  
  
 L’exemple suivant illustre l’utilisation de la `KeepDuplicates` attribut.  
  
```  
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
 [MSBuild](../msbuild/msbuild1.md)   
 [Comment : sélectionner des fichiers pour la Build](../msbuild/how-to-select-the-files-to-build.md)   
 [Comment : exclure des fichiers de la Build](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Comment : afficher une liste d’éléments séparée par des virgules](../msbuild/how-to-display-an-item-list-separated-with-commas.md)   
 [Définitions d’éléments](../msbuild/item-definitions.md)   
 [Le traitement par lots](../msbuild/msbuild-batching.md)   
 [Item, élément (MSBuild)](../msbuild/item-element-msbuild.md)