---
title: dotnet-restore
description: outil devinit dotnet-Restore.
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
ms.openlocfilehash: 5beea84edce408acda7fc157f530c4a5f3253835
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672234"
---
# <a name="dotnet-restore"></a>dotnet-restore

> [!IMPORTANT]
> Depuis le 12 avril 2021, la connexion à GitHub Codespaces à partir de Visual Studio 2019 ne sera plus prise en charge et cette version préliminaire privée s’est terminée. Nous nous concentrons sur les expériences en constante évolution d’une boucle interne basée sur le Cloud et de solutions VDI optimisées pour un large éventail de charges de travail Visual Studio. Dans le cadre de cet article `devinit` , les outils associés ne seront plus disponibles. Nous vous encourageons à participer au Forum de la communauté des développeurs pour Visual Studio afin d’obtenir des informations sur les futures versions préliminaires et les informations de feuille de route.

Les `dotnet-restore` dépendances de restauration de l’outil et les outils spécifiques au projet qui sont spécifiés dans le fichier projet. En savoir plus sur dotnet restore [ici](/dotnet/core/tools/dotnet-restore).

## <a name="usage"></a>Utilisation

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                             | Type   | Obligatoire | Valeur                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                                                |
| [**entrée**](#input)                              | string | Non       | Chemin d’accès au fichier projet/solution à restaurer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous. |
| [**additionalOptions**](#additional-options)     | string | Non       | Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.                     |

### <a name="input"></a>Entrée

Chemin d’accès au fichier projet/solution à restaurer.

### <a name="additional-options"></a>Options supplémentaires

Des options supplémentaires sont passées en l’absence de la commande dotnet restore.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `dotnet-restore` outil est l’exécution `dotnet restore` dans le répertoire actif.

## <a name="example-usage"></a>Exemple d’utilisation
Vous trouverez ci-dessous un exemple de la façon d’exécuter `dotnet-restore` à l’aide d’un `.devinit.json` .

#### <a name="devinitjson-that-will-restore-dependencies-and-tools-of-a-project"></a>.devinit.jssur qui restaure les dépendances et les outils d’un projet :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "dotnet-restore",
            "input": "C:\\app1\\app1.csproj"
        }
    ]
}
```