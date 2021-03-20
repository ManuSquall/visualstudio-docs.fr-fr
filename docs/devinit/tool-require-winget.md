---
title: require-Winget
description: l’outil devinit requiert-winget.
ms.date: 02/08/2021
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 6c9f72eb1ae66fbaa4376716fcd140b92502cd5e
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672665"
---
# <a name="require-winget"></a>require-Winget

> [!IMPORTANT]
> Depuis le 12 avril 2021, la connexion à GitHub Codespaces à partir de Visual Studio 2019 ne sera plus prise en charge et cette version préliminaire privée s’est terminée. Nous nous concentrons sur les expériences en constante évolution d’une boucle interne basée sur le Cloud et de solutions VDI optimisées pour un large éventail de charges de travail Visual Studio. Dans le cadre de cet article `devinit` , les outils associés ne seront plus disponibles. Nous vous encourageons à participer au Forum de la communauté des développeurs pour Visual Studio afin d’obtenir des informations sur les futures versions préliminaires et les informations de feuille de route.

L' `require-winget` outil est utilisé pour installer [Winget](https://docs.microsoft.com/windows/package-manager/winget/). 
## <a name="usage"></a>Utilisation

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                             | Type   | Obligatoire | Valeur                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                                                |
| [**entrée**](#input)                              | string | Non       | Non utilisé.                                                                            |
| [**additionalOptions**](#additional-options)     | string | Non       | Non utilisé.                                                                            |

### <a name="input"></a>Entrée

Non utilisé.

### <a name="additional-options"></a>Options supplémentaires

Non utilisé.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `require-winget` outil consiste à installer la dernière version à l’aide du [ `winget-cli` référentiel git](https://github.com/microsoft/winget-cli).

## <a name="example-usage"></a>Exemple d’utilisation

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-6.0",
    "comments": "Example that installs the latest version of winget",
    "run": [
        {
            "tool": "require-winget",
            "comments": "Installs winget",
        }
    ]
}
```
