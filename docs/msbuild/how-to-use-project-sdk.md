---
title: Guide pratique pour référencer un kit SDK de projet MSBuild | Microsoft Docs
ms.date: 01/25/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74ccc29417cdee7a9f93c39509c0f7d06a5c72ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76826469"
---
# <a name="how-to-use-msbuild-project-sdks"></a>Guide pratique pour utiliser les kits SDK de projet MSBuild

MSBuild 15,0 a introduit le concept de « kit de développement logiciel (SDK) de projet », qui simplifie l’utilisation de kits de développement de logiciels qui nécessitent l’importation de propriétés et de cibles.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```

Pendant l’évaluation du projet, MSBuild ajoute des importations implicites en haut et en bas du fichier projet :

```xml
<Project>
    <!-- Implicit top import -->
    <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>

    <!-- Implicit bottom import -->
    <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

## <a name="reference-a-project-sdk"></a>Référencer un kit SDK de projet

Il existe trois manières de référencer un kit SDK de projet :

- Utilisez l'attribut `Sdk` sur l'élément `<Project/>` :

    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```

    Une importation implicite est ajoutée au début et à la fin du projet, comme indiqué précédemment.
    
    Pour spécifier une version spécifique du kit de développement logiciel (SDK), ajoutez-la à l' `Sdk` attribut :

    ```xml
    <Project Sdk="My.Custom.Sdk/1.2.3">
        ...
    </Project>
    ```

    > [!NOTE]
    > C’est actuellement le seul moyen possible de faire référence à un kit SDK de projet dans Visual Studio pour Mac.

- Utilisez l'élément `<Sdk/>` de niveau supérieur :

    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```

   Une importation implicite est ajoutée au début et à la fin du projet, comme indiqué précédemment.
   
   L'attribut `Version` n'est pas requis.

- Utilisez l’élément `<Import/>` à un endroit quelconque de votre projet :

    ```xml
    <Project>
        <PropertyGroup>
            <MyProperty>Value</MyProperty>
        </PropertyGroup>
        <Import Project="Sdk.props" Sdk="My.Custom.Sdk" />
        ...
        <Import Project="Sdk.targets" Sdk="My.Custom.Sdk" />
    </Project>
   ```

   L’inclusion explicite des importations dans votre projet vous permet d’avoir un contrôle total de l’ordre.

   Quand vous utilisez l’élément `<Import/>`, vous pouvez également spécifier un attribut `Version` facultatif. Par exemple, vous pouvez spécifier `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />`.

## <a name="how-project-sdks-are-resolved"></a>Méthode de résolution des kits SDK de projet

Lors de l’évaluation de l’importation, MSBuild résout dynamiquement le chemin d’accès au kit de développement logiciel (SDK) du projet en fonction du nom et de la version que vous avez spécifiés.  MSBuild dispose également d’une liste de programmes de résolution du kit de développement logiciel (SDK) inscrits, qui sont des plug-ins qui localisent les Kits SDK de projet sur votre ordinateur. Ces plug-ins sont les suivants :

- Un programme de résolution basé sur NuGet qui interroge vos flux de packages configurés pour localiser les packages NuGet qui correspondent à l’ID et à la version du kit SDK que vous avez spécifié.

   Ce programme de résolution n’est actif que si vous avez spécifié une version facultative. Il peut être utilisé pour n’importe quel kit de développement logiciel (SDK) de projet personnalisé.
   
- Un programme de résolution de l’interface CLI .NET qui résout les kits de développement logiciel installés avec l' [interface CLI .net](/dotnet/core/tools/).

   Ce programme de résolution localise les kits de développement logiciel (SDK) de projet tels que `Microsoft.NET.Sdk` et `Microsoft.NET.Sdk.Web` qui font partie du produit.
   
- Un programme de résolution par défaut qui résout les kits SDK installés avec MSBuild.

Le programme de résolution du SDK NuGet prend en charge la spécification d’une version dans le [global.jssur](/dotnet/core/tools/global-json) le fichier, ce qui vous permet de contrôler la version du SDK Project dans un emplacement plutôt que dans chaque projet individuel :

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```

Seule une version de chaque kit SDK de projet peut être utilisée durant une build. Si vous référencez deux versions différentes du même Kit de développement logiciel (SDK) de projet, MSBuild émet un avertissement. Il est recommandé de **ne pas** spécifier de version dans vos projets si une version est spécifiée dans le *global.jssur* le fichier.

## <a name="see-also"></a>Voir aussi

- [Concepts MSBuild](../msbuild/msbuild-concepts.md)
- [Personnaliser votre build](../msbuild/customize-your-build.md)
- [Packages, métadonnées et frameworks](/dotnet/core/packages)
- [Ajouts au format csproj pour .NET Core](/dotnet/core/tools/csproj)
