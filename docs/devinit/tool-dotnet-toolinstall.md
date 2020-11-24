---
title: dotnet-toolinstall
description: outil devinit dotnet-toolinstall.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 343c66a0f1da955479993502cf5dcf967abe03b9
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440401"
---
# <a name="dotnet-toolinstall"></a>dotnet-toolinstall

L' `dotnet-toolinstall` outil est utilisé pour installer les [outils .net Core](https://dotnet.microsoft.com/) à l’aide de la `dotnet tool update` commande.

## <a name="usage"></a>Usage

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                             | Type   | Obligatoire | Valeur                                                                 |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                                 |
| [**entrée**](#input)                              | string | Oui      | Outil .NET Core à installer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous. |
| [**additionalOptions**](#additional-options)     | string | Non       | Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.      |

### <a name="input"></a>Entrée

La `input` propriété est utilisée pour spécifier l’outil .net core à installer. Il existe une liste non officielle d’outils à l’adresse [https://github.com/natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) .

### <a name="additional-options"></a>Options supplémentaires

Des options de configuration supplémentaires peuvent être transmises en tant que valeur de `additionalOptions` . Ces arguments sont un relais direct vers les arguments utilisés par la [`dotnet tool update`](/dotnet/core/tools/global-tools#update-a-tool) commande.

La `dotnet tool update` commande est utilisée pour gérer en toute sécurité le cas où un outil est déjà installé.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `dotnet-toolinstall` outil est l’erreur telle qu’elle est `input` requise.

## <a name="example-usage"></a>Exemple d’utilisation
Vous trouverez ci-dessous des exemples d’exécution à `dotnet-toolinstall` l’aide d’un `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-dotnet-trace-tool"></a>.devinit.jssur qui installe l’outil dotnet-trace :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-trace"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-dotnet-trace-tool-as-a-global-tool"></a>.devinit.jssur qui installe l’outil dotnet-trace en tant qu’outil Global :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-trace",
            "additionalOptions": "--global"
        }
    ]
}
```