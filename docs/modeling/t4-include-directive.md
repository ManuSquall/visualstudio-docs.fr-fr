---
title: Directive d'inclusion T4
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a3ab6aa4cd116c779cac4367d1eeb9a187edaeb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62964090"
---
# <a name="t4-include-directive"></a>Directive d'inclusion T4

Dans un modèle de texte dans Visual Studio, vous pouvez inclure le texte à partir d’un autre fichier à l’aide un `<#@include#>` directive. Vous pouvez placer les directives `include` n'importe où dans un modèle de texte avant le premier bloc de fonctionnalité de classe `<#+ ... #>`. Les fichiers inclus peuvent également contenir des directives `include` et d'autres directives. Cela vous permet de partager du code de modèle et du texte réutilisable entre les modèles.

## <a name="using-include-directives"></a>Utilisation de directives Include

```
<#@ include file="filePath" [once="true"] #>
```

- `filePath` peut être absolu ou relatif au fichier modèle actuel.

   En outre, les extensions spécifiques de Visual Studio peuvent spécifier leurs propres répertoires dans lesquels rechercher des fichiers include. Par exemple, lorsque vous avez installé la visualisation et le SDK de modélisation (outils DSL), le dossier suivant est ajouté à la liste d’inclusion : `Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates`.

   Ces dossiers d'inclusion supplémentaires peuvent dépendre de l'extension du fichier d'inclusion. Par exemple, le dossier d’inclusion des outils DSL est uniquement accessible aux fichiers d’inclusion ayant l’extension de fichier `.tt`

- `filePath` peut inclure des variables d'environnement délimitées par "%". Exemple :

  ```
  <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>
  ```

- Le nom d’un fichier inclus n’a pas à utiliser l’extension `".tt"`.

   Vous pouvez utiliser une autre extension telle que `".t4"` pour les fichiers inclus. C’est pourquoi, lorsque vous ajoutez un `.tt` fichier à un projet, Visual Studio définit automatiquement son **un outil personnalisé** propriété `TextTemplatingFileGenerator`. En général, vous ne souhaitez pas que les fichiers inclus soient transformés individuellement.

   D'un autre côté, vous devez savoir que dans certains cas, l'extension de fichier affecte les dossiers supplémentaires dans lesquels seront recherchés les fichiers Include. Cela peut être important lorsque vous possédez un fichier inclus qui contient d'autres fichiers.

- Le contenu inclus est traité presque comme s'il faisait partie du modèle de texte d'inclusion. Toutefois, vous pouvez inclure un fichier qui contient un bloc de fonctionnalité de classe `<#+...#>` même si la directive `include` est suivie de texte ordinaire et de blocs de contrôle standard.

- Utilisez `once="true"` pour vous assurer qu’un modèle est inclus qu’une seule fois, même si elle est appelée à partir de plusieurs autres fichiers include.

   Cela rend fonctionnalité facilement générer une bibliothèque d’extraits de code T4 réutilisables que vous pouvez inclure à sera sans se préoccuper de qui certains autres extrait de code a déjà incluses.  Par exemple, supposons que vous avez une bibliothèque d’extraits de code très précis qui traitent de traitement du modèle et de génération de c#.  À son tour, ils sont utilisés par certains utilitaires plus spécifiques aux tâches telles que la génération d’exceptions, qui vous permet ensuite à partir de n’importe quel modèle plus spécifiques à l’application. Si vous dessinez le graphique de dépendance, vous constatez que certains extraits de code sont inclus plusieurs fois. Mais le paramètre `once` empêche les inclusions suivantes.

  **MyTextTemplate.tt :**

```
<#@ output extension=".txt" #>
Output message 1 (from top template).
<#@ include file="TextFile1.t4"#>
Output message 5 (from top template).
<#
   GenerateMessage(6); // defined in TextFile1.t4
   AnotherGenerateMessage(7); // defined in TextFile2.t4
#>
```

 **TextFile1.t4 :**

```
   Output Message 2 (from included file).
<#@ include file="TextFile2.t4" #>
   Output Message 4 (from included file).
<#+ // Start of class feature control block.
void GenerateMessage(int n)
{
#>
   Output Message <#= n #> (from GenerateMessage method).
<#+
}
#>
```

 **TextFile2.t4:**

```
        Output Message 3 (from included file 2).
<#+ // Start of class feature control block.
void AnotherGenerateMessage(int n)
{
#>
       Output Message <#= n #> (from AnotherGenerateMessage method).
<#+
}
#>
```

 **Le fichier généré résultant, MyTextTemplate.txt :**

```
Output message 1 (from top template).
   Output Message 2 (from included file).
        Output Message 3 (from included file 2).

   Output Message 4 (from included file).

Output message 5 (from top template).
   Output Message 6 (from GenerateMessage method).
       Output Message 7 (from AnotherGenerateMessage method).
```

## <a name="msbuild"></a> À l’aide des propriétés du projet dans MSBuild et Visual Studio
 Bien que vous pouvez utiliser des macros de Visual Studio telles que $ (SolutionDir) dans une directive include, elles ne fonctionnent pas dans MSBuild. Si vous souhaitez transformer les modèles de votre ordinateur de build, vous devez utiliser les propriétés de projet à la place.

 Modifiez votre fichier projet .csproj ou .vbproj pour définir une propriété de projet. Cet exemple définit une propriété nommée `myIncludeFolder` :

```xml
<!-- Define a project property, myIncludeFolder: -->
<PropertyGroup>
    <myIncludeFolder>$(MSBuildProjectDirectory)\..\libs</myIncludeFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myIncludeFolder">
      <Value>$(myIncludeFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

 Maintenant, vous pouvez utiliser votre propriété de projet dans les modèles de texte, lesquels se transforment correctement dans Visual Studio et MSBuild :

```
<#@ include file="$(myIncludeFolder)\defs.tt" #>
```
