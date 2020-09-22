---
title: NPM-installer
description: devinit outil NPM-install.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 2af35ea0998b36fb5585feb4fa633f3ca538397e
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810136"
---
# <a name="npm-install"></a>NPM-installer

L' `npm-install` outil peut être utilisé pour installer des packages [NPM](https://www.npmjs.com/) .

## <a name="usage"></a>Usage

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil ne fait rien.

| Name                                             | Type   | Obligatoire | Valeur                                                                                                          |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                                                                          |
| [**entrée**](#input)                              | string | Oui      | Le package à installer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous.                                                 |
| [**additionalOptions**](#additional-options)     | string | Non       | Options supplémentaires à passer à l’outil. Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.       |

### <a name="input"></a>Entrée

La `input` propriété est utilisée pour spécifier le nom du package à installer (par exemple, 'Mongo').

### <a name="additional-options"></a>Options supplémentaires

Des options de configuration supplémentaires peuvent être transmises en tant que valeur de `additionalOptions` . Ces arguments sont directement dirigés vers les arguments utilisés par l' [installation de NPM](https://docs.npmjs.com/cli/install).

## <a name="example-usage"></a>Exemple d’utilisation

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will install the mongo NPM package (https://www.npmjs.com/package/mongo).",
            "tool": "npm-install",
            "input": "mongo",
        }
    ]
}
```
