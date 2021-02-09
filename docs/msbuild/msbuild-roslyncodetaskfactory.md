---
title: Tâches inline MSBuild avec RoslynCodeTaskFactory | Microsoft Docs
description: En savoir plus sur MSBuild RoslynCodeTaskFactory, qui utilise les compilateurs Roslyn multiplateforme pour générer des assemblys de tâche en mémoire à utiliser comme tâches Inline.
ms.custom: SEO-VS-2020
ms.date: 09/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: e72e6506-4a11-4edf-ae8d-cfb5a3b9d8a0
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c033c4d0ee36b9cb01618dd3ac3183e8782c70d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878420"
---
# <a name="msbuild-inline-tasks-with-roslyncodetaskfactory"></a>Tâches inline MSBuild avec RoslynCodeTaskFactory

Comme [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md), RoslynCodeTaskFactory utilise les compilateurs Roslyn multiplateformes pour générer des assemblys de tâches en mémoire à utiliser en tant que tâches inline.  Les tâches RoslynCodeTaskFactory ciblent .NET Standard et peuvent fonctionner sur les runtimes .NET Framework et .NET Core, ainsi que sur d’autres plateformes, comme Linux et Mac OS.

>[!NOTE]
>RoslynCodeTaskFactory est disponible uniquement dans MSBuild 15.8 et les versions ultérieures. Les versions de MSBuild suivent les versions de Visual Studio. par conséquent, RoslynCodeTaskFactory est disponible dans Visual Studio 2017 version 15,8 ou ultérieure.

## <a name="the-structure-of-an-inline-task-with-roslyncodetaskfactory"></a>Structure d’une tâche inline avec RoslynCodeTaskFactory

 Les tâches inline RoslynCodeTaskFactory sont déclarées de manière identique à [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md), à ceci près qu’elles ciblent .NET Standard.  La tâche inline et l’élément `UsingTask` qui la contient sont généralement inclus dans un fichier *.targets* et importés dans d’autres fichiers projet selon les besoins. Voici une tâche inline de base. Notez qu’elle n’a aucun effet.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task does nothing. -->
  <UsingTask
    TaskName="DoNothing"
    TaskFactory="RoslynCodeTaskFactory"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >
    <ParameterGroup />
    <Task>
      <Reference Include="" />
      <Using Namespace="" />
      <Code Type="Fragment" Language="cs">
      </Code>
    </Task>
  </UsingTask>
</Project>
```

 L’élément `UsingTask` dans l’exemple a trois attributs qui décrivent la tâche et la fabrique de tâches inline qui la compile.

- L’attribut `TaskName` nomme la tâche, dans le cas présent `DoNothing`.

- L’attribut `TaskFactory` nomme la classe qui implémente la fabrique de tâches inline.

- L’attribut `AssemblyFile` indique l’emplacement de la fabrique de tâches inline. Vous pouvez également utiliser l’attribut `AssemblyName` pour spécifier le nom qualifié complet de la classe de fabrique de tâches inline, qui se trouve généralement dans le global assembly cache (GAC).

Les éléments restants de la tâche `DoNothing` sont vides et fournis pour illustrer l’ordre et la structure d’une tâche inline. Un exemple plus pertinent est présenté plus loin dans cette rubrique.

- L’élément `ParameterGroup` est facultatif. Quand il est spécifié, il déclare les paramètres de la tâche. Pour plus d’informations sur les paramètres d’entrée et de sortie, consultez [paramètres d’entrée et de sortie](#input-and-output-parameters) plus loin dans cette rubrique.

- L’élément `Task` décrit et contient le code source de la tâche.

- L’élément `Reference` spécifie des références aux assemblys .NET que vous utilisez dans votre code. Cela équivaut à ajouter une référence à un projet dans Visual Studio. L’attribut `Include` spécifie le chemin de l’assembly référencé.

- L’élément `Using` répertorie les espaces de noms auxquels vous souhaitez accéder. Cela ressemble à l’instruction `Using` en Visual C#. L’attribut `Namespace` spécifie l’espace de noms à inclure.

Les éléments `Reference` et `Using` sont indépendants du langage. Les tâches inline peuvent être écrites dans n’importe quel langage .NET CodeDom pris en charge, par exemple Visual Basic ou Visual C#.

> [!NOTE]
> Les éléments contenus dans l’élément `Task` sont propres à la fabrique de tâches, dans le cas présent la fabrique de tâches de code.

### <a name="code-element"></a>Élément de code

Le dernier élément enfant de l’élément `Task` est l’élément `Code`. L’élément `Code` contient ou identifie le code à compiler dans une tâche. Ce que vous placez dans l’élément `Code` dépend de la façon dont vous souhaitez écrire la tâche.

L’attribut `Language` spécifie le langage dans lequel votre code est écrit. Les valeurs acceptables sont `cs` pour C# et `vb` pour Visual Basic.

L’attribut `Type` spécifie le type de code qui se trouve dans l’élément `Code`.

- Si la valeur de `Type` est `Class`, l’élément `Code` contient du code pour une classe qui dérive de l’interface <xref:Microsoft.Build.Framework.ITask>.

- Si la valeur de `Type` est `Method`, le code définit une substitution de la méthode `Execute` de l’interface <xref:Microsoft.Build.Framework.ITask>.

- Si la valeur de `Type` est `Fragment`, le code définit le contenu de la méthode `Execute`, mais pas la signature ou l’instruction `return`.

Le code proprement dit apparaît généralement entre un marqueur `<![CDATA[` et un marqueur `]]>`. Étant donné que le code se trouve dans une section CDATA, vous n’avez pas à vous soucier de la séquence d’échappement des caractères réservés, par exemple, « \<" or "> ».

Vous pouvez également utiliser l’attribut `Source` de l’élément `Code` pour spécifier l’emplacement d’un fichier qui contient le code de votre tâche. Le code dans le fichier source doit être du type spécifié par l’attribut `Type`. Si l’attribut `Source` est présent, la valeur par défaut de `Type` est `Class`. Si `Source` est absent, la valeur par défaut est `Fragment`.

> [!NOTE]
> Quand vous définissez la classe de la tâche dans le fichier source, le nom de classe doit correspondre à l’attribut `TaskName` de l’élément [UsingTask](../msbuild/usingtask-element-msbuild.md) correspondant.

## <a name="hello-world"></a>Hello World

 Voici une tâche inline plus robuste avec RoslynCodeTaskFactory. La tâche HelloWorld affiche « Hello, world! » sur l’appareil de journalisation des erreurs par défaut, qui est généralement la console système ou la fenêtre **Sortie** de Visual Studio. L’élément `Reference` dans l’exemple est fourni uniquement à titre d’illustration.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task displays "Hello, world!" -->
  <UsingTask
    TaskName="HelloWorld"
    TaskFactory="RoslynCodeTaskFactory"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >
    <ParameterGroup />
    <Task>
      <Reference Include="System.Xml"/>
      <Using Namespace="System"/>
      <Using Namespace="System.IO"/>
      <Code Type="Fragment" Language="cs">
<![CDATA[
// Display "Hello, world!"
Log.LogError("Hello, world!");
]]>
      </Code>
    </Task>
  </UsingTask>
</Project>
```

Vous pouvez enregistrer la tâche HelloWorld dans un fichier nommé *HelloWorld.targets*, puis l’appeler à partir d’un projet en procédant comme suit.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="HelloWorld.targets" />
  <Target Name="Hello">
    <HelloWorld />
  </Target>
</Project>
```

## <a name="input-and-output-parameters"></a>Paramètres d’entrée et de sortie

 Les paramètres de tâche inline sont des éléments enfants d’un élément `ParameterGroup`. Chaque paramètre prend le nom de l’élément qui le définit. Le code suivant définit le paramètre `Text`.

```xml
<ParameterGroup>
    <Text />
</ParameterGroup>
```

Les paramètres peuvent avoir un ou plusieurs de ces attributs :

- `Required` est un attribut facultatif qui est `false` par défaut. Si cet attribut est `true`, le paramètre est obligatoire et vous devez lui affecter une valeur avant d’appeler la tâche.

- `ParameterType` est un attribut facultatif qui est `System.String` par défaut. Vous pouvez lui affecter n’importe quel type qualifié complet qui est un élément ou une valeur pouvant être converti vers et à partir d’une chaîne à l’aide de System.Convert.ChangeType. (En d’autres termes, tout type qui peut être passé à et depuis une tâche externe.)

- `Output` est un attribut facultatif qui est `false` par défaut. Si cet attribut est `true`, vous devez affecter une valeur au paramètre avant le retour de la méthode Execute.

Par exemple,

```xml
<ParameterGroup>
    <Expression Required="true" />
    <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />
    <Tally ParameterType="System.Int32" Output="true" />
</ParameterGroup>
```

définit ces trois paramètres :

- `Expression` est un paramètre d’entrée obligatoire de type System.String.

- `Files` est un paramètre d’entrée de liste d’éléments obligatoire.

- `Tally` est un paramètre de sortie de type System.Int32.

Si l’élément `Code` a un attribut `Type` égal à `Fragment` ou `Method`, des propriétés sont créées automatiquement pour chaque paramètre.  Dans RoslynCodeTaskFactory, si l' `Code` élément a l' `Type` attribut de `Class` , vous n’avez pas besoin de spécifier le `ParameterGroup` , car il est déduit du code source (il s’agit d’une différence par rapport à `CodeTaskFactory` ). Dans le cas contraire, les propriétés doivent être déclarées explicitement dans le code source de la tâche, et elles doivent correspondre exactement à leurs définitions de paramètres.

## <a name="example"></a>Exemple

 La tâche inline suivante consigne des messages et retourne une chaîne.

```xml
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">

    <UsingTask TaskName="MySample"
               TaskFactory="RoslynCodeTaskFactory"
               AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Parameter1 ParameterType="System.String" Required="true" />
            <Parameter2 ParameterType="System.String" />
            <Parameter3 ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
              <![CDATA[
              Log.LogMessage(MessageImportance.High, "Hello from an inline task created by Roslyn!");
              Log.LogMessageFromText($"Parameter1: '{Parameter1}'", MessageImportance.High);
              Log.LogMessageFromText($"Parameter2: '{Parameter2}'", MessageImportance.High);
              Parameter3 = "A value from the Roslyn CodeTaskFactory";
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <Target Name="Demo">
      <MySample Parameter1="A value for parameter 1" Parameter2="A value for parameter 2">
          <Output TaskParameter="Parameter3" PropertyName="NewProperty" />
      </MySample>

      <Message Text="NewProperty: '$(NewProperty)'" />
    </Target>
</Project>
```

Ces tâches inline peuvent combiner des chemins et obtenir le nom de fichier.

```xml
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">

    <UsingTask TaskName="PathCombine"
               TaskFactory="RoslynCodeTaskFactory"
               AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Paths ParameterType="System.String[]" Required="true" />
            <Combined ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
            <![CDATA[
            Combined = Path.Combine(Paths);
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <UsingTask TaskName="PathGetFileName"
             TaskFactory="RoslynCodeTaskFactory"
             AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Path ParameterType="System.String" Required="true" />
            <FileName ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
            <![CDATA[
            FileName = System.IO.Path.GetFileName(Path);
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <Target Name="Demo">
        <PathCombine Paths="$(Temp);MyFolder;$([System.Guid]::NewGuid()).txt">
            <Output TaskParameter="Combined" PropertyName="MyCombinedPaths" />
        </PathCombine>

        <Message Text="Combined Paths: '$(MyCombinedPaths)'" />

        <PathGetFileName Path="$(MyCombinedPaths)">
            <Output TaskParameter="FileName" PropertyName="MyFileName" />
        </PathGetFileName>

        <Message Text="File name: '$(MyFileName)'" />
    </Target>
</Project>
```

## <a name="provide-backward-compatibility"></a>Fournir une compatibilité descendante

`RoslynCodeTaskFactory` est d’abord disponible dans MSBuild version 15,8. Supposons que vous ayez besoin de prendre en charge les versions antérieures de Visual Studio et de MSBuild, lorsque n' `RoslynCodeTaskFactory` était pas disponible, mais que `CodeTaskFactory` était, mais que vous souhaitez utiliser le même script de compilation. Vous pouvez utiliser une `Choose` construction qui utilise la `$(MSBuildVersion)` propriété pour déterminer au moment de la génération s’il faut utiliser `RoslynCodeTaskFactory` ou revenir à `CodeTaskFactory` , comme dans l’exemple suivant :

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <Choose>
    <When Condition=" '$(MSBuildVersion.Substring(0,2))' >= 16 Or
    ('$(MSBuildVersion.Substring(0,2))' == 15 And '$(MSBuildVersion.Substring(3,1))' >= 8)">
      <PropertyGroup>
        <TaskFactory>RoslynCodeTaskFactory</TaskFactory>
      </PropertyGroup>
    </When>
    <Otherwise>
      <PropertyGroup>
        <TaskFactory>CodeTaskFactory</TaskFactory>
      </PropertyGroup>
    </Otherwise>
  </Choose>
  
  <UsingTask
    TaskName="HelloWorld"
    TaskFactory="$(TaskFactory)"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll">
    <ParameterGroup />
    <Task>
      <Using Namespace="System"/>
      <Using Namespace="System.IO"/>
      <Code Type="Fragment" Language="cs">
        <![CDATA[
         Log.LogError("Using RoslynCodeTaskFactory");
      ]]>
      </Code>
    </Task>
  </UsingTask>

  <Target Name="RunTask" AfterTargets="Build">
    <Message Text="MSBuildVersion: $(MSBuildVersion)"/>
    <Message Text="TaskFactory: $(TaskFactory)"/>
    <HelloWorld />
  </Target>

</Project>
```

## <a name="see-also"></a>Voir aussi

- [Tâches](../msbuild/msbuild-tasks.md)
- [Procédure pas à pas : Créer une tâche inline](../msbuild/walkthrough-creating-an-inline-task.md)
