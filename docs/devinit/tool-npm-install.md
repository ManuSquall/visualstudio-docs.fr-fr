---
title: npm-install
description: devinit outil NPM-install.
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
ms.openlocfilehash: 21630f5dbc80294547be33ab4a82bdf286a0b08f
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671905"
---
# <a name="npm-install"></a>npm-install

L' `npm-install` outil peut être utilisé pour installer des packages [NPM](https://www.npmjs.com/) .

## <a name="usage"></a>Utilisation

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil ne fait rien.

| Nom                                             | Type   | Obligatoire | Valeur                                                                                                          |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------------------------------------------|
| **commentaires**                                     | string | No       | Propriété de commentaires facultative. Non utilisé.                                                                          |
| [**entrée**](#input)                              | string | Oui      | Le package à installer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous.                                                 |
| [**additionalOptions**](#additional-options)     | string | No       | Options supplémentaires à passer à l’outil. Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.       |

### <a name="input"></a>Entrée

La `input` propriété est utilisée pour spécifier le nom du package à installer (par exemple, 'Mongo').

### <a name="additional-options"></a>Options supplémentaires

Des options de configuration supplémentaires peuvent être transmises en tant que valeur de `additionalOptions` . Ces arguments sont directement dirigés vers les arguments utilisés par l' [installation de NPM](https://docs.npmjs.com/cli/install).

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
