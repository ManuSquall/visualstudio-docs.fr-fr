---
title: require-choco
description: l’outil devinit requiert-Choco.
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
ms.openlocfilehash: d9ecd12a36621ab2a21f94014d6a0fd13568609b
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671878"
---
# <a name="require-choco"></a>require-choco

L' `require-choco` outil peut être utilisé pour installer le [chocolat](https://chocolatey.org/).

## <a name="usage"></a>Utilisation

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                             | Type   | Obligatoire | Valeur                                                                      |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------|
| **commentaires**                                     | string | No       | Propriété de commentaires facultative. Non utilisé.                                      |
| [**entrée**](#input)                              | string | No       | Non utilisé. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous.                           |
| [**additionalOptions**](#additional-options)     | string | No       | Non utilisé. Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous. |

### <a name="input"></a>Entrée

Non utilisé.

### <a name="additional-options"></a>Options supplémentaires

Non utilisé.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `require-choco` outil consiste à installer le chocolat et à l’ajouter au chemin d’accès (Windows uniquement).

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