---
title: Créer un fichier projet MSBuild à partir de zéro
description: Découvrez comment créer un fichier projet MSBuild en partant de zéro pour comprendre comment le code XML est organisé et comment vous pouvez le modifier pour contrôler une build.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: e3acff7c-cb4e-4ae1-8be2-a871bcff847b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2d3d0462382ddcc86a23c7e25162fb429b9f9893
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967538"
---
# <a name="walkthrough-create-an-msbuild-project-file-from-scratch"></a>Procédure pas à pas : créer un fichier projet MSBuild en partant de zéro

Les langages de programmation qui ciblent .NET Framework utilisent des fichiers projet MSBuild pour décrire et contrôler le processus de génération d'application. Quand vous utilisez Visual Studio pour créer un fichier projet MSBuild, le code XML approprié est ajouté automatiquement au fichier. Il peut cependant être utile de comprendre comment le code XML est organisé et comment vous pouvez le modifier pour contrôler une build.

 Pour plus d’informations sur la création d’un fichier projet pour un projet C++, consultez [MSBuild (c++)](/cpp/build/msbuild-visual-cpp).

 Cette procédure pas à pas montre comment créer progressivement un fichier projet de base, en utilisant seulement un éditeur de texte. Cette procédure pas à pas comprend les étapes suivantes :

1. Étendez la variable d’environnement PATH.

2. Créer un fichier source d'application minimal.

3. Créer un fichier projet MSBuild minimal.

4. Générer l'application en utilisant le fichier projet.

5. Ajouter des propriétés pour contrôler la build.

6. Contrôler la build en changeant les valeurs de propriétés.

7. Ajouter des cibles à la build.

8. Contrôler la build en spécifiant des cibles.

9. Générer de façon incrémentielle.

Cette procédure pas à pas montre comment créer le projet sur l'invite de commandes et examiner les résultats. Pour plus d’informations sur MSBuild et son exécution à l’invite de commandes, consultez la [Procédure pas à pas : utiliser MSBuild](../msbuild/walkthrough-using-msbuild.md).

Pour effectuer la procédure pas à pas, vous devez avoir installé Visual Studio, car il comprend MSBuild et le compilateur Visual C#, qui sont requis pour la procédure pas à pas.

## <a name="extend-the-path"></a>Étendre le chemin d’accès

Avant de pouvoir utiliser MSBuild, vous devez étendre la variable d’environnement PATH pour inclure tous les outils requis. Vous pouvez utiliser le **invite de commandes développeur pour Visual Studio**. Recherchez-le sur Windows 10 dans la zone de recherche de la barre des tâches Windows. Pour configurer l’environnement dans une invite de commandes ordinaire ou dans un environnement de script, exécutez *VSDevCmd.bat* dans le sous-dossier *Common7/Tools* d’une installation Visual Studio.

## <a name="create-a-minimal-application"></a>Créer une application minimale

 Cette section montre comment créer un fichier source d’application C# minimal à l’aide d’un éditeur de texte.

1. À l’invite de commandes, accédez au dossier dans lequel vous souhaitez créer l’application, par exemple *\Mes documents \\* ou *\Bureau \\*.

2. Tapez **MD HelloWorld** pour créer un sous-dossier *nommé \\ \HelloWorld*.

3. Entrez **cd HelloWorld** pour accéder au nouveau dossier.

4. Démarrez le Bloc-notes ou un autre éditeur de texte, puis entrez le code suivant.

    ```csharp
    using System;

    class HelloWorld
    {
        static void Main()
        {
    #if DebugConfig
            Console.WriteLine("WE ARE IN THE DEBUG CONFIGURATION");
    #endif

            Console.WriteLine("Hello, world!");
        }
    }
    ```

5. Enregistrez ce fichier de code source et nommez-le *HelloWorld.cs*.

6. Générez l’application en entrant **csc helloworld.cs** à l’invite de commandes.

7. Testez l’application en entrant **helloworld** à l’invite de commandes.

     Le message **Hello, world!** doit s’afficher.

8. Supprimez l’application en entrant **del helloworld.exe** à l’invite de commandes.

## <a name="create-a-minimal-msbuild-project-file"></a>Créer un fichier projet MSBuild minimal

 Maintenant que vous avez un fichier source d'application minimal, vous pouvez créer un fichier projet minimal pour générer l'application. Ce fichier projet contient les éléments suivants :

- Le nœud `Project` racine requis.

- Un nœud `ItemGroup` pour contenir les éléments item.

- Un élément item qui référence le fichier source d'application.

- Un nœud `Target` pour contenir les tâches requises pour générer l'application.

- Un élément `Task` pour démarrer le compilateur Visual C# pour générer l'application.

### <a name="to-create-a-minimal-msbuild-project-file"></a>Pour créer un fichier projet MSBuild minimal

1. Dans l'éditeur de texte, remplacez le texte existant en utilisant ces deux lignes :

    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

2. Insérez ce nœud `ItemGroup` comme élément enfant du nœud `Project` :

    ```xml
    <ItemGroup>
      <Compile Include="helloworld.cs" />
    </ItemGroup>
    ```

     Notez que ce nœud `ItemGroup` contient déjà un élément item.

3. Ajoutez un nœud `Target` comme élément enfant du nœud `Project`. Nommez le nœud `Build`.

    ```xml
    <Target Name="Build">
    </Target>
    ```

4. Insérez cet élément de tâche comme élément enfant du nœud `Target` :

    ```xml
    <Csc Sources="@(Compile)"/>
    ```

5. Enregistrez ce fichier projet et nommez-le *HelloWorld. csproj*.

Votre fichier projet minimal doit ressembler au code suivant :

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <Csc Sources="@(Compile)"/>  
  </Target>
</Project>
```

Les tâches de la cible Build sont exécutées séquentiellement. Dans ce cas, la tâche du compilateur Visual C# `Csc` est la seule tâche. Elle attend une liste de fichiers source à compiler, qui lui est donnée par la valeur de l'élément `Compile`. L' `Compile` élément ne fait référence qu’à un seul fichier source, *HelloWorld.cs*.

> [!NOTE]
> Dans l’élément Item, vous pouvez utiliser le caractère générique astérisque ( \* ) pour référencer tous les fichiers ayant l’extension de nom de fichier *. cs* , comme suit :
>
> ```xml
> <Compile Include="*.cs" />
> ```

## <a name="build-the-application"></a>Créer l’application

 Maintenant, pour créer l'application, utilisez le fichier projet que vous venez de créer.

1. À l’invite de commandes, tapez **MSBuild HelloWorld. csproj-t :Build**.

     Ceci crée la cible Build du fichier projet Helloworld en appelant le compilateur Visual C# pour créer l'application Helloworld.

2. Testez l’application en entrant **helloworld**.

     Le message **Hello, world!** doit s’afficher.

> [!NOTE]
> Vous pouvez afficher plus de détails sur la génération en augmentant le niveau de détail. Pour définir le niveau de détail sur « détaillé », entrez cette commande à l’invite de commandes :
>
> **MSBuild HelloWorld. csproj-t :Build-verbosity : detailed**

## <a name="add-build-properties"></a>Ajouter des propriétés de build

 Vous pouvez ajouter des propriétés de build au fichier projet pour contrôler davantage la génération. Ajoutez maintenant ces propriétés :

- Une propriété `AssemblyName` pour spécifier le nom de l'application.

- Une propriété `OutputPath` pour spécifier un dossier destiné à contenir l'application.

### <a name="to-add-build-properties"></a>Pour ajouter des propriétés de build

1. Supprimez l’application en entrant **del helloworld.exe** à l’invite de commandes.

2. Dans le fichier projet, insérez cet élément `PropertyGroup` juste après l'élément `Project` du début :

    ```xml
    <PropertyGroup>
      <AssemblyName>MSBuildSample</AssemblyName>
      <OutputPath>Bin\</OutputPath>
    </PropertyGroup>
    ```

3. Ajoutez cette tâche à la cible Build, juste avant la tâche `Csc` :

    ```xml
    <MakeDir Directories="$(OutputPath)"      Condition="!Exists('$(OutputPath)')" />
    ```

     La tâche `MakeDir` crée un dossier dont le nom est donné par la propriété `OutputPath`, à condition qu'aucun dossier de ce nom n'existe déjà.

4. Ajoutez cet attribut `OutputAssembly` à la tâche `Csc` :

    ```xml
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    ```

     Ceci demande au compilateur Visual C# de produire un assembly dont le nom est donné par la propriété `AssemblyName` et de le placer dans le dossier dont le nom est donné par la propriété `OutputPath`.

5. Enregistrez vos modifications.

Votre fichier projet doit maintenant ressembler au code suivant :

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <AssemblyName>MSBuildSample</AssemblyName>
    <OutputPath>Bin\</OutputPath>
  </PropertyGroup>
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
  </Target>
</Project>
```

> [!NOTE]
> Nous vous recommandons d’ajouter le délimiteur de chemin (\\) (barre oblique inverse) à la fin du nom du dossier quand vous le spécifiez dans l’élément `OutputPath`, au lieu de l’ajouter dans l’attribut `OutputAssembly` de la tâche `Csc`. Par conséquent,
>
> `<OutputPath>Bin\</OutputPath>`
>
> `OutputAssembly="$(OutputPath)$(AssemblyName).exe" />`
>
> est mieux que
>
> `<OutputPath>Bin</OutputPath>`
>
> `OutputAssembly="$(OutputPath)\$(AssemblyName).exe" />`

## <a name="test-the-build-properties"></a>Tester les propriétés de build

 Vous pouvez maintenant générer l'application en utilisant le fichier projet où vous avez utilisé des propriétés de build pour spécifier le dossier de sortie et le nom de l'application.

1. À l’invite de commandes, tapez **MSBuild HelloWorld. csproj-t :Build**.

     Cela crée le *dossier \\ \Bin* , puis appelle le compilateur Visual C# pour créer l’application *MSBuildSample* et la place dans le dossier *\Bin \\* .

2. Pour vérifier que le *dossier \\ \Bin* a été créé et qu’il contient l’application *MSBuildSample* , tapez **dir Bin**.

3. Testez l’application en entrant **Bin\MSBuildSample**.

     Le message **Hello, world!** doit s’afficher.

## <a name="add-build-targets"></a>Ajouter des cibles de génération

 Ensuite, ajoutez deux cibles de plus au fichier projet, comme suit :

- Une cible Clean qui supprime les anciens fichiers.

- Une cible Rebuild qui utilise l'attribut `DependsOnTargets` pour forcer la tâche Clean à s'exécuter avant la tâche Build.

Maintenant que vous avez plusieurs cibles, vous pouvez définir la cible Build comme cible par défaut.

### <a name="to-add-build-targets"></a>Pour ajouter des cibles de génération

1. Dans le fichier projet, ajoutez ces deux cibles juste après la cible Build :

    ```xml
    <Target Name="Clean" >
      <Delete Files="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    <Target Name="Rebuild" DependsOnTargets="Clean;Build" />
    ```

     La cible Clean appelle la tâche Delete pour supprimer l'application. La cible Rebuild ne s'exécute pas tant que la cible Clean et la cible Build n'ont pas été exécutées. Même si la cible Rebuild n'a pas de tâches, elle provoque l'exécution de la cible Clean avant l'exécution de la cible Build.

2. Ajoutez cet attribut `DefaultTargets` à l'élément `Project` du début :

    ```xml
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    ```

     Ceci définit la cible Build comme cible par défaut.

Votre fichier projet doit maintenant ressembler au code suivant :

```xml
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <AssemblyName>MSBuildSample</AssemblyName>
    <OutputPath>Bin\</OutputPath>
  </PropertyGroup>
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
  </Target>
  <Target Name="Clean" >
    <Delete Files="$(OutputPath)$(AssemblyName).exe" />
  </Target>
  <Target Name="Rebuild" DependsOnTargets="Clean;Build" />
</Project>
```

## <a name="test-the-build-targets"></a>Tester les cibles de génération

 Vous pouvez utiliser les nouvelles cibles de génération pour tester ces fonctionnalités dans le fichier projet :

- Création de la génération par défaut

- Définition du nom de l'application à l'invite de commandes

- Suppression de l'application avant la génération d'une autre application

- Suppression de l'application sans génération d'une autre application

### <a name="to-test-the-build-targets"></a>Pour tester les cibles de génération

1. À l’invite de commandes, tapez **MSBuild HelloWorld. csproj-p :AssemblyName = Greetings**.

     Étant donné que vous n’avez pas utilisé le commutateur **-t** pour définir explicitement la cible, MSBuild exécute la cible de génération par défaut. Le commutateur **-p** remplace la `AssemblyName` propriété et lui donne la nouvelle valeur, `Greetings` . Cela entraîne la création d’une nouvelle application, *Greetings.exe*, dans le *dossier \\ \Bin* .

2. Pour vérifier que le *dossier \\ \Bin* contient à la fois l’application *MSBuildSample* et la nouvelle application *Greetings* , tapez **dir Bin**.

3. Testez l’application Greetings en entrant **Bin\Greetings**.

     Le message **Hello, world!** doit s’afficher.

4. Supprimez l’application MSBuildSample en tapant **MSBuild HelloWorld. csproj-t :Clean**.

     Cela exécute la tâche Clean pour supprimer l’application qui a la valeur de la propriété `AssemblyName` par défaut, `MSBuildSample`.

5. Pour supprimer l’application Greetings, tapez **MSBuild HelloWorld. csproj-t :Clean-p :AssemblyName = Greetings**.

     Cela exécute la tâche Clean pour supprimer l’application qui a la valeur de la propriété **AssemblyName** spécifiée, `Greetings`.

6. Pour vérifier que le *dossier \\ \Bin* est maintenant vide, tapez **dir Bin**.

7. Tapez **msbuild**.

     Même si aucun fichier projet n’est spécifié, MSBuild génère le fichier *HelloWorld. csproj* , car il n’y a qu’un seul fichier projet dans le dossier actif. Cela entraîne la création de l’application *MSBuildSample* dans le *dossier \\ \Bin* .

     Pour vérifier que le *dossier \\ \Bin* contient l’application *MSBuildSample* , tapez **dir Bin**.

## <a name="build-incrementally"></a>Générer de façon incrémentielle

 Vous pouvez indiquer à MSBuild de générer une cible seulement si les fichiers source ou les fichiers cible dont dépend la cible ont changé. MSBuild utilise l'horodatage d'un fichier pour déterminer s'il a changé.

### <a name="to-build-incrementally"></a>Pour générer de façon incrémentielle

1. Dans le fichier projet, ajoutez ces attributs après la cible Build du début :

    ```xml
    Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe"
    ```

     Ceci spécifie que la cible Build dépend des fichiers d'entrée qui sont spécifiés dans le groupe d'éléments `Compile` et que la cible en sortie est le fichier d'application.

     La cible Build résultante doit être similaire au code suivant :

    ```xml
    <Target Name="Build" Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe">
      <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
      <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    ```

2. Testez la cible Build en tapant **MSBuild-v :d** à l’invite de commandes.

     N’oubliez pas que *HelloWorld. csproj* est le fichier projet par défaut et que Build est la cible par défaut.

     Le commutateur **-v :d** spécifie une description détaillée pour le processus de génération.

     Ces lignes doivent être affichées.

     **La cible est ignorée "Build", car tous les fichiers de sortie sont à jour par rapport aux fichiers d'entrée.**

     **Fichiers d'entrée: HelloWorld.cs**

     **Fichiers de sortie: BinMSBuildSample.exe**

     MSBuild ignore la cible Build, car aucun des fichiers source n'a changé depuis la dernière génération de l'application.

## <a name="c-example"></a>Exemple en code C#

L’exemple suivant montre un fichier projet qui compile une application C# et enregistre un message contenant le nom du fichier de sortie.

### <a name="code"></a>Code

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>HelloWorldCS</appname>
    </PropertyGroup>

    <!-- Specify the inputs by type and file name -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using input files of type CSFile -->
        <CSC
            Sources = "@(CSFile)"
            OutputAssembly = "$(appname).exe">
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="visual-basic-example"></a>Exemple Visual Basic

L’exemple suivant montre un fichier projet qui compile une application Visual Basic et enregistre un message qui contient le nom du fichier de sortie.

### <a name="code"></a>Code

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>HelloWorldVB</appname>
    </PropertyGroup>

    <!-- Specify the inputs by type and file name -->
    <ItemGroup>
        <VBFile Include = "consolehwvb1.vb"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Run the Visual Basic compilation using input files of type VBFile -->
        <VBC
            Sources = "@(VBFile)"
            OutputAssembly= "$(appname).exe">
            <!-- Set the OutputAssembly attribute of the VBC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </VBC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="whats-next"></a>Quelle est l’étape suivante ?

 Visual Studio peut faire automatiquement la plus grande partie du travail qui est montré dans cette procédure pas à pas. Pour découvrir comment utiliser Visual Studio pour créer, modifier, générer et tester des fichiers projet MSBuild, consultez la [Procédure pas à pas : utiliser MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de MSBuild](../msbuild/msbuild.md)
- [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)
