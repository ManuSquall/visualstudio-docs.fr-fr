---
title: require-dotnetcoresdk
description: l’outil devinit requiert-dotnetcoresdk.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 1963ad8dfe1bd31eb3f98ec6fdf57524a274cfb6
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671790"
---
# <a name="require-dotnetcoresdk"></a>require-dotnetcoresdk

> [!IMPORTANT]
> Depuis le 12 avril 2021, la connexion à GitHub Codespaces à partir de Visual Studio 2019 ne sera plus prise en charge et cette version préliminaire privée s’est terminée. Nous nous concentrons sur les expériences en constante évolution d’une boucle interne basée sur le Cloud et de solutions VDI optimisées pour un large éventail de charges de travail Visual Studio. Dans le cadre de cet article `devinit` , les outils associés ne seront plus disponibles. Nous vous encourageons à participer au Forum de la communauté des développeurs pour Visual Studio afin d’obtenir des informations sur les futures versions préliminaires et les informations de feuille de route.

L' `require-dotnetcoresdk` outil est utilisé pour installer le [Kit SDK .net Core](https://dotnet.microsoft.com/) et le runtime partagé via le script [dotnet-install](/dotnet/core/tools/dotnet-install-script) .

## <a name="usage"></a>Utilisation

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                             | Type   | Obligatoire | Valeur                                                                               |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                                               |
| [**entrée**](#input)                              | string | Non       | Version de la kit SDK .NET Core à installer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous. |
| [**additionalOptions**](#additional-options)     | string | Non       | Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.                    |

### <a name="input"></a>Entrée

La `input` propriété est utilisée pour spécifier la version de kit SDK .net core à installer. Une liste de versions est disponible sur le [site DotNet-Core](https://dotnet.microsoft.com/download/dotnet-core).

### <a name="additional-options"></a>Options supplémentaires

Des options de configuration supplémentaires peuvent être transmises en tant que valeur de `additionalOptions` . Ces arguments sont un relais direct vers les arguments utilisés dans le script [dotnet-install](/dotnet/core/tools/dotnet-install-script) . Pour plus d’informations sur les paramètres disponibles, consultez la [documentation](/dotnet/core/tools/dotnet-install-script) du script [dotnet-install](/dotnet/core/tools/dotnet-install-script) . Lorsque vous utilisez, assurez-vous `additionalOptions` d’utiliser les noms et le format des arguments PowerShell.

> [!NOTE]
> Toute valeur supplémentaire à un argument qui inclut un espace doit inclure une paire supplémentaire de guillemets d’échappement (à l’aide de la barre oblique inverse). Vous pouvez voir un exemple d' [utilisation](#example-usage) à l’aide de `-InstallDir` .

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `require-dotnetcoresdk` outil consiste à installer la version de la kit SDK .net Core spécifiée dans un `global.json` fichier [(de documentation)](/dotnet/core/tools/global-json?tabs=netcore3x) dans le répertoire de travail actuel. Si aucun `global.json` fichier n’est trouvé, `require-dotnetcoresdk` installe la dernière version actuelle du kit SDK .net Core et du runtime partagé.

## <a name="example-usage"></a>Exemple d’utilisation
Vous trouverez ci-dessous des exemples d’exécution à `require-dotnetcoresdk` l’aide d’un `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-latest-version-of-net-core"></a>.devinit.jssur qui installe la dernière version de .NET Core :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetcoresdk"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-net-core"></a>.devinit.jssur qui installe une version spécifique de .NET Core :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-net-core-and-aspnet-core"></a>.devinit.jssur qui installe une version spécifique de .NET Core et ASP.NET Core :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0",
            "additionalOptions": "-Runtime aspnetcore"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-net-core-in-a-specific-directory"></a>.devinit.jssur qui installe .NET Core dans un répertoire spécifique :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetcoresdk",
            "additionalOptions": "-InstallDir \"C:\\Program Files\\dotnet\""
        }
    ]
}
```