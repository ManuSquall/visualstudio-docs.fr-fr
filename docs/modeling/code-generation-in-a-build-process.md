---
title: Génération de code dans un processus de génération
description: Découvrez comment la transformation de texte peut être appelée dans le cadre du processus de génération d’une solution Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: how-to
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 7db1b41df5007678c84be71f34aea110c04348c1
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389746"
---
# <a name="invoke-text-transformation-in-the-build-process"></a>Appeler la transformation de texte dans le processus de génération

La [transformation de texte](../modeling/code-generation-and-t4-text-templates.md) peut être appelée dans le cadre du processus de [génération](/azure/devops/pipelines/index) d’une solution Visual Studio. Il existe des tâches de génération qui sont spécialisées pour la transformation de texte. Les tâches de génération T4 exécutent les modèles de texte au moment du design. En outre, elles compilent les modèles de texte (prétraités) au moment de l’exécution.

Il existe quelques différences en matière de possibilités offertes par les tâches de génération, selon le moteur de génération que vous utilisez. Lorsque vous générez la solution dans Visual Studio, un modèle de texte peut accéder à l’API Visual Studio (EnvDTE) si l’attribut [hostspecific = "true"](../modeling/t4-template-directive.md) est défini. Mais cela n’est pas vrai lorsque vous générez la solution à partir de la ligne de commande ou lorsque vous lancez une génération de serveur par le biais de Visual Studio. Dans ces situations, la génération est exécutée par MSBuild et un autre hôte T4 est utilisé. Cela signifie que vous ne pouvez pas accéder à des éléments tels que des noms de fichiers projet de la même façon quand vous générez un modèle de texte à l’aide de MSBuild. Toutefois, vous pouvez [passer des informations d’environnement dans des modèles de texte et des processeurs de directive en utilisant des paramètres de build](#parameters).

## <a name="configure-your-machines"></a><a name="buildserver"></a> Configurer vos ordinateurs

Pour activer les tâches de génération sur votre ordinateur de développement, installez le kit de développement logiciel Modeling SDK pour Visual Studio.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Si [votre serveur de builds](/azure/devops/pipelines/agents/agents) s’exécute sur un ordinateur sur lequel Visual Studio n’est pas installé, copiez les fichiers suivants sur l’ordinateur de build à partir de votre ordinateur de développement :

- % ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\MSBuild\Microsoft\VisualStudio\v16.0\TextTemplating

  - Microsoft.VisualStudio.TextTemplating.Sdk.Host.15.0.dll
  - Microsoft.TextTemplating.Build.Tasks.dll
  - Microsoft.TextTemplating.targets

- % ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0

  - Microsoft.VisualStudio.TextTemplating.15.0.dll
  - Microsoft.VisualStudio.TextTemplating.Interfaces.15.0.dll
  - Microsoft.VisualStudio.TextTemplating.VSHost.15.0.dll

- % ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\IDE\PublicAssemblies

  - Microsoft.VisualStudio.TextTemplating.Modeling.15.0.dll

> [!TIP]
> Si vous recevez une `MissingMethodException` pour une méthode Microsoft. CodeAnalysis lors de l’exécution des cibles de génération TextTemplating sur un serveur de builds, assurez-vous que les assemblys Roslyn se trouvent dans un répertoire nommé *Roslyn* qui se trouve dans le même répertoire que l’exécutable de génération (par exemple, *msbuild.exe*).

## <a name="edit-the-project-file"></a>Modifier le fichier projet

Modifiez votre fichier projet pour configurer certaines fonctionnalités dans MSBuild, par exemple, pour importer les cibles de transformation de texte.

Dans **Explorateur de solutions**, choisissez **décharger** dans le menu contextuel de votre projet. Cela vous permet de modifier le fichier .csproj ou .vbproj dans l'éditeur XML. Lorsque vous avez terminé la modification, choisissez **recharger**.

## <a name="import-the-text-transformation-targets"></a>Importer les cibles de transformation de texte

Dans le fichier .vbproj ou .csproj, recherchez une ligne telle que :

`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`

\- ou -

`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`

Après cette ligne, insérez l'importation de modèles de texte :

::: moniker range=">=vs-2019"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets" />
```

::: moniker-end

::: moniker range="vs-2017"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets" />
```

::: moniker-end

## <a name="transform-templates-in-a-build"></a>Transformer des modèles dans une build

Il existe des propriétés que vous pouvez insérer dans votre fichier projet afin de contrôler la tâche de transformation :

- Exécutez la tâche de transformation au début de chaque génération :

    ```xml
    <PropertyGroup>
        <TransformOnBuild>true</TransformOnBuild>
    </PropertyGroup>
    ```

- Remplacer les fichiers en lecture seule, par exemple parce qu’ils ne sont pas extraits :

    ```xml
    <PropertyGroup>
        <OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>
    </PropertyGroup>
    ```

- Transformez chaque modèle à chaque fois :

    ```xml
    <PropertyGroup>
        <TransformOutOfDateOnly>false</TransformOutOfDateOnly>
    </PropertyGroup>
    ```

     Par défaut, la tâche de MSBuild T4 régénère un fichier de sortie s’il est antérieur à :

     - son fichier de modèle
     - tous les fichiers inclus
     - tous les fichiers qui ont été précédemment lus par le modèle ou par un processeur de directive qu’il utilise

     Il s’agit d’un test de dépendance plus puissant que celui utilisé par la commande **transformer tous les modèles** dans Visual Studio, qui compare uniquement les dates du modèle et du fichier de sortie.

Pour exécuter uniquement les transformations de texte dans votre projet, appelez la tâche TransformAll :

`msbuild myProject.csproj /t:TransformAll`

Pour transformer un modèle de texte spécifique :

`msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`

Vous pouvez utiliser des caractères génériques dans TransformFile :

`msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`

## <a name="source-control"></a>Contrôle de code source

Il n'existe aucune intégration prédéfinie spécifique avec un système de contrôle de code source. Toutefois, vous pouvez ajouter vos propres extensions, par exemple, pour extraire et archiver un fichier généré. Par défaut, la tâche de transformation de texte évite de remplacer un fichier marqué en lecture seule. Lorsqu’un tel fichier est trouvé, une erreur est consignée dans le Liste d’erreurs Visual Studio, et la tâche échoue.

Pour spécifier que les fichiers en lecture seule doivent être remplacés, insérez la propriété suivante :

`<OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>`

À moins que vous ne personnalisiez l’étape de post-traitement, un avertissement est consigné dans le Liste d’erreurs lors du remplacement d’un fichier.

## <a name="customize-the-build-process"></a>Personnaliser le processus de génération

La transformation de texte se produit avant les autres tâches du processus de génération. Pour définir les tâches appelées avant et après la transformation, définissez les propriétés `$(BeforeTransform)` et `$(AfterTransform)` :

```xml
<PropertyGroup>
    <BeforeTransform>CustomPreTransform</BeforeTransform>
    <AfterTransform>CustomPostTransform</AfterTransform>
</PropertyGroup>
<Target Name="CustomPreTransform">
    <Message Text="In CustomPreTransform..." Importance="High" />
</Target>
<Target Name="CustomPostTransform">
    <Message Text="In CustomPostTransform..." Importance="High" />
</Target>
```

Dans `AfterTransform`, vous pouvez référencer des listes de fichiers :

- GeneratedFiles : liste des fichiers écrits par le processus. Pour les fichiers qui ont remplacé des fichiers en lecture seule existants, `%(GeneratedFiles.ReadOnlyFileOverwritten)` a la valeur true. Ces fichiers peuvent être extraits du contrôle de code source.

- NonGeneratedFiles : liste des fichiers en lecture seule qui n'ont pas été remplacés.

Par exemple, vous définissez une tâche afin d'extraire GeneratedFiles.

## <a name="outputfilepath-and-outputfilename"></a>OutputFilePath et OutputFileName

Ces propriétés sont utilisées uniquement par MSBuild. Elles n'affectent pas la génération du code dans Visual Studio. Elles redirigent le fichier de sortie généré vers un autre dossier ou fichier. Le dossier cible doit déjà exister.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFilePath>MyFolder</OutputFilePath>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

Un dossier utile pour la redirection est `$(IntermediateOutputPath)` .

Si vous spécifiez un nom de fichier de sortie, il est prioritaire par rapport à l’extension spécifiée dans la directive de sortie des modèles.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFileName>MyOutputFileName.cs</OutputFileName>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

La spécification d’un OutputFileName ou d’un OutputFilePath n’est pas recommandée si vous transformez également des modèles dans Visual Studio à l’aide de l’option **transformer tout** ou de l’exécution du générateur de fichier unique. Vous obtiendrez des chemins d’accès de fichiers différents selon la façon dont vous avez déclenché la transformation. Ceci peut prêter à confusion.

## <a name="add-reference-and-include-paths"></a>Ajouter une référence et inclure des chemins

L’hôte possède un ensemble de chemins d’accès par défaut dans lesquels il recherche les assemblys référencés dans les modèles. Pour effectuer un ajout à cet ensemble :

```xml
<ItemGroup>
    <T4ReferencePath Include="$(VsIdePath)PublicAssemblies\" />
    <!-- Add more T4ReferencePath items here -->
</ItemGroup>
```

Pour définir les dossiers où rechercher les fichiers Include, fournissez une liste d'éléments délimités par des points-virgules. Généralement, vous effectuez l'ajout à la liste des dossiers existants.

```xml
<PropertyGroup>
    <IncludeFolders>
$(IncludeFolders);$(MSBuildProjectDirectory)\Include;AnotherFolder;And\Another</IncludeFolders>
</PropertyGroup>
```

## <a name="pass-build-context-data-into-the-templates"></a><a name="parameters"></a> Passer les données de contexte de build dans les modèles

Vous pouvez définir des valeurs de paramètre dans le fichier projet. Par exemple, vous pouvez passer des propriétés de [Build](../msbuild/msbuild-properties.md) et des [variables d’environnement](../msbuild/how-to-use-environment-variables-in-a-build.md):

```xml
<ItemGroup>
  <T4ParameterValues Include="ProjectFolder">
    <Value>$(ProjectDir)</Value>
    <Visible>false</Visible>
  </T4ParameterValues>
</ItemGroup>
```

Dans un modèle de texte, définissez `hostspecific` dans la directive de modèle. Utilisez la directive de [paramètre](../modeling/t4-parameter-directive.md) pour récupérer des valeurs :

```
<#@template language="c#" hostspecific="true"#>
<#@ parameter type="System.String" name="ProjectFolder" #>
The project folder is: <#= ProjectFolder #>
```

Dans un processeur de directive, vous pouvez appeler [ITextTemplatingEngineHost. ResolveParameterValue n'](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)):

```csharp
string value = Host.ResolveParameterValue("-", "-", "parameterName");
```

```vb
Dim value = Host.ResolveParameterValue("-", "-", "parameterName")
```

> [!NOTE]
> `ResolveParameterValue` Obtient les données à partir de `T4ParameterValues` uniquement lorsque vous utilisez MSBuild. Lorsque vous transformez le modèle à l’aide de Visual Studio, les paramètres ont des valeurs par défaut.

## <a name="use-project-properties-in-assembly-and-include-directives"></a><a name="msbuild"></a> Utiliser les propriétés de projet dans les directives d’assembly et include

Les macros Visual Studio telles que **$ (SolutionDir)** ne fonctionnent pas dans MSBuild. Vous pouvez utiliser des propriétés de projet à la place.

Modifiez votre fichier *. csproj* ou *. vbproj* pour définir une propriété de projet. Cet exemple définit une propriété nommée **myLibFolder**:

```xml
<!-- Define a project property, myLibFolder: -->
<PropertyGroup>
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myLibFolder">
      <Value>$(myLibFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

Désormais, vous pouvez utiliser votre propriété de projet dans les directives d'assembly et Include :

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
<#@ include file="$(myLibFolder)\MyIncludeFile.t4" #>
```

Ces directives obtiennent des valeurs à partir de T4parameterValues dans MSBuild et les hôtes Visual Studio.

## <a name="q--a"></a>Questions et réponses

**Pourquoi souhaite-t-il transformer des modèles dans le serveur de builds ? J’ai déjà transformé les modèles dans Visual Studio avant d’avoir archivé mon code.**

Si vous mettez à jour un fichier inclus ou un autre fichier lu par le modèle, Visual Studio ne transforme pas automatiquement le fichier. La transformation des modèles dans le cadre de la génération permet de s’assurer que tout est à jour.

**Quelles sont les autres options en matière de transformation de modèles de texte ?**

- L' [utilitaire TextTransform](../modeling/generating-files-with-the-texttransform-utility.md) peut être utilisé dans des scripts de commande. Dans la plupart des cas, il est plus facile d’utiliser MSBuild.

- [Appelle la transformation de texte dans une extension Visual Studio](../modeling/invoking-text-transformation-in-a-vs-extension.md).

- Les [modèles de texte au moment du design](../modeling/design-time-code-generation-by-using-t4-text-templates.md) sont transformés par Visual Studio.

- Les [modèles de texte au moment](../modeling/run-time-text-generation-with-t4-text-templates.md) de l’exécution sont transformés au moment de l’exécution dans votre application.

## <a name="see-also"></a>Voir aussi

::: moniker range="vs-2017"

- Il y a de bonnes recommandations dans le modèle de MSbuild T4 à l’adresse `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\msbuild\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets`

::: moniker-end

::: moniker range=">=vs-2019"

- Il y a de bonnes recommandations dans le modèle de MSbuild T4 à l’adresse `%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\msbuild\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets`

::: moniker-end

- [Écrire un modèle de texte T4](../modeling/writing-a-t4-text-template.md)
