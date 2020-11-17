---
title: windowsfeature-list
description: devinit, outil WindowsFeature-List.
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
ms.openlocfilehash: b521009affbc1db81676481e33640a69e619aaf3
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671711"
---
# <a name="windowsfeature-list"></a>windowsfeature-list

L' `windowsfeature-list` outil est utilisé pour répertorier l’état d’activation/de désactivation de toutes les fonctionnalités de Windows.

| Nom                                             | Type   | Obligatoire | Valeur                                      |
|--------------------------------------------------|--------|----------|--------------------------------------------|
| **commentaires**                                     | string | No       | Propriété de commentaires facultative. Non utilisé.      |
| [**entrée**](#input)                              | string | No       | Non utilisé. Ignoré.                         |
| [**additionalOptions**](#additional-options)     | string | No       | Non utilisé. Ignoré.                         |

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
