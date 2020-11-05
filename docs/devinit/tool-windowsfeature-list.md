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
ms.openlocfilehash: 3030ddaaa3cc19b8719b067d9bd5e3572957b84f
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400197"
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

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0.json",
    "run": [
        {
            "comments": "Lists the state of all Windows features.",
            "tool": "windowsfeature-list"
        }
    ]
}
```
