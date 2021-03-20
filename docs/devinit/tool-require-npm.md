---
title: require-npm
description: l’outil devinit requiert-NPM.
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
ms.openlocfilehash: 93723ee50fd718c5abb7c86f0f3b986ed9832abd
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672295"
---
# <a name="require-npm"></a>require-npm

> [!IMPORTANT]
> Depuis le 12 avril 2021, la connexion à GitHub Codespaces à partir de Visual Studio 2019 ne sera plus prise en charge et cette version préliminaire privée s’est terminée. Nous nous concentrons sur les expériences en constante évolution d’une boucle interne basée sur le Cloud et de solutions VDI optimisées pour un large éventail de charges de travail Visual Studio. Dans le cadre de cet article `devinit` , les outils associés ne seront plus disponibles. Nous vous encourageons à participer au Forum de la communauté des développeurs pour Visual Studio afin d’obtenir des informations sur les futures versions préliminaires et les informations de feuille de route.

L' `require-npm` outil est utilisé pour installer [NPM](https://www.npmjs.com/).

## <a name="usage"></a>Utilisation

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                             | Type   | Obligatoire | Valeur                                                                                       |
|--------------------------------------------------|--------|----------|---------------------------------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                                                       |
| [**entrée**](#input)                              | string | Oui      | Spécifie la version de NPM. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous.                           |
| [**additionalOptions**](#additional-options)     | string | Non       | Non utilisé. Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.                  |

### <a name="input"></a>Entrée

La `input` propriété est utilisée pour spécifier la version de NPM.

### <a name="additional-options"></a>Options supplémentaires

Inutilisé.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `require-nodejs` outil consiste à installer la dernière version de LTS de NPM.

## <a name="example-usage"></a>Exemple d’utilisation
Vous trouverez ci-dessous des exemples d’exécution à `require-npm` l’aide d’un `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-lts-of-npm"></a>.devinit.jssur qui installe le LTS de NPM :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-npm"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-npm"></a>.devinit.jssur qui installe une version spécifique de NPM :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-npm",
            "input": "6.14.6"
        }
    ]
}
```