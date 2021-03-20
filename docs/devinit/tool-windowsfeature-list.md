---
title: windowsfeature-list
description: devinit, outil WindowsFeature-List.
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
ms.openlocfilehash: 3225e67db734e02abce96820d44ca1515ddc348f
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672630"
---
# <a name="windowsfeature-list"></a>windowsfeature-list

> [!IMPORTANT]
> Depuis le 12 avril 2021, la connexion à GitHub Codespaces à partir de Visual Studio 2019 ne sera plus prise en charge et cette version préliminaire privée s’est terminée. Nous nous concentrons sur les expériences en constante évolution d’une boucle interne basée sur le Cloud et de solutions VDI optimisées pour un large éventail de charges de travail Visual Studio. Dans le cadre de cet article `devinit` , les outils associés ne seront plus disponibles. Nous vous encourageons à participer au Forum de la communauté des développeurs pour Visual Studio afin d’obtenir des informations sur les futures versions préliminaires et les informations de feuille de route.

L' `windowsfeature-list` outil est utilisé pour répertorier l’état d’activation/de désactivation de toutes les fonctionnalités de Windows.

| Nom                                             | Type   | Obligatoire | Valeur                                      |
|--------------------------------------------------|--------|----------|--------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.      |
| [**entrée**](#input)                              | string | Non       | Non utilisé. Ignoré.                         |
| [**additionalOptions**](#additional-options)     | string | Non       | Non utilisé. Ignoré.                         |

### <a name="input"></a>Entrée

Non utilisé. Ignoré.

#### <a name="additional-options"></a>Options supplémentaires

Non utilisé. Ignoré.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `windowsfeature-list` outil consiste à répertorier l’état d’activation/de désactivation de toutes les fonctionnalités de Windows.

## <a name="example-usage"></a>Exemple d’utilisation
Vous trouverez ci-dessous un exemple de la façon d’exécuter `windowsfeature-list` à l’aide d’un `.devinit.json` .

#### <a name="devinitjson-that-will-list-the-state-of-all-windows-features"></a>.devinit.js, qui répertorie l’état de toutes les fonctionnalités de Windows :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0.json",
    "run": [
        {
            "tool": "windowsfeature-list"
        }
    ]
}
```
