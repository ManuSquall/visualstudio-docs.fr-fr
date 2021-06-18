---
title: Utiliser MSBuild
description: Découvrez les différentes parties d’un fichier projet MSBuild, y compris les éléments, les métadonnées d’élément, les propriétés, les cibles et les tâches.
ms.date: 10/19/2020
ms.topic: conceptual
ms.custom: contperf-fy21q2
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: b8a8b866-bb07-4abf-b9ec-0b40d281c310
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e3a301c1bd4758ea08f49036fcf8756c8d7e7c26
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306447"
---
# <a name="walkthrough-use-msbuild"></a>Procédure pas à pas : utiliser MSBuild

MSBuild est la plateforme de génération pour Microsoft et Visual Studio. Cette procédure pas à pas vous présente les blocs de construction de MSBuild, et vous indique comment écrire, manipuler et déboguer des projets MSBuild. Vous allez découvrir comment :

- créer et manipuler un fichier projet ;

- utiliser des propriétés de génération ;

- utiliser des éléments de génération.

Vous pouvez exécuter MSBuild à partir de Visual Studio ou à partir de la **fenêtre commande**. Dans cette procédure pas à pas, vous créez un fichier projet MSBuild à l’aide de Visual Studio. Vous modifiez le fichier projet dans Visual Studio et utilisez la **fenêtre Commande** pour générer le projet et examiner les résultats.

## <a name="install-msbuild"></a>Installer MSBuild

::: moniker range="vs-2017"

Si vous disposez de Visual Studio, MSBuild est déjà installé. Pour installer MSBuild 15 sur un système qui ne dispose pas de Visual Studio, accédez à [téléchargements plus anciens de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/), développez **Visual Studio 2017** , puis choisissez le bouton **Télécharger** . Si vous disposez d’un abonnement Visual Studio, connectez-vous et recherchez le lien pour télécharger la dernière version des **outils de génération pour Visual Studio 2017**. Si vous n’avez pas d’abonnement Visual Studio, vous pouvez toujours installer la dernière version des outils de génération. Sur cette page, utilisez le sélecteur de version pour basculer vers la version 2019 de la page et suivez les instructions d’installation.
::: moniker-end

::: moniker range=">=vs-2019"
Si vous disposez de Visual Studio, MSBuild est déjà installé. Avec Visual Studio 2019 et versions ultérieures, il est installé dans le dossier d’installation de Visual Studio. Pour une installation par défaut classique sur Windows 10, MSBuild.exe se trouve sous le dossier d’installation dans *MSBuild\Current\Bin*.

Pour installer MSBuild sur un système qui ne dispose pas de Visual Studio, accédez à [téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/) et faites défiler jusqu’à **tous les téléchargements**, puis développez **outils pour Visual Studio 2019**. Installez les **outils de génération pour Visual Studio 2019**, qui incluent MSBuild, ou installez le [Kit SDK .net Core](/dotnet/core/sdk#acquiring-the-net-core-sdk).

Dans le programme d’installation, assurez-vous que les outils MSBuild pour les charges de travail que vous utilisez sont sélectionnés, puis choisissez **installer**.

![Installation de MSBuild](media/walkthrough-using-msbuild/installation-msbuild-tools.png)

::: moniker-end

## <a name="create-an-msbuild-project"></a>Création d’un projet MSBuild

 Le système de projet Visual Studio est basé sur MSBuild. La création d’un fichier projet à l’aide de Visual Studio est ainsi facilité. Dans cette section, vous créez un fichier projet Visual C#. Vous pouvez choisir de créer un fichier projet Visual Basic à la place. Dans le cadre de cette procédure pas à pas, la différence entre les deux fichiers projet est mineure.

**Pour créer un fichier projet**

1. Ouvrez Visual Studio et créez un projet.

    ::: moniker range=">=vs-2019"
    Appuyez sur **Échap** pour fermer la fenêtre de démarrage. Tapez **Ctrl+Q** pour ouvrir la zone de recherche, tapez **winforms**, puis choisissez **Créer une application Windows Forms (.NET Framework)**. Dans la boîte de dialogue qui apparaît, choisissez **Créer**.

    Dans le champ **Nom**, saisissez `BuildApp`. Entrez un **Emplacement** pour la solution, par exemple, *D :\\*. Acceptez les valeurs par défaut de **Solution**, **Nom de la solution** (**BuildApp**) et **Framework**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans la barre de menus supérieure, choisissez **fichier**  >  **nouveau**  >  **projet**. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, développez **Visual C#** > **Windows Desktop**, puis choisissez **Application Windows Forms (.NET Framework)**. Ensuite, choisissez **OK**.

    Dans le champ **Nom**, saisissez `BuildApp`. Entrez un **Emplacement** pour la solution, par exemple, *D :\\*. Acceptez les valeurs par défaut des options **Créer le répertoire pour la solution** (sélectionnée), **Ajouter au contrôle de code source** (non sélectionnée) et **Nom de la solution** (**BuildApp**).
    ::: moniker-end

1. Cliquez sur **OK** ou **Créer** pour créer le fichier projet.

## <a name="examine-the-project-file"></a>Examiner le fichier projet

 Dans la section précédente, vous avez utilisé Visual Studio pour créer un fichier projet Visual C#. Le fichier projet est représenté dans l’**Explorateur de solutions** par le nœud de projet nommé BuildApp. Vous pouvez examiner le fichier projet dans l’éditeur de code Visual Studio.

**Pour examiner le fichier projet**

1. Dans **Explorateur de solutions**, cliquez sur le nœud de projet **BuildApp**.

1. Dans l’Explorateur de **Propriétés** , Notez que la propriété du **fichier projet** est *BuildApp. csproj*. Tous les fichiers projet sont nommés avec le suffixe *proj*. Si vous avez créé un projet Visual Basic, le nom du fichier projet est *BuildApp. vbproj*.

1. Cliquez avec le bouton droit sur le nœud de projet une nouvelle fois, puis cliquez sur **Modifier BuildApp.csproj**. 

     Le fichier projet s’affiche dans l’éditeur de code.

>[!NOTE]
> Pour certains types de projets, tels que C++, vous devez décharger le projet (cliquez avec le bouton droit sur le fichier projet et choisissez **décharger le projet**) pour pouvoir ouvrir et modifier le fichier projet.

## <a name="targets-and-tasks"></a>Cibles et tâches

Les fichiers projet sont des fichiers XML avec le nœud racine [Projet](../msbuild/project-element-msbuild.md).

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0"  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Les nouveaux projets .NET Core (de style SDK) ont un `Sdk` attribut.

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

Si le projet n’est pas un projet de type SDK, vous devez spécifier l’espace de noms xmlns dans l’élément de projet. Si `ToolsVersion` est présent dans un nouveau projet, il doit s’agir de la version « 15.0 ».

Le processus de création d’une application est effectué avec les éléments [Target](../msbuild/target-element-msbuild.md) et [Task](../msbuild/task-element-msbuild.md).

- Une tâche est la plus petite unité de travail, en d’autres termes, « l’atome » d’une génération. Les tâches sont des composants exécutables indépendants qui peuvent compter des entrées et des sorties. Pour le moment, aucune tâche n’est référencée ni définie dans le fichier projet. Vous ajoutez des tâches au fichier projet dans les sections ci-dessous. Pour plus d’informations, consultez l’article [Tâches MSBuild](../msbuild/msbuild-tasks.md).

- Une cible est une séquence de tâches nommée. Pour plus d’informations, consultez l’article [Targets (Cibles MSBuild)](../msbuild/msbuild-targets.md).
- [il s’agit peut-être d’une séquence de tâches nommée, mais il s’agit d’une opération critique qui représente un travail à générer ou à faire. il doit donc être défini d’une manière orientée objectifs]

La cible par défaut n’est pas définie dans le fichier projet. Au lieu de cela, elle est spécifiée dans les projets importés. L’élément [Import](../msbuild/import-element-msbuild.md) spécifie les projets importés. Par exemple, dans un projet C#, la cible par défaut est importée à partir du fichier *Microsoft.CSharp.targets*.

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

Les fichiers importés sont insérés dans le fichier projet partout où ils sont référencés.

Dans les projets de type SDK, vous ne voyez pas cet élément import, car l’attribut SDK entraîne l’importation implicite de ce fichier.

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

La tâche Message est l’une des nombreuses tâches fournies avec MSBuild. Pour obtenir la liste complète des tâches disponibles et des informations sur l’utilisation, consultez [référence des tâches](../msbuild/msbuild-task-reference.md).

La tâche message prend la valeur de chaîne de l’attribut text comme entrée et l’affiche sur le périphérique de sortie (ou l’écrit dans un ou plusieurs journaux, le cas échéant). La cible HelloWorld exécute la tâche Message à deux reprises : tout d’abord pour afficher « Hello », puis pour afficher « World ».

## <a name="build-the-target"></a>Générer la cible

Si vous essayez de générer ce projet à partir de Visual Studio, il ne génère pas la cible que vous avez définie. Cela est dû au fait que Visual Studio choisit la cible par défaut, qui est toujours celle du fichier *. targets* importé.

Exécutez MSBuild à partir de **l’Invite de commandes développeur** pour Visual Studio pour générer la cible HelloWorld définie précédemment. Utilisez le commutateur de ligne de commande-Target ou-t pour sélectionner la cible.

> [!NOTE]
> Dans les sections ci-après, nous appellerons **l’Invite de commandes développeur****fenêtre Commande**.

**Pour générer la cible :**

1. Ouvrez la **fenêtre Commande**.

   (Windows 10) Dans la zone de recherche dans la barre des tâches, commencez à taper le nom de l’outil, tel que `dev` ou `developer command prompt`. S’affiche alors une liste des applications installées qui correspondent à votre modèle de recherche.

   Si vous devez le trouver manuellement, le fichier est *LaunchDevCmd.bat* dans le dossier *\> \<version> \Common7\Tools du dossier d’installation<VisualStudio* .

2. Dans la fenêtre commande, accédez au dossier contenant le fichier projet, dans le cas présent, *D:\BuildApp\BuildApp*.

3. Exécutez MSBuild avec le commutateur de commande `-t:HelloWorld` . Cette opération sélectionne et génère la cible HelloWorld :

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

 définit la propriété nommée TargetFrameworkVersion, en lui donnant la valeur de chaîne « v 4.5 ».

 Les propriétés de génération peuvent être redéfinies à tout moment. Si

```xml
<TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
```

 apparaît plus loin dans le fichier projet ou dans un fichier importé ultérieurement dans le fichier projet, TargetFrameworkVersion prend la nouvelle valeur « v3.5 ».

## <a name="examine-a-property-value"></a>Examiner une valeur de propriété

 Pour obtenir la valeur d’une propriété, utilisez la syntaxe suivante, où `PropertyName` est le nom de la propriété :

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

De nombreuses propriétés `Configuration` , telles que, sont définies de manière conditionnelle, autrement dit, l' `Condition` attribut apparaît dans l’élément Property. Les propriétés conditionnelles sont définies ou redéfinies uniquement si la condition a la valeur « true ». Notez que les propriétés non définies ont la valeur par défaut d’une chaîne vide. Par exemple,

```xml
<Configuration   Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

signifie « Si la propriété Configuration n’a pas encore été définie, définissez-la et attribuez-lui la valeur "Debug" ».

Pratiquement tous les éléments MSBuild peuvent posséder un attribut Condition. Pour en savoir plus sur l’utilisation de l’attribut Condition, consultez l’article [Conditions MSBuild](../msbuild/msbuild-conditions.md).

### <a name="reserved-properties"></a>Propriétés réservées

MSBuild réserve certains noms de propriété pour stocker des informations sur le fichier projet et les binaires de MSBuild. MSBuildToolsPath est un exemple de propriété réservée. Les propriétés réservées sont référencées avec la notation $ comme toute autre propriété. Pour plus d’informations, consultez [Guide pratique pour référencer le nom ou l’emplacement du fichier projet](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) et des [propriétés réservées et connues de MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).

### <a name="environment-variables"></a>Variables d'environnement

Vous pouvez référencer des variables d’environnement dans les fichiers projet de la même façon que les propriétés de génération. Par exemple, pour utiliser la variable d’environnement PATH dans votre fichier projet, utilisez $(Path). Si le projet contient une définition de propriété qui porte le même nom qu’une variable d’environnement, la propriété du projet remplace la valeur de la variable d’environnement. Pour plus d’informations, consultez [Comment : utiliser des variables d’environnement dans une build](../msbuild/how-to-use-environment-variables-in-a-build.md).

## <a name="set-properties-from-the-command-line"></a>Définir les propriétés à partir de la ligne de commande

Il est possible de définir des propriétés en ligne de commande à l’aide du commutateur de ligne de commande -property ou -p. Les valeurs de propriété reçues à partir de la ligne de commande remplacent celles qui sont définies dans les variables d’environnement et le fichier projet.

**Pour définir une valeur de propriété à partir de la ligne de commande :**

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

Certains caractères ont une signification spéciale dans les fichiers projet MSBuild. Il s’agit par exemple des points-virgules (;) et des astérisques (*). Pour utiliser ces caractères spéciaux en tant que littéraux dans un fichier projet, vous devez les spécifier à l’aide de la syntaxe% \<xx> , où \<xx> représente la valeur hexadécimale ASCII du caractère.

Modifiez la tâche Message pour afficher la valeur de la propriété Configuration avec des caractères spéciaux afin de la rendre plus lisible.

**Pour utiliser des caractères spéciaux dans la tâche message :**

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

Pour plus d’informations, consultez [caractères spéciaux MSBuild](../msbuild/msbuild-special-characters.md).

## <a name="build-items"></a>Générer des éléments

Un élément est une information, généralement un nom de fichier, qui est utilisée comme entrée dans le système de génération. Par exemple, une collection d’éléments représentant des fichiers sources peut être transmise à une tâche nommée Compile pour les compiler dans un assembly.

Tous les éléments sont des éléments enfants des éléments ItemGroup. Le nom de l’élément est le nom de l’élément enfant, et la valeur de l’élément est la valeur de l’attribut Include de l’élément enfant. Les valeurs des éléments du même nom sont collectées dans les types d’élément de ce nom.  Par exemple,

```xml
<ItemGroup>
    <Compile Include="Program.cs" />
    <Compile Include="Properties\AssemblyInfo.cs" />
</ItemGroup>
```

définit un groupe de deux éléments. La compilation du type d’élément a deux valeurs : *Program. cs* et *Properties\AssemblyInfo.cs*.

Le code suivant crée le même type d’élément en déclarant les deux fichiers dans un attribut Include, séparés par un point-virgule.

```xml
<ItemGroup>
    <Compile Include="Program.cs;Properties\AssemblyInfo.cs" />
</ItemGroup>
```

Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).

> [!NOTE]
> Les chemins d’accès aux fichiers sont relatifs au dossier contenant le fichier projet MSBuild, même si le fichier projet est un fichier projet importé. Il existe quelques exceptions à ce cas, par exemple lors de l’utilisation d’éléments [Import](import-element-msbuild.md) et [UsingTask](usingtask-element-msbuild.md) .

## <a name="examine-item-type-values"></a>Examiner des valeurs de type d’élément

 Pour obtenir les valeurs d’un type d’élément, utilisez la syntaxe suivante, où ItemType est le nom du type d’élément :

```xml
@(ItemType)
```

Utilisez cette syntaxe pour examiner le type d’élément Compile dans le fichier projet.

**Pour examiner les valeurs de type d’élément :**

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

 ajoute tous les fichiers avec l’extension de fichier *. jpeg* dans le dossier *images* au type d’élément photos, alors que

```xml
<Photos Include="images\**\*.jpeg" />
```

 ajoute tous les fichiers avec l’extension de fichier *. jpeg* dans le dossier *images* , ainsi que tous ses sous-dossiers, au type d’élément photos. Pour obtenir plus d’exemples, consultez [Comment : sélectionner les fichiers à générer](../msbuild/how-to-select-the-files-to-build.md).

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

 ajoute tous les fichiers portant l’extension de fichier  *.cs* au type d’élément Compile, à l’exception des fichiers dont les noms contiennent la chaîne *Designer*. Pour obtenir plus d’exemples, consultez [Comment : exclure des fichiers de la build](../msbuild/how-to-exclude-files-from-the-build.md).

L’attribut Exclude affecte uniquement les éléments ajoutés par l’attribut Include dans l’élément Item qui les contient. Par exemple,

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

n’exclut pas le fichier *Form1. cs*, qui a été ajouté dans l’élément item précédent.

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

**Pour examiner les métadonnées de l’élément :**

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

 Chaque fois qu’un élément est ajouté à une liste d’éléments, il reçoit des métadonnées connues. Par exemple, %(Filename) retourne le nom de fichier de n’importe quel élément. Pour obtenir la liste complète des métadonnées connues, consultez [métadonnées d’éléments connus](../msbuild/msbuild-well-known-item-metadata.md).

**Pour examiner les métadonnées connues :**

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

 Les listes d’éléments peuvent être transformées en nouvelles listes d’éléments. Pour transformer une liste d’éléments, utilisez la syntaxe suivante, où \<ItemType> est le nom du type d’élément et \<MetadataName> est le nom des métadonnées :

```xml
@(ItemType -> '%(MetadataName)')
```

Par exemple, une liste d’éléments de fichiers sources peut être transformée en une collection de fichiers objets à l’aide d’une expression comme `@(SourceFiles -> '%(Filename).obj')`. Pour plus d’informations, consultez l’article [Transforms (Transformations MSBuild)](../msbuild/msbuild-transforms.md).

**Pour transformer des éléments à l’aide de métadonnées :**

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

 Pour savoir comment créer un fichier de projet simple en une seule étape à la fois, essayez la [procédure pas à pas : création d’un fichier projet MSBuild en partant de zéro](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de MSBuild](../msbuild/msbuild.md)
- [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)
