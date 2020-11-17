---
title: require-npm
description: l’outil devinit requiert-NPM.
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
ms.openlocfilehash: e28a1f896904c89a4553f18c73324293ea468ee6
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672124"
---
# <a name="require-npm"></a>require-npm

L' `require-npm` outil est utilisé pour installer [NPM](https://www.npmjs.com/).

## <a name="usage"></a>Utilisation

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                             | Type   | Obligatoire | Valeur                                                                                       |
|--------------------------------------------------|--------|----------|---------------------------------------------------------------------------------------------|
| **commentaires**                                     | string | No       | Propriété de commentaires facultative. Non utilisé.                                                       |
| [**entrée**](#input)                              | string | Oui      | Spécifie la version de NPM. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous.                           |
| [**additionalOptions**](#additional-options)     | string | No       | Non utilisé. Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.                  |

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