---
title: Directive d'assembly T4
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: cd7f1f36374f3411b5a76f5df5e3e25bb52df230
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948634"
---
# <a name="t4-assembly-directive"></a>Directive d'assembly T4

Dans un modèle de texte au moment du design de Visual Studio, le `assembly` directive charge un assembly afin que votre code de modèle puisse utiliser ses types. L’effet est similaire à l’ajout d’une référence d’assembly dans un projet Visual Studio.

 Pour obtenir une vue d’ensemble de l’écriture de modèles de texte, consultez [écriture d’un modèle de texte T4](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
>  Vous n'avez pas besoin de la directive `assembly` dans un modèle de texte au moment de l'exécution (prétraité). Au lieu de cela, ajoutez les assemblys nécessaires à la **références** de votre projet Visual Studio.

## <a name="using-the-assembly-directive"></a>Utilisation de la directive d'assembly
 La syntaxe de la directive est la suivante :

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

 Le nom d'assembly doit correspondre à l'un des éléments suivants :

- Nom fort d'un assembly dans le GAC, tel que `System.Xml.dll`. Vous pouvez également utiliser la forme longue, telle que `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"`. Pour plus d'informations, consultez <xref:System.Reflection.AssemblyName>.

- Chemin d’accès absolu de l’assembly

  Vous pouvez utiliser la `$(variableName)` la syntaxe pour référencer des variables de Visual Studio comme `$(SolutionDir)`, et `%VariableName%` aux variables d’environnement de référence. Exemple :

```
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>
```

 La directive assembly n'a aucun effet dans un modèle de texte prétraité. Au lieu de cela, incluez les références nécessaires dans le **références** section de votre projet Visual Studio. Pour plus d’informations, consultez [génération de texte d’exécution avec les modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="standard-assemblies"></a>Assemblys standard
 Les assemblys suivants sont chargés automatiquement, afin que vous n'ayez pas besoin d'écrire des directives d'assembly pour eux :

- `Microsoft.VisualStudio.TextTemplating.1*.dll`

- `System.dll`

- `WindowsBase.dll`

  Si vous utilisez une directive personnalisée, le processeur de directive peut charger des assemblys supplémentaires. Par exemple, si vous écrivez des modèles pour un langage spécifique à un domaine (DSL), vous n’avez pas besoin d’écrire des directives d’assembly pour les assemblys suivants :

- `Microsoft.VisualStudio.Modeling.Sdk.1*.dll`

- `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.1*.dsl`

- `Microsoft.VisualStudio.TextTemplating.Modeling.1*.dll`

- Assembly contenant votre DSL.

## <a name="msbuild"></a> À l’aide des propriétés du projet dans MSBuild et Visual Studio
 Visual Studio macros telles que $ (SolutionDir) ne fonctionnent pas dans MSBuild. Si vous souhaitez transformer les modèles de votre ordinateur de build, vous devez utiliser les propriétés de projet à la place.

 Modifiez votre fichier projet .csproj ou .vbproj pour définir une propriété de projet. Cet exemple définit une propriété nommée `myLibFolder` :

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

 Maintenant, vous pouvez utiliser votre propriété de projet dans les modèles de texte, lesquels se transforment correctement dans Visual Studio et MSBuild :

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
```

## <a name="see-also"></a>Voir aussi

- [Directive d’inclusion T4](../modeling/t4-include-directive.md)