---
title: "Procédure pas à pas : utilisation de MSBuild | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MSBuild, tutorial
ms.assetid: b8a8b866-bb07-4abf-b9ec-0b40d281c310
caps.latest.revision: "32"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 9500cdb26b51d3a91b9565c7ef0353907e9afe7c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-using-msbuild"></a>Procédures pas à pas : utilisation de MSBuild
MSBuild est la plateforme de génération pour Microsoft et Visual Studio. Cette procédure pas à pas vous présente les blocs de construction de MSBuild, et vous indique comment écrire, manipuler et déboguer des projets MSBuild. Vous allez découvrir comment :  
  
-   créer et manipuler un fichier projet ;  
  
-   utiliser des propriétés de génération ;  
  
-   utiliser des éléments de génération.  
  
 Vous pouvez exécuter MSBuild à partir de Visual Studio ou à partir de la fenêtre Commande. Dans cette procédure pas à pas, vous créez un fichier projet MSBuild à l’aide de Visual Studio. Vous modifiez le fichier projet dans Visual Studio et utilisez une fenêtre Commande pour générer le projet et examiner les résultats.  
  
## <a name="creating-an-msbuild-project"></a>Création d’un projet MSBuild  
 Le système de projet Visual Studio est basé sur MSBuild. La création d’un fichier projet à l’aide de Visual Studio est ainsi facilité. Dans cette section, vous créez un fichier projet Visual C#. Vous pouvez choisir de créer un fichier projet Visual Basic à la place. Dans le cadre de cette procédure pas à pas, la différence entre les deux fichiers projet est mineure.  
  
#### <a name="to-create-a-project-file"></a>Pour créer un fichier projet  
  
1.  Ouvrez Visual Studio.  
  
2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans la boîte de dialogue **Nouveau projet**, sélectionnez le type de projet Visual C#, puis le modèle **Application Windows Forms**. Dans la zone **Nom**, tapez `BuildApp`. Entrez un **Emplacement** pour la solution, par exemple, `D:\`. Acceptez les valeurs par défaut des options **Créer le répertoire pour la solution** (sélectionnée), **Ajouter au contrôle de code source** (non sélectionnée) et **Nom de la solution** (`BuildApp`).  
  
     Cliquez sur **OK** pour créer le fichier projet.  
  
## <a name="examining-the-project-file"></a>Examen du fichier projet  
 Dans la section précédente, vous avez utilisé Visual Studio pour créer un fichier projet Visual C#. Le fichier projet est représenté dans l’**Explorateur de solutions** par le nœud de projet nommé BuildApp. Vous pouvez examiner le fichier projet dans l’éditeur de code Visual Studio.  
  
#### <a name="to-examine-the-project-file"></a>Pour examiner le fichier projet  
  
1.  Dans l’**Explorateur de solutions**, cliquez sur le nœud de projet BuildApp.  
  
2.  Dans l’**Explorateur de propriétés**, notez que la propriété **Fichier projet** s’appelle BuildApp.csproj. Tous les fichiers projet sont nommés avec le suffixe « proj ». Si vous aviez créé un projet Visual Basic, le nom du fichier projet aurait été BuildApp.vbproj.  
  
3.  Cliquez avec le bouton droit sur le nœud de projet, puis cliquez sur **Décharger le projet**.  
  
4.  Cliquez avec le bouton droit sur le nœud de projet une nouvelle fois, puis cliquez sur **Modifier BuildApp.csproj**.  
  
     Le fichier projet s’affiche dans l’éditeur de code.  
  
## <a name="targets-and-tasks"></a>Cibles et tâches  
 Les fichiers projet sont des fichiers XML avec le nœud racine [Projet](../msbuild/project-element-msbuild.md).  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Project ToolsVersion="12.0" DefaultTargets="Build"  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 Vous devez spécifier l’espace de noms xmlns dans l’élément Project.  
  
 Le processus de création d’une application est effectué avec les éléments [Target](../msbuild/target-element-msbuild.md) et [Task](../msbuild/task-element-msbuild.md).  
  
-   Une tâche est la plus petite unité de travail, en d’autres termes, « l’atome » d’une génération. Les tâches sont des composants exécutables indépendants qui peuvent compter des entrées et des sorties. Pour le moment, aucune tâche n’est référencée ni définie dans le fichier projet. Vous ajoutez des tâches au fichier projet dans les sections ci-dessous. Pour plus d’informations, consultez l’article [Tâches MSBuild](../msbuild/msbuild-tasks.md).  
  
-   Une cible est une séquence de tâches nommée. Pour l’instant, deux cibles indiquées à la fin du fichier projet sont comprises dans les commentaires HTML : BeforeBuild et AfterBuild.  
  
    ```xml  
    <Target Name="BeforeBuild">  
    </Target>  
    <Target Name="AfterBuild">  
    </Target>  
    ```  
  
     Pour plus d’informations, consultez l’article [Targets (Cibles MSBuild)](../msbuild/msbuild-targets.md).  
  
 Le nœud Projet possède un attribut DefaultTargets facultatif qui sélectionne la cible par défaut à générer, dans ce cas Build.  
  
```xml  
<Project ToolsVersion="12.0" DefaultTargets="Build" ...  
```  
  
 La cible Build n’est pas définie dans le fichier projet. Elle est importée à partir du fichier Microsoft.CSharp.targets à l’aide de l’élément [Import](../msbuild/import-element-msbuild.md).  
  
```xml  
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
```  
  
 Les fichiers importés sont insérés dans le fichier projet partout où ils sont référencés.  
  
 MSBuild effectue le suivi des cibles d’une génération et garantit que chaque cible est générée une seule fois.  
  
## <a name="adding-a-target-and-a-task"></a>Ajout d’une cible et d’une tâche  
 Ajoutez une cible au fichier projet. Ajoutez une tâche à la cible qui imprime un message.  
  
#### <a name="to-add-a-target-and-a-task"></a>Pour ajouter une cible et une tâche  
  
1.  Ajoutez ces lignes au fichier projet, juste après l’instruction Import :  
  
    ```xml  
    <Target Name="HelloWorld">  
    </Target>  
    ```  
  
     Une cible nommée HelloWorld est alors créée. Notez la prise en charge Intellisense lorsque vous modifiez le fichier projet.  
  
2.  Ajoutez des lignes à la cible HelloWorld afin que la section obtenue ressemble à ceci :  
  
    ```xml  
    <Target Name="HelloWorld">  
      <Message Text="Hello"></Message>  <Message Text="World"></Message>  
    </Target>  
    ```  
  
3.  Enregistrez le fichier projet.  
  
 La tâche Message est l’une des nombreuses tâches fournies avec MSBuild. Pour obtenir la liste complète des tâches disponibles et les informations sur leur utilisation, consultez l’article [Informations de référence sur les tâches MSBuild](../msbuild/msbuild-task-reference.md).  
  
 La tâche Message prend la valeur de chaîne de l’attribut Text en tant qu’entrée et l’affiche sur le périphérique de sortie. La cible HelloWorld exécute la tâche Message à deux reprises : tout d’abord pour afficher « Hello », puis pour afficher « World ».  
  
## <a name="building-the-target"></a>Génération de la cible  
 Exécutez MSBuild à partir de l’**Invite de commandes de Visual Studio** pour générer la cible HelloWorld définie précédemment. Utilisez le commutateur de ligne de commande /target ou /t pour sélectionner la cible.  
  
> [!NOTE]
>  Dans les sections ci-après, nous appellerons l’**Invite de commandes de Visual Studio** **fenêtre Commande**.  
  
#### <a name="to-build-the-target"></a>Pour générer la cible  
  
1.  Cliquez sur **Démarrer**, puis sur **Tous les programmes**. Recherchez l’**Invite de commandes de Visual Studio** et cliquez dessus dans le dossier **Visual Studio Tools**.  
  
2.  Dans la fenêtre Commande, accédez au dossier contenant le fichier projet, dans ce cas, D:\BuildApp\BuildApp.  
  
3.  Exécutez msbuild avec le commutateur de commande /t:HelloWorld. Cette opération sélectionne et génère la cible HelloWorld :  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Examinez la sortie dans la **fenêtre Commande**. Vous devez voir les deux lignes « Hello » et « World » :  
  
    ```  
    Hello  
    World  
    ```  
  
> [!NOTE]
>  Si vous voyez `The target "HelloWorld" does not exist in the project` à la place, vous avez probablement oublié d’enregistrer le fichier projet dans l’éditeur de code. Enregistrez le fichier et réessayez.  
  
 En alternant entre l’éditeur de code et la fenêtre Commande, vous pouvez modifier le fichier projet et observer rapidement les résultats.  
  
> [!NOTE]
>  Si vous exécutez msbuild sans le commutateur de commande /t, msbuild génère la cible fournie par l’attribut DefaultTarget de l’élément Project, dans ce cas « Build ». Cette opération génère l’application Windows Forms BuildApp.exe.  
  
## <a name="build-properties"></a>Propriétés de build  
 Les propriétés de génération sont des paires nom-valeur qui guident la génération. Plusieurs propriétés de génération sont déjà définies en haut du fichier projet :  
  
```xml  
<PropertyGroup>  
...  
  <ProductVersion>10.0.11107</ProductVersion>  
  <SchemaVersion>2.0</SchemaVersion>  
  <ProjectGuid>{30E3C9D5-FD86-4691-A331-80EA5BA7E571}</ProjectGuid>  
  <OutputType>WinExe</OutputType>  
...  
</PropertyGroup>  
```  
  
 Toutes les propriétés sont des éléments enfants des éléments PropertyGroup. Le nom de la propriété est le nom de l’élément enfant, et la valeur de la propriété est l’élément de texte de l’élément enfant. Par exemple :  
  
```xml  
<TargetFrameworkVersion>v12.0</TargetFrameworkVersion>  
```  
  
 définit la propriété nommée TargetFrameworkVersion, en lui attribuant la valeur de chaîne « v12.0 ».  
  
 Les propriétés de génération peuvent être redéfinies à tout moment. If  
  
```xml  
<TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
```  
  
 apparaît plus loin dans le fichier projet ou dans un fichier importé ultérieurement dans le fichier projet, TargetFrameworkVersion prend la nouvelle valeur « v3.5 ».  
  
## <a name="examining-a-property-value"></a>Examen d’une valeur de propriété  
 Pour obtenir la valeur d’une propriété, utilisez la syntaxe suivante, où PropertyName est le nom de la propriété :  
  
```  
$(PropertyName)  
```  
  
 Utilisez cette syntaxe pour examiner certaines propriétés du fichier projet.  
  
#### <a name="to-examine-a-property-value"></a>Pour examiner une valeur de propriété  
  
1.  Dans l’éditeur de code, remplacez la cible HelloWorld par ce code :  
  
    ```xml  
    <Target Name="HelloWorld">  
      <Message Text="Configuration is $(Configuration)" />  
      <Message Text="MSBuildToolsPath is $(MSBuildToolsPath)" />  
    </Target>  
    ```  
  
2.  Enregistrez le fichier projet.  
  
3.  Dans la **fenêtre Commande**, entrez et exécutez cette ligne :  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Examinez le résultat. Vous devez observer ces deux lignes (votre version .NET Framework peut varier) :  
  
    ```  
    Configuration is Debug  
    MSBuildToolsPath is C:\Program Files\MSBuild\12.0\bin  
    ```  
  
> [!NOTE]
>  Si vous ne voyez pas ces lignes, vous avez probablement oublié d’enregistrer le fichier projet dans l’éditeur de code. Enregistrez le fichier et réessayez.  
  
### <a name="conditional-properties"></a>Propriétés conditionnelles  
 Plusieurs propriétés, comme la propriété Configuration, sont définies de manière conditionnelle, autrement dit, l’attribut Condition s’affiche dans l’élément de propriété. Les propriétés conditionnelles sont définies ou redéfinies uniquement si la condition a la valeur « true ». Notez que les propriétés non définies ont la valeur par défaut d’une chaîne vide. Par exemple :  
  
```xml  
<Configuration   Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
```  
  
 signifie « Si la propriété Configuration n’a pas encore été définie, définissez-la et attribuez-lui la valeur "Debug" ».  
  
 Pratiquement tous les éléments MSBuild peuvent posséder un attribut Condition. Pour en savoir plus sur l’utilisation de l’attribut Condition, consultez l’article [Conditions MSBuild](../msbuild/msbuild-conditions.md).  
  
### <a name="reserved-properties"></a>Propriétés réservées  
 MSBuild réserve certains noms de propriété pour stocker des informations sur le fichier projet et les binaires de MSBuild. MSBuildToolsPath est un exemple de propriété réservée. Les propriétés réservées sont référencées avec la notation $ comme toute autre propriété. Pour plus d’informations, consultez les articles [Comment : référencer le nom ou l’emplacement du fichier projet](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) et [Propriétés réservées et connues de MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
### <a name="environment-variables"></a>Environment Variables  
 Vous pouvez référencer des variables d’environnement dans les fichiers projet de la même façon que les propriétés de génération. Par exemple, pour utiliser la variable d’environnement PATH dans votre fichier projet, utilisez $(Path). Si le projet contient une définition de propriété qui porte le même nom qu’une variable d’environnement, la propriété du projet remplace la valeur de la variable d’environnement. Pour plus d’informations, consultez l’article [Comment : utiliser des variables d’environnement dans une génération](../msbuild/how-to-use-environment-variables-in-a-build.md).  
  
## <a name="setting-properties-from-the-command-line"></a>Définition des propriétés à partir de la ligne de commande  
 Des propriétés peuvent être définies sur la ligne de commande à l’aide du commutateur de ligne de commande /property ou /p. Les valeurs de propriété reçues à partir de la ligne de commande remplacent celles qui sont définies dans les variables d’environnement et le fichier projet.  
  
#### <a name="to-set-a-property-value-from-the-command-line"></a>Pour définir une valeur de propriété dans la ligne de commande  
  
1.  Dans la **fenêtre Commande**, entrez et exécutez cette ligne :  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld /p:Configuration=Release  
    ```  
  
2.  Examinez le résultat. Vous devez normalement voir cette ligne :  
  
    ```  
    Configuration is Release.  
    ```  
  
 MSBuild crée la propriété Configuration et lui attribue la valeur « Release ».  
  
## <a name="special-characters"></a>Caractères spéciaux  
 Certains caractères ont une signification spéciale dans les fichiers projet MSBuild. Il s’agit par exemple des points-virgules (;) et des astérisques (*). Pour utiliser ces caractères spéciaux en tant que littéraux dans un fichier projet, vous devez les spécifier à l’aide de la syntaxe %xx, où xx représente la valeur hexadécimale ASCII du caractère.  
  
 Modifiez la tâche Message pour afficher la valeur de la propriété Configuration avec des caractères spéciaux afin de la rendre plus lisible.  
  
#### <a name="to-use-special-characters-in-the-message-task"></a>Pour utiliser des caractères spéciaux dans la tâche Message  
  
1.  Dans l’éditeur de code, remplacez les deux tâches Message par cette ligne :  
  
    ```xml  
    <Message Text="%24(Configuration) is %22$(Configuration)%22" />  
    ```  
  
2.  Enregistrez le fichier projet.  
  
3.  Dans la **fenêtre Commande**, entrez et exécutez cette ligne :  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Examinez le résultat. Vous devez normalement voir cette ligne :  
  
    ```  
    $(Configuration) is "Debug"  
    ```  
  
 Pour plus d’informations, consultez l’article [MSBuild Special Characters (Caractères spéciaux MSBuild)](../msbuild/msbuild-special-characters.md).  
  
## <a name="build-items"></a>Éléments de génération  
 Un élément est une information, généralement un nom de fichier, qui est utilisée comme entrée dans le système de génération. Par exemple, une collection d’éléments représentant des fichiers sources peut être transmise à une tâche nommée Compile pour les compiler dans un assembly.  
  
 Tous les éléments sont des éléments enfants des éléments ItemGroup. Le nom de l’élément est le nom de l’élément enfant, et la valeur de l’élément est la valeur de l’attribut Include de l’élément enfant. Les valeurs des éléments du même nom sont collectées dans les types d’élément de ce nom.  Par exemple :  
  
```xml  
<ItemGroup>  
    <Compile Include="Program.cs" />  
    <Compile Include="Properties\AssemblyInfo.cs" />  
</ItemGroup>  
```  
  
 définit un groupe de deux éléments. Le type d’élément Compile possède deux valeurs : « Program.cs » et « Properties\AssemblyInfo.cs ».  
  
 Le code suivant crée le même type d’élément en déclarant les deux fichiers dans un attribut Include, séparés par un point-virgule.  
  
```xml  
<ItemGroup>  
    <Compile Include="Program.cs;Properties\AssemblyInfo.cs" />  
</ItemGroup>  
```  
  
 Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).  
  
> [!NOTE]
>  Les chemins d’accès aux fichiers sont relatifs au dossier contenant le fichier projet MSBuild.  
  
## <a name="examining-item-type-values"></a>Examen des valeurs des types d’élément  
 Pour obtenir les valeurs d’un type d’élément, utilisez la syntaxe suivante, où ItemType est le nom du type d’élément :  
  
```  
@(ItemType)  
```  
  
 Utilisez cette syntaxe pour examiner le type d’élément Compile dans le fichier projet.  
  
#### <a name="to-examine-item-type-values"></a>Pour examiner des valeurs de types d’élément  
  
1.  Dans l’éditeur de code, remplacez la tâche cible HelloWorld par ce code :  
  
    ```xml  
    <Target Name="HelloWorld">  
      <Message Text="Compile item type contains @(Compile)" />  
    </Target>  
    ```  
  
2.  Enregistrez le fichier projet.  
  
3.  Dans la **fenêtre Commande**, entrez et exécutez cette ligne :  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Examinez le résultat. Vous devez normalement observer cette longue ligne :  
  
    ```  
    Compile item type contains Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs  
    ```  
  
 Par défaut, les valeurs d’un type d’élément sont séparées par des points-virgules.  
  
 Pour changer le séparateur d’un type d’élément, utilisez la syntaxe suivante, où ItemType est le type d’élément, et Separator une chaîne d’un ou de plusieurs caractères de séparation :  
  
```  
@(ItemType, Separator)  
```  
  
 Modifiez la tâche Message afin d’utiliser des retours chariot et des sauts de ligne (%0A%0D) pour afficher un élément Compile par ligne.  
  
#### <a name="to-display-item-type-values-one-per-line"></a>Pour afficher une valeur de type d’élément par ligne  
  
1.  Dans l’éditeur de code, remplacez la tâche Message par cette ligne :  
  
    ```xml  
    <Message Text="Compile item type contains @(Compile, '%0A%0D')" />  
    ```  
  
2.  Enregistrez le fichier projet.  
  
3.  Dans la **fenêtre Commande**, entrez et exécutez cette ligne :  
  
     `msbuild buildapp.csproj /t:HelloWorld`  
  
4.  Examinez le résultat. Vous devez normalement voir ces lignes :  
  
    ```  
    Compile item type contains Form1.cs  
    Form1.Designer.cs  
    Program.cs  
    Properties\AssemblyInfo.cs  
    Properties\Resources.Designer.cs  
    Properties\Settings.Designer.cs  
    ```  
  
### <a name="include-exclude-and-wildcards"></a>Caractères génériques et attributs Include et Exclude  
 Vous pouvez utiliser les caractères génériques « * », « \*\* » et « ? » avec l’attribut Include pour ajouter des éléments à un type d’élément. Par exemple :  
  
```xml  
<Photos Include="images\*.jpeg" />  
```  
  
 ajoute tous les fichiers pourvus de l’extension de fichier « .jpeg » du dossier images au type d’élément Photos, alors que  
  
```xml  
<Photos Include="images\**.jpeg" />  
```  
  
 ajoute tous les fichiers pourvus de l’extension de fichier « .jpeg » du dossier images et de l’ensemble de ses sous-dossiers, au type d’élément Photos. Pour plus d’exemples, consultez l’article [How to: Select the Files to Build (Comment : sélectionner les fichiers pour une génération)](../msbuild/how-to-select-the-files-to-build.md).  
  
 Notez que les éléments sont ajoutés au type d’élément à mesure qu’ils sont déclarés. Par exemple :  
  
```xml  
<Photos Include="images\*.jpeg" />  
<Photos Include="images\*.gif" />  
```  
  
 crée un type d’élément nommé Photo qui contient tous les fichiers du dossier images pourvus d’une extension de fichier « .jpeg » ou « .gif ». Cet exemple est équivalent à celui de la ligne suivante :  
  
```xml  
<Photos Include="images\*.jpeg;images\*.gif" />  
```  
  
 Vous pouvez exclure un élément d’un type d’élément avec l’attribut Exclude. Par exemple :  
  
```xml  
<Compile Include="*.cs" Exclude="*Designer*">  
```  
  
 ajoute tous les fichiers portant l’extension de fichier « .cs » au type d’élément Compile, à l’exception des fichiers dont les noms contiennent la chaîne « Designer ». Pour plus d’exemples, consultez l’article [Comment : exclure des fichiers de la build](../msbuild/how-to-exclude-files-from-the-build.md).  
  
 L’attribut Exclude affecte uniquement les éléments ajoutés par l’attribut Include dans l’élément Item qui les contient. Par exemple :  
  
```xml  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 n’exclut pas le fichier Form1.cs, qui a été ajouté dans l’élément Item précédent.  
  
##### <a name="to-include-and-exclude-items"></a>Pour inclure et exclure des éléments  
  
1.  Dans l’éditeur de code, remplacez la tâche Message par cette ligne :  
  
    ```xml  
    <Message Text="XFiles item type contains @(XFiles)" />  
    ```  
  
2.  Ajoutez ce groupe d’éléments juste après l’élément Import :  
  
    ```xml  
    <ItemGroup>  
       <XFiles Include="*.cs;properties/*.resx" Exclude="*Designer*" />  
    </ItemGroup>  
    ```  
  
3.  Enregistrez le fichier projet.  
  
4.  Dans la **fenêtre Commande**, entrez et exécutez cette ligne :  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
5.  Examinez le résultat. Vous devez normalement voir cette ligne :  
  
    ```  
    XFiles item type contains Form1.cs;Program.cs;Properties/Resources.resx  
    ```  
  
## <a name="item-metadata"></a>Métadonnées d’élément  
 Outre les informations collectées à partir des attributs Include et Exclude, les éléments peuvent contenir des métadonnées. Ces métadonnées peuvent être utilisées par les tâches qui requièrent plus d’informations sur les éléments que leur seule valeur.  
  
 Les métadonnées d’élément sont déclarées dans le fichier projet en créant un élément avec le nom des métadonnées comme élément enfant de l’élément. Un élément peut comporter zéro ou plusieurs valeurs de métadonnées. Par exemple, l’élément CSFile suivant contient les métadonnées Culture de valeur « Fr » :  
  
```xml  
<ItemGroup>  
    <CSFile Include="main.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 Pour obtenir la valeur des métadonnées d’un type d’élément, utilisez la syntaxe suivante, où ItemType est le nom du type d’élément et MetaDataName le nom des métadonnées :  
  
```  
%(ItemType.MetaDataName)  
```  
  
#### <a name="to-examine-item-metadata"></a>Pour examiner des métadonnées d’élément  
  
1.  Dans l’éditeur de code, remplacez la tâche Message par cette ligne :  
  
    ```xml  
    <Message Text="Compile.DependentUpon: %(Compile.DependentUpon)" />  
    ```  
  
2.  Enregistrez le fichier projet.  
  
3.  Dans la **fenêtre Commande**, entrez et exécutez cette ligne :  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Examinez le résultat. Vous devez normalement voir ces lignes :  
  
    ```  
    Compile.DependentUpon:  
    Compile.DependentUpon: Form1.cs  
    Compile.DependentUpon: Resources.resx  
    Compile.DependentUpon: Settings.settings  
    ```  
  
 Notez que l’expression « Compile.DependentUpon » apparaît plusieurs fois. L’utilisation de métadonnées avec cette syntaxe dans une cible provoque le « traitement par lot ». Cela signifie que les tâches de la cible sont exécutées une fois pour chaque valeur de métadonnée unique. Ce script MSBuild revient à utiliser la construction de programmation courante « for loop ». Pour plus d’informations, consultez l’article [Batching (Traitement par lot MSBuild)](../msbuild/msbuild-batching.md).  
  
### <a name="well-known-metadata"></a>Métadonnées connues  
 Chaque fois qu’un élément est ajouté à une liste d’éléments, il reçoit des métadonnées connues. Par exemple, %(Filename) retourne le nom de fichier de n’importe quel élément. Pour obtenir la liste complète des métadonnées connues, consultez l’article [Well-known Item Metadata (Métadonnées connues d’éléments MSBuild)](../msbuild/msbuild-well-known-item-metadata.md).  
  
##### <a name="to-examine-well-known-metadata"></a>Pour examiner des métadonnées connues  
  
1.  Dans l’éditeur de code, remplacez la tâche Message par cette ligne :  
  
    ```xml  
    <Message Text="Compile Filename: %(Compile.Filename)" />  
    ```  
  
2.  Enregistrez le fichier projet.  
  
3.  Dans la **fenêtre Commande**, entrez et exécutez cette ligne :  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Examinez le résultat. Vous devez normalement voir ces lignes :  
  
    ```  
    Compile Filename: Form1  
    Compile Filename: Form1.Designer  
    Compile Filename: Program  
    Compile Filename: AssemblyInfo  
    Compile Filename: Resources.Designer  
    Compile Filename: Settings.Designer  
    ```  
  
 En comparant les deux exemples ci-dessus, vous pouvez constater que si tous les éléments du type d’élément Compile ne disposent pas de la métadonnée DependentUpon, tous possèdent la métadonnée Filename connue.  
  
### <a name="metadata-transformations"></a>Transformations de métadonnées  
 Les listes d’éléments peuvent être transformées en nouvelles listes d’éléments. Pour transformer une liste d’éléments, utilisez la syntaxe suivante, où ItemType est le nom du type d’élément et MetaDataName le nom des métadonnées :  
  
```  
@(ItemType -> '%(MetadataName)')  
```  
  
 Par exemple, une liste d’éléments de fichiers sources peut être transformée en une collection de fichiers objets à l’aide d’une expression comme `@(SourceFiles -> '%(Filename).obj')`. Pour plus d’informations, consultez l’article [Transforms (Transformations MSBuild)](../msbuild/msbuild-transforms.md).  
  
##### <a name="to-transform-items-using-metadata"></a>Pour transformer des éléments à l’aide de métadonnées  
  
1.  Dans l’éditeur de code, remplacez la tâche Message par cette ligne :  
  
    ```xml  
    <Message Text="Backup files: @(Compile->'%(filename).bak')" />  
    ```  
  
2.  Enregistrez le fichier projet.  
  
3.  Dans la **fenêtre Commande**, entrez et exécutez cette ligne :  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Examinez le résultat. Vous devez normalement voir cette ligne :  
  
    ```  
    Backup files: Form1.bak;Form1.Designer.bak;Program.bak;AssemblyInfo.bak;Resources.Designer.bak;Settings.Designer.bak  
    ```  
  
 Notez que les métadonnées exprimées dans cette syntaxe ne provoquent pas le traitement par lot.  
  
## <a name="whats-next"></a>Quelle est la suite ?  
 Pour découvrir comment créer pas à pas un fichier projet simple, consultez la [Procédure pas à pas : création d’un fichier projet MSBuild à partir de zéro](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).  
  
## <a name="see-also"></a>Voir aussi
[MSBuild Overview (Vue d’ensemble de MSBuild)](../msbuild/msbuild.md)  
 [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)
