---
title: 'Procédure pas à pas : utilisation de MSBuild | Microsoft Docs'
ms.date: 03/20/2019
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: b8a8b866-bb07-4abf-b9ec-0b40d281c310
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 310fa3b6795a5e340dcd9c7fa40cb27807c132ba
ms.sourcegitcommit: 0b8497b720eb06bed8ce2194731177161b65eb84
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82072539"
---
# <a name="walkthrough-use-msbuild"></a>Procédure pas à pas : utiliser MSBuild

MSBuild est la plateforme de génération pour Microsoft et Visual Studio. Cette procédure pas à pas vous présente les blocs de construction de MSBuild, et vous indique comment écrire, manipuler et déboguer des projets MSBuild. Vous allez découvrir comment :

- créer et manipuler un fichier projet ;

- utiliser des propriétés de génération ;

- utiliser des éléments de génération.

Vous pouvez exécuter MSBuild à partir de Visual Studio, ou à partir de la **fenêtre de commande**. Dans cette procédure pas à pas, vous créez un fichier projet MSBuild à l’aide de Visual Studio. Vous modifiez le fichier projet dans Visual Studio et utilisez la **fenêtre Commande** pour générer le projet et examiner les résultats.

## <a name="create-an-msbuild-project"></a>Création d’un projet MSBuild

 Le système de projet Visual Studio est basé sur MSBuild. La création d’un fichier projet à l’aide de Visual Studio est ainsi facilité. Dans cette section, vous créez un fichier projet Visual C#. Vous pouvez choisir de créer un fichier projet Visual Basic à la place. Dans le cadre de cette procédure pas à pas, la différence entre les deux fichiers projet est mineure.

**Pour créer un fichier projet**

1. Ouvrez Visual Studio et créez un projet.

    ::: moniker range=">=vs-2019"
    Appuyez sur **Échap** pour fermer la fenêtre de démarrage. Tapez **Ctrl+Q** pour ouvrir la zone de recherche, tapez **winforms**, puis choisissez **Créer une application Windows Forms (.NET Framework)**. Dans la boîte de dialogue qui apparaît, choisissez **Créer**.

    Dans le champ **Nom**, saisissez `BuildApp`. Entrez un **Emplacement** pour la solution, par exemple, *D :\\*. Acceptez les valeurs par défaut de **Solution**, **Nom de la solution** (**BuildApp**) et **Framework**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    De la barre de menu haut, choisissez **File** > **New** > **Project**. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, développez **Visual C#** > **Windows Desktop**, puis choisissez **Application Windows Forms (.NET Framework)**. Ensuite, choisissez **OK**.

    Dans le champ **Nom**, saisissez `BuildApp`. Entrez un **Emplacement** pour la solution, par exemple, *D :\\*. Acceptez les valeurs par défaut des options **Créer le répertoire pour la solution** (sélectionnée), **Ajouter au contrôle de code source** (non sélectionnée) et **Nom de la solution** (**BuildApp**).
    ::: moniker-end

1. Cliquez sur **OK** ou **Créer** pour créer le fichier projet.

## <a name="examine-the-project-file"></a>Examiner le fichier projet

 Dans la section précédente, vous avez utilisé Visual Studio pour créer un fichier projet Visual C#. Le fichier projet est représenté dans l’**Explorateur de solutions** par le nœud de projet nommé BuildApp. Vous pouvez examiner le fichier projet dans l’éditeur de code Visual Studio.

**Pour examiner le fichier projet**

1. Dans **Solution Explorer**, cliquez sur le nœud de projet **BuildApp**.

1. Dans le navigateur **Properties,** notez que la propriété **Project File** est *BuildApp.csproj*. Tous les fichiers de projet sont nommés avec le *proj*suffixe . Si vous aviez créé un projet Visual Basic, le nom du fichier du projet serait *BuildApp.vbproj*.

1. Cliquez avec le bouton droit sur le nœud de projet une nouvelle fois, puis cliquez sur **Modifier BuildApp.csproj**. 

     Le fichier projet s’affiche dans l’éditeur de code.

>[!NOTE]
> Pour certains types de projets, tels que le C, vous devez décharger le projet (cliquez à droite sur le fichier du projet et choisissez **le projet Deload)** avant de pouvoir ouvrir et modifier le fichier de projet.

## <a name="targets-and-tasks"></a>Cibles et tâches

Les fichiers projet sont des fichiers XML avec le nœud racine [Projet](../msbuild/project-element-msbuild.md).

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0"  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Les nouveaux projets .NET Core (style `Sdk` SDK) ont un attribut.

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

Si le projet n’est pas un projet de style SDK, vous devez spécifier l’espace de nom xmlns dans l’élément Projet. Si `ToolsVersion` est présent dans un nouveau projet, il doit s’agir de la version « 15.0 ».

Le processus de création d’une application est effectué avec les éléments [Target](../msbuild/target-element-msbuild.md) et [Task](../msbuild/task-element-msbuild.md).

- Une tâche est la plus petite unité de travail, en d’autres termes, « l’atome » d’une génération. Les tâches sont des composants exécutables indépendants qui peuvent compter des entrées et des sorties. Pour le moment, aucune tâche n’est référencée ni définie dans le fichier projet. Vous ajoutez des tâches au fichier projet dans les sections ci-dessous. Pour plus d’informations, consultez l’article [Tâches MSBuild](../msbuild/msbuild-tasks.md).

- Une cible est une séquence de tâches nommée. Pour plus d’informations, consultez l’article [Targets (Cibles MSBuild)](../msbuild/msbuild-targets.md).
- [Il peut s’agir d’une séquence de tâches nommée, mais de façon critique, elle représente quelque chose à construire ou à faire, de sorte qu’elle doit être définie d’une manière orientée vers les objectifs]

La cible par défaut n’est pas définie dans le fichier projet. Au lieu de cela, elle est spécifiée dans les projets importés. L’élément [Import](../msbuild/import-element-msbuild.md) spécifie les projets importés. Par exemple, dans un projet C#, la cible par défaut est importée à partir du fichier *Microsoft.CSharp.targets*.

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

Les fichiers importés sont insérés dans le fichier projet partout où ils sont référencés.

Dans les projcts de style SDK, vous ne voyez pas cet élément d’importation, puisque l’attribut SDK provoque l’importation implicite de ce fichier.

MSBuild effectue le suivi des cibles d’une génération et garantit que chaque cible est générée une seule fois.

## <a name="add-a-target-and-a-task"></a>Ajouter une cible et une tâche

 Ajoutez une cible au fichier projet. Ajoutez une tâche à la cible qui imprime un message.

**Pour ajouter une cible et une tâche**

1. Ajoutez ces lignes au fichier projet, juste après l’instruction Import :

    ```xml
    <Target Name="HelloWorld">
    </Target>
    ```

    Une cible nommée HelloWorld est alors créée. Notez qu’IntelliSense est activé quand vous modifiez le fichier projet.

2. Ajoutez des lignes à la cible HelloWorld afin que la section obtenue ressemble à ceci :

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Hello"></Message>  <Message Text="World"></Message>
    </Target>
    ```

3. Enregistrez le fichier projet.

La tâche Message est l’une des nombreuses tâches fournies avec MSBuild. Pour une liste complète des tâches disponibles et des informations d’utilisation, voir [référence De tâche](../msbuild/msbuild-task-reference.md).

La tâche Message prend la valeur de chaîne de l’attribut texte comme entrée et l’affiche sur le périphérique de sortie (ou l’écrit à un ou plusieurs journaux, le cas échéant). La cible HelloWorld exécute la tâche Message à deux reprises : tout d’abord pour afficher « Hello », puis pour afficher « World ».

## <a name="build-the-target"></a>Générer la cible

Si vous essayez de construire ce projet à partir de Visual Studio, il ne construira pas la cible que vous avez définie. C’est parce que Visual Studio choisit la cible par défaut, qui est toujours celle dans le fichier *.targets* importés.

Exécutez MSBuild à partir de **l’Invite de commandes développeur** pour Visual Studio pour générer la cible HelloWorld définie précédemment. Utilisez le commutateur de commande-cible ou -t pour sélectionner la cible.

> [!NOTE]
> Dans les sections ci-après, nous appellerons **l’Invite de commandes développeur****fenêtre Commande**.

**Pour construire la cible :**

1. Ouvrez la **fenêtre Commande**.

   (Windows 10) Dans la zone de recherche dans la barre des tâches, commencez à taper le nom de l’outil, tel que `dev` ou `developer command prompt`. S’affiche alors une liste des applications installées qui correspondent à votre modèle de recherche.

   Si vous avez besoin pour le trouver manuellement, le fichier est *LaunchDevCmd.bat* et se trouve dans le dossier *<dossier d’installation de Visual Studio\>\<version>\Common7\Tools*.

2. De la fenêtre de commande, naviguez vers le dossier contenant le fichier de projet, dans ce cas, *D: 'BuildApp’BuildApp*.

3. Exécuter msbuild avec `-t:HelloWorld`le commutateur de commande . Cette opération sélectionne et génère la cible HelloWorld :

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Examinez la sortie dans la **fenêtre Commande**. Vous devez voir les deux lignes « Hello » et « World » :

    ```output
    Hello
    World
    ```

> [!NOTE]
> Si vous voyez `The target "HelloWorld" does not exist in the project` à la place, vous avez probablement oublié d’enregistrer le fichier projet dans l’éditeur de code. Enregistrez le fichier et réessayez.

 En alternant entre l’éditeur de code et la fenêtre Commande, vous pouvez modifier le fichier projet et observer rapidement les résultats.

## <a name="build-properties"></a>Propriétés de la build

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

 Toutes les propriétés sont des éléments enfants des éléments PropertyGroup. Le nom de la propriété est le nom de l’élément enfant, et la valeur de la propriété est l’élément de texte de l’élément enfant. Par exemple,

```xml
<TargetFrameworkVersion>v4.5</TargetFrameworkVersion>
```

 définit la propriété nommée TargetFrameworkVersion, lui donnant la valeur de chaîne "v4.5".

 Les propriétés de génération peuvent être redéfinies à tout moment. Si

```xml
<TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
```

 apparaît plus loin dans le fichier projet ou dans un fichier importé ultérieurement dans le fichier projet, TargetFrameworkVersion prend la nouvelle valeur « v3.5 ».

## <a name="examine-a-property-value"></a>Examiner une valeur de propriété

 Pour obtenir la valeur d’une propriété, `PropertyName` utilisez la syntaxe suivante, où se trouve le nom de la propriété :

```xml
$(PropertyName)
```

Utilisez cette syntaxe pour examiner certaines propriétés du fichier projet.

**Pour examiner une valeur de propriété**

1. Dans l’éditeur de code, remplacez la cible HelloWorld par ce code :

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Configuration is $(Configuration)" />
      <Message Text="MSBuildToolsPath is $(MSBuildToolsPath)" />
    </Target>
    ```

1. Enregistrez le fichier projet.

1. Dans la **fenêtre Commande**, entrez et exécutez cette ligne :

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. Analyser la sortie. Vous devez observer ces deux lignes (votre version .NET Framework peut varier) :

    ::: moniker range=">=vs-2019"

    ```output
    Configuration is Debug
    MSBuildToolsPath is C:\Program Files (x86)\Microsoft Visual Studio\2019\<Visual Studio SKU>\MSBuild\15.0\Bin
    ```

    ::: moniker-end
    ::: moniker range="vs-2017"

    ```output
    Configuration is Debug
    MSBuildToolsPath is C:\Program Files (x86)\Microsoft Visual Studio\2017\<Visual Studio SKU>\MSBuild\15.0\Bin
    ```

    ::: moniker-end

### <a name="conditional-properties"></a>Propriétés conditionnelles

Beaucoup de `Configuration` propriétés comme sont définies conditionnellement, c’est-à-dire, l’attribut `Condition` apparaît dans l’élément de propriété. Les propriétés conditionnelles sont définies ou redéfinies uniquement si la condition a la valeur « true ». Notez que les propriétés non définies ont la valeur par défaut d’une chaîne vide. Par exemple,

```xml
<Configuration   Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

signifie « Si la propriété Configuration n’a pas encore été définie, définissez-la et attribuez-lui la valeur "Debug" ».

Pratiquement tous les éléments MSBuild peuvent posséder un attribut Condition. Pour en savoir plus sur l’utilisation de l’attribut Condition, consultez l’article [Conditions MSBuild](../msbuild/msbuild-conditions.md).

### <a name="reserved-properties"></a>Propriétés réservées

MSBuild réserve certains noms de propriété pour stocker des informations sur le fichier projet et les binaires de MSBuild. MSBuildToolsPath est un exemple de propriété réservée. Les propriétés réservées sont référencées avec la notation $ comme toute autre propriété. Pour plus d’informations, voir [Comment : Référencez le nom ou l’emplacement du dossier du projet](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) et des propriétés réservées et bien connues de [MSBuild.](../msbuild/msbuild-reserved-and-well-known-properties.md)

### <a name="environment-variables"></a>Variables d'environnement

Vous pouvez référencer des variables d’environnement dans les fichiers projet de la même façon que les propriétés de génération. Par exemple, pour utiliser la variable d’environnement PATH dans votre fichier projet, utilisez $(Path). Si le projet contient une définition de propriété qui porte le même nom qu’une variable d’environnement, la propriété du projet remplace la valeur de la variable d’environnement. Pour plus d’informations, voir [Comment : Utilisez les variables de l’environnement dans une build](../msbuild/how-to-use-environment-variables-in-a-build.md).

## <a name="set-properties-from-the-command-line"></a>Définir les propriétés à partir de la ligne de commande

Il est possible de définir des propriétés en ligne de commande à l’aide du commutateur de ligne de commande -property ou -p. Les valeurs de propriété reçues à partir de la ligne de commande remplacent celles qui sont définies dans les variables d’environnement et le fichier projet.

**Pour définir une valeur de propriété à partir de la ligne de commande :**

1. Dans la **fenêtre Commande**, entrez et exécutez cette ligne :

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld -p:Configuration=Release
    ```

1. Analyser la sortie. Vous devez normalement voir cette ligne :

    ```output
    Configuration is Release.
    ```

MSBuild crée la propriété Configuration et lui attribue la valeur « Release ».

## <a name="special-characters"></a>Caractères spéciaux

Certains caractères ont une signification spéciale dans les fichiers projet MSBuild. Il s’agit par exemple des points-virgules (;) et des astérisques (*). Pour utiliser ces caractères spéciaux en tant que littéraux dans un fichier projet, vous devez les spécifier à l’aide de la syntaxe %\<xx>, où \<xx> représente la valeur hexadécimale ASCII du caractère.

Modifiez la tâche Message pour afficher la valeur de la propriété Configuration avec des caractères spéciaux afin de la rendre plus lisible.

**Pour utiliser des caractères spéciaux dans la tâche Message :**

1. Dans l’éditeur de code, remplacez les deux tâches Message par cette ligne :

    ```xml
    <Message Text="%24(Configuration) is %22$(Configuration)%22" />
    ```

1. Enregistrez le fichier projet.

1. Dans la **fenêtre Commande**, entrez et exécutez cette ligne :

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. Analyser la sortie. Vous devez normalement voir cette ligne :

    ```output
    $(Configuration) is "Debug"
    ```

Pour plus d’informations, voir [MSBuild caractères spéciaux](../msbuild/msbuild-special-characters.md).

## <a name="build-items"></a>Générer des éléments

Un élément est une information, généralement un nom de fichier, qui est utilisée comme entrée dans le système de génération. Par exemple, une collection d’éléments représentant des fichiers sources peut être transmise à une tâche nommée Compile pour les compiler dans un assembly.

Tous les éléments sont des éléments enfants des éléments ItemGroup. Le nom de l’élément est le nom de l’élément enfant, et la valeur de l’élément est la valeur de l’attribut Include de l’élément enfant. Les valeurs des éléments du même nom sont collectées dans les types d’élément de ce nom.  Par exemple,

```xml
<ItemGroup>
    <Compile Include="Program.cs" />
    <Compile Include="Properties\AssemblyInfo.cs" />
</ItemGroup>
```

définit un groupe de deux éléments. Le type d’élément Compile a deux valeurs: *Program.cs* et *Properties-AssemblyInfo.cs*.

Le code suivant crée le même type d’élément en déclarant les deux fichiers dans un attribut Include, séparés par un point-virgule.

```xml
<ItemGroup>
    <Compile Include="Program.cs;Properties\AssemblyInfo.cs" />
</ItemGroup>
```

Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).

> [!NOTE]
> Les trajectoires de fichiers sont relatives au dossier contenant le fichier du projet MSBuild, même si le fichier de projet est un fichier de projet importé. Il y a quelques exceptions à cela, comme lors de l’utilisation [d’éléments Import](import-element-msbuild.md) and [UsingTask.](usingtask-element-msbuild.md)

## <a name="examine-item-type-values"></a>Examiner des valeurs de type d’élément

 Pour obtenir les valeurs d’un type d’élément, utilisez la syntaxe suivante, où ItemType est le nom du type d’élément :

```xml
@(ItemType)
```

Utilisez cette syntaxe pour examiner le type d’élément Compile dans le fichier projet.

**Pour examiner les valeurs de type d’élément :**

1. Dans l’éditeur de code, remplacez la tâche cible HelloWorld par ce code :

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Compile item type contains @(Compile)" />
    </Target>
    ```

1. Enregistrez le fichier projet.

1. Dans la **fenêtre Commande**, entrez et exécutez cette ligne :

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. Analyser la sortie. Vous devez normalement observer cette longue ligne :

    ```
    Compile item type contains Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
    ```

Par défaut, les valeurs d’un type d’élément sont séparées par des points-virgules.

Pour changer le séparateur d’un type d’élément, utilisez la syntaxe suivante, où ItemType est le type d’élément, et Separator une chaîne d’un ou de plusieurs caractères de séparation :

```xml
@(ItemType, Separator)
```

Modifiez la tâche Message afin d’utiliser des retours chariot et des sauts de ligne (%0A%0D) pour afficher un élément Compile par ligne.

**Pour afficher une valeur de type d’élément par ligne**

1. Dans l’éditeur de code, remplacez la tâche Message par cette ligne :

    ```xml
    <Message Text="Compile item type contains @(Compile, '%0A%0D')" />
    ```

2. Enregistrez le fichier projet.

3. Dans la **fenêtre Commande**, entrez et exécutez cette ligne :

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Analyser la sortie. Vous devez normalement voir ces lignes :

    ```
    Compile item type contains Form1.cs
    Form1.Designer.cs
    Program.cs
    Properties\AssemblyInfo.cs
    Properties\Resources.Designer.cs
    Properties\Settings.Designer.cs
    ```

### <a name="include-exclude-and-wildcards"></a>Caractères génériques et attributs Include et Exclude

 Vous pouvez utiliser les caractères génériques « * », « \*\* » et « ? » avec l’attribut Include pour ajouter des éléments à un type d’élément. Par exemple,

```xml
<Photos Include="images\*.jpeg" />
```

 ajoute tous les fichiers avec l’extension de fichier *.jpeg* dans le dossier *d’images* au type d’élément Photos, tandis que

```xml
<Photos Include="images\**\*.jpeg" />
```

 ajoute tous les fichiers avec l’extension de fichier *.jpeg* dans le dossier *d’images,* et tous ses sous-plieurs, au type d’élément Photos. Pour plus d’exemples, voir [Comment : Sélectionnez les fichiers à construire.](../msbuild/how-to-select-the-files-to-build.md)

 Notez que les éléments sont ajoutés au type d’élément à mesure qu’ils sont déclarés. Par exemple,

```xml
<Photos Include="images\*.jpeg" />
<Photos Include="images\*.gif" />
```

 crée un type d’élément nommé Photo qui contient tous les fichiers du dossier *images* avec une extension de fichier *.jpeg* ou *.gif*. Cet exemple est équivalent à celui de la ligne suivante :

```xml
<Photos Include="images\*.jpeg;images\*.gif" />
```

 Vous pouvez exclure un élément d’un type d’élément avec l’attribut Exclude. Par exemple,

```xml
<Compile Include="*.cs" Exclude="*Designer*">
```

 ajoute tous les fichiers portant l’extension de fichier  *.cs* au type d’élément Compile, à l’exception des fichiers dont les noms contiennent la chaîne *Designer*. Pour plus d’exemples, voir [Comment : Exclure les fichiers de la version](../msbuild/how-to-exclude-files-from-the-build.md).

L’attribut Exclude affecte uniquement les éléments ajoutés par l’attribut Include dans l’élément Item qui les contient. Par exemple,

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

n’exclurait pas le fichier *Form1.cs*, qui a été ajouté dans l’élément précédent.

**Pour inclure et exclure des éléments**

1. Dans l’éditeur de code, remplacez la tâche Message par cette ligne :

    ```xml
    <Message Text="XFiles item type contains @(XFiles)" />
    ```

2. Ajoutez ce groupe d’éléments juste après l’élément Import :

    ```xml
    <ItemGroup>
       <XFiles Include="*.cs;properties/*.resx" Exclude="*Designer*" />
    </ItemGroup>
    ```

3. Enregistrez le fichier projet.

4. Dans la **fenêtre Commande**, entrez et exécutez cette ligne :

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

5. Analyser la sortie. Vous devez normalement voir cette ligne :

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

```xml
%(ItemType.MetaDataName)
```

**Pour examiner les métadonnées de l’article :**

1. Dans l’éditeur de code, remplacez la tâche Message par cette ligne :

    ```xml
    <Message Text="Compile.DependentUpon: %(Compile.DependentUpon)" />
    ```

2. Enregistrez le fichier projet.

3. Dans la **fenêtre Commande**, entrez et exécutez cette ligne :

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Analyser la sortie. Vous devez normalement voir ces lignes :

    ```output
    Compile.DependentUpon:
    Compile.DependentUpon: Form1.cs
    Compile.DependentUpon: Resources.resx
    Compile.DependentUpon: Settings.settings
    ```

Notez que l’expression « Compile.DependentUpon » apparaît plusieurs fois. L’utilisation de métadonnées avec cette syntaxe dans une cible provoque le « traitement par lot ». Cela signifie que les tâches de la cible sont exécutées une fois pour chaque valeur de métadonnée unique. Ce script MSBuild revient à utiliser la construction de programmation courante « for loop ». Pour plus d’informations, consultez l’article [Batching (Traitement par lot MSBuild)](../msbuild/msbuild-batching.md).

### <a name="well-known-metadata"></a>Métadonnées connues

 Chaque fois qu’un élément est ajouté à une liste d’éléments, il reçoit des métadonnées connues. Par exemple, %(Filename) retourne le nom de fichier de n’importe quel élément. Pour une liste complète de métadonnées bien connues, voir [métadonnées d’objets bien connus](../msbuild/msbuild-well-known-item-metadata.md).

**Pour examiner les métadonnées bien connues :**

1. Dans l’éditeur de code, remplacez la tâche Message par cette ligne :

    ```xml
    <Message Text="Compile Filename: %(Compile.Filename)" />
    ```

2. Enregistrez le fichier projet.

3. Dans la **fenêtre Commande**, entrez et exécutez cette ligne :

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Analyser la sortie. Vous devez normalement voir ces lignes :

    ```output
    Compile Filename: Form1
    Compile Filename: Form1.Designer
    Compile Filename: Program
    Compile Filename: AssemblyInfo
    Compile Filename: Resources.Designer
    Compile Filename: Settings.Designer
    ```

En comparant les deux exemples ci-dessus, vous pouvez constater que si tous les éléments du type d’élément Compile ne disposent pas de la métadonnée DependentUpon, tous possèdent la métadonnée Filename connue.

### <a name="metadata-transformations"></a>Transformations de métadonnées

 Les listes d’éléments peuvent être transformées en nouvelles listes d’éléments. Pour transformer une liste d’éléments, utilisez la syntaxe suivante, où \< ItemType est le nom du type d’élément et \< MetaDataName le nom des métadonnées :

```xml
@(ItemType -> '%(MetadataName)')
```

Par exemple, une liste d’éléments de fichiers sources peut être transformée en une collection de fichiers objets à l’aide d’une expression comme `@(SourceFiles -> '%(Filename).obj')`. Pour plus d’informations, consultez l’article [Transforms (Transformations MSBuild)](../msbuild/msbuild-transforms.md).

**Pour transformer les éléments à l’aide de métadonnées :**

1. Dans l’éditeur de code, remplacez la tâche Message par cette ligne :

    ```xml
    <Message Text="Backup files: @(Compile->'%(filename).bak')" />
    ```

2. Enregistrez le fichier projet.

3. Dans la **fenêtre Commande**, entrez et exécutez cette ligne :

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Analyser la sortie. Vous devez normalement voir cette ligne :

    ```output
    Backup files: Form1.bak;Form1.Designer.bak;Program.bak;AssemblyInfo.bak;Resources.Designer.bak;Settings.Designer.bak
    ```

Notez que les métadonnées exprimées dans cette syntaxe ne provoquent pas le traitement par lot.

## <a name="next-steps"></a>Étapes suivantes

 Pour apprendre à créer un simple fichier de projet une étape à la fois, essayez le [Walkthrough: Création d’un fichier de projet MSBuild](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)à partir de zéro .

## <a name="see-also"></a>Voir aussi

- [Aperçu MSBuild](../msbuild/msbuild.md)
- [Référence MSBuild](../msbuild/msbuild-reference.md)
