---
title: windowsfeature-list
description: devinit, outil WindowsFeature-List.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 07b92e8783393fa19e5c09344a396a6c5c4fc011
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442125"
---
# <a name="windowsfeature-list"></a>windowsfeature-list

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
