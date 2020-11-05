---
title: require-dotnetcoresdk
description: l’outil devinit requiert-dotnetcoresdk.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 5c5b68b663d6ee4cd0294aa77bd89c2e778f8d2b
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399605"
---
# <a name="require-dotnetcoresdk"></a>require-dotnetcoresdk

L' `require-dotnetcoresdk` outil est utilisé pour installer le [Kit SDK .net Core](https://dotnet.microsoft.com/) et le runtime partagé via le script [dotnet-install](/dotnet/core/tools/dotnet-install-script) .

## <a name="usage"></a>Usage

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

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of installing latest or, if present, the SDK version from a global.json file.",
            "tool": "require-dotnetcoresdk"
        },
        {
            "comments": "Example that will install a specific version.",
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0"
        },
        {
            "comments": "Example that will install a specific version and the aspnetcore runtime.",
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0",
            "additionalOptions": "-Runtime aspnetcore"
        },
        {
            "comments": "Example that will install in a specific directory.",
            "tool": "require-dotnetcoresdk",
            "additionalOptions": "-InstallDir \"C:\\Program Files\\dotnet\""
        }
    ]
}
```