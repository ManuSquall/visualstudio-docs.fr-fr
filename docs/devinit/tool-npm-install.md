---
title: npm-install
description: devinit outil NPM-install.
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
ms.openlocfilehash: 011364e851670362ecaa9f4bdbfff965782ed706
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671622"
---
# <a name="npm-install"></a>npm-install

> [!IMPORTANT]
> Depuis le 12 avril 2021, la connexion à GitHub Codespaces à partir de Visual Studio 2019 ne sera plus prise en charge et cette version préliminaire privée s’est terminée. Nous nous concentrons sur les expériences en constante évolution d’une boucle interne basée sur le Cloud et de solutions VDI optimisées pour un large éventail de charges de travail Visual Studio. Dans le cadre de cet article `devinit` , les outils associés ne seront plus disponibles. Nous vous encourageons à participer au Forum de la communauté des développeurs pour Visual Studio afin d’obtenir des informations sur les futures versions préliminaires et les informations de feuille de route.

L' `npm-install` outil peut être utilisé pour installer des packages [NPM](https://www.npmjs.com/) .

## <a name="usage"></a>Utilisation

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil ne fait rien.

| Nom                                             | Type   | Obligatoire | Valeur                                                                                                          |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                                                                          |
| [**entrée**](#input)                              | string | Non       | Le package à installer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous.                                                 |
| [**additionalOptions**](#additional-options)     | string | Non       | Options supplémentaires à passer à l’outil. Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.       |

### <a name="input"></a>Entrée

La `input` propriété est utilisée pour spécifier le nom du package à installer (par exemple, 'Mongo').

### <a name="additional-options"></a>Options supplémentaires

Des options de configuration supplémentaires peuvent être transmises en tant que valeur de `additionalOptions` . Ces arguments sont directement dirigés vers les arguments utilisés par l' [installation de NPM](https://docs.npmjs.com/cli/install).

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `npm-install` outil consiste à exécuter `npm install` sans arguments. Pour obtenir une description de ce comportement, consultez [la documentation de NPM](https://docs.npmjs.com/cli/v6/commands/npm-install) .

## <a name="example-usage"></a>Exemple d’utilisation
Vous trouverez ci-dessous un exemple de la façon d’exécuter `npm-install` à l’aide d’un `.devinit.json` .

#### <a name="devinitjson-that-will-install-mongo"></a>.devinit.jssur qui installe Mongo :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "npm-install",
            "input": "mongo",
        }
    ]
}
```
