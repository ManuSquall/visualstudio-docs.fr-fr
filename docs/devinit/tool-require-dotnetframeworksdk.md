---
title: require-dotnetframeworksdk
description: l’outil devinit requiert-dotnetframeworksdk.
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
ms.openlocfilehash: 42bcb44704c0273c936a763661ec78d232fe7a82
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400273"
---
# <a name="require-dotnetframeworksdk"></a>require-dotnetframeworksdk

L' `require-dotnetframeworksdk` outil est utilisé pour installer le [Kit de développement logiciel (SDK) .NET Framework](https://dotnet.microsoft.com/) par le biais des [programmes d’installation fournis](https://dotnet.microsoft.com/download/visual-studio-sdks).

## <a name="usage"></a>Usage

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                             | Type   | Obligatoire  | Valeur                                                                                    |
|--------------------------------------------------|--------|-----------|------------------------------------------------------------------------------------------|
| **commentaires**                                     | string | Non        | Propriété de commentaires facultative. Non utilisé.                                                    |
| [**entrée**](#input)                              | string | Non        | Version du kit de développement logiciel (SDK) .NET Framework à installer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous. |
| [**additionalOptions**](#additional-options)     | string | Non        | Non utilisé. Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.               |

### <a name="input"></a>Entrée

La `input` propriété est utilisée pour spécifier la version du kit de développement logiciel (SDK) .NET Framework à installer. Une liste de versions est disponible sur le [site DotNet-Framework](https://dotnet.microsoft.com/download/visual-studio-sdks).

### <a name="additional-options"></a>Options supplémentaires

Non utilisé.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `require-dotnetframeworksdk` outil consiste à installer la dernière version. Consultez les [programmes d’installation fournis](https://dotnet.microsoft.com/download/visual-studio-sdks) pour la version la plus récente.

## <a name="example-usage"></a>Exemple d’utilisation

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "comments": "Example that will install a specific version of the .NET Framework SDK.",
            "tool": "require-dotnetframeworksdk",
            "input": "4.8.0"
        },
        {
            "comments": "Example that will install the latest version of the .NET Framework SDK.",
            "tool": "require-dotnetframeworksdk"
        }
    ]
}
```
