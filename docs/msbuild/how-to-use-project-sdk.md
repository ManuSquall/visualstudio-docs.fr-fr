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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76826469"
---
# <a name="how-to-use-msbuild-project-sdks"></a>Guide pratique pour utiliser les kits SDK de projet MSBuild

MSBuild 15.0 a introduit le concept du « projet SDK », qui simplifie à l’aide de kits de développement logiciel qui nécessitent l’importation de propriétés et de cibles.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```

Lors de l’évaluation du projet, MSBuild ajoute des importations implicites en haut et en bas du dossier du projet :

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

    Une importation implicite est ajoutée au haut et au bas du projet comme nous l’avons déjà vu.
    
    Pour spécifier une version spécifique du SDK, l’appendice à l’attribut `Sdk` :

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

   Une importation implicite est ajoutée au haut et au bas du projet comme nous l’avons déjà vu.
   
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

Lors de l’évaluation de l’importation, MSBuild résout dynamiquement le chemin vers le projet SDK en fonction du nom et de la version que vous avez spécifié.  MSBuild dispose également d’une liste de résolveurs SDK enregistrés, qui sont des plug-ins qui localisent les SDK du projet sur votre machine. Ces plug-ins sont les suivants :

- Un programme de résolution basé sur NuGet qui interroge vos flux de packages configurés pour localiser les packages NuGet qui correspondent à l’ID et à la version du kit SDK que vous avez spécifié.

   Ce résolveur n’est actif que si vous avez spécifié une version facultative. Il peut être utilisé pour n’importe quel projet personnalisé SDK.
   
- Un résolveur CLI .NET qui résout les SDK qui sont installés avec [.NET CLI](/dotnet/core/tools/).

   Ce résolveur localise le projet `Microsoft.NET.Sdk` SDKs tels que et `Microsoft.NET.Sdk.Web` qui font partie du produit.
   
- Un programme de résolution par défaut qui résout les kits SDK installés avec MSBuild.

Le résolveur SDK basé à NuGet prend en charge la spécifier une version dans le fichier [global.json,](/dotnet/core/tools/global-json) qui vous permet de contrôler la version SDK du projet en un seul endroit plutôt que dans chaque projet individuel :

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```

Seule une version de chaque kit SDK de projet peut être utilisée durant une build. Si vous faites référence à deux versions différentes du même projet SDK, MSBuild émet un avertissement. Il est recommandé de **ne pas** spécifier une version dans vos projets si une version est spécifiée dans le fichier *global.json.*

## <a name="see-also"></a>Voir aussi

- [Concepts MSBuild](../msbuild/msbuild-concepts.md)
- [Personnaliser votre build](../msbuild/customize-your-build.md)
- [Packages, métadonnées et frameworks](/dotnet/core/packages)
- [Ajouts au format csproj pour .NET Core](/dotnet/core/tools/csproj)
