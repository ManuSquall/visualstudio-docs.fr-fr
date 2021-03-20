---
title: require-choco
description: l’outil devinit requiert-Choco.
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
ms.openlocfilehash: 5ffd726133128e551ba9bec8c9288d43b7c9a5b6
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672097"
---
# <a name="require-choco"></a>require-choco

> [!IMPORTANT]
> Depuis le 12 avril 2021, la connexion à GitHub Codespaces à partir de Visual Studio 2019 ne sera plus prise en charge et cette version préliminaire privée s’est terminée. Nous nous concentrons sur les expériences en constante évolution d’une boucle interne basée sur le Cloud et de solutions VDI optimisées pour un large éventail de charges de travail Visual Studio. Dans le cadre de cet article `devinit` , les outils associés ne seront plus disponibles. Nous vous encourageons à participer au Forum de la communauté des développeurs pour Visual Studio afin d’obtenir des informations sur les futures versions préliminaires et les informations de feuille de route.

L' `require-choco` outil peut être utilisé pour installer le [chocolat](https://chocolatey.org/).

## <a name="usage"></a>Utilisation

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                             | Type   | Obligatoire | Valeur                                                                      |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                                      |
| [**entrée**](#input)                              | string | Non       | Non utilisé. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous.                           |
| [**additionalOptions**](#additional-options)     | string | Non       | Non utilisé. Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous. |

### <a name="input"></a>Entrée

Non utilisé.

### <a name="additional-options"></a>Options supplémentaires

Non utilisé.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `require-choco` outil consiste à installer le chocolat et à l’ajouter au `PATH` .

## <a name="example-usage"></a>Exemple d’utilisation
Vous trouverez ci-dessous un exemple de la façon d’exécuter `require-choco` à l’aide d’un `.devinit.json` .

#### <a name="devinitjson-that-will-install-chocolatey"></a>.devinit.jssur qui installe le chocolat :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-choco"
        }
    ]
}
```