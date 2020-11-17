---
title: require-vcpkg
description: l’outil devinit requiert-vcpkg.
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
ms.openlocfilehash: 6a9559da218912b6e045c174b7ed20a60f93062e
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671745"
---
# <a name="require-vcpkg"></a>require-vcpkg

L' `require-vcpkg` outil est utilisé pour installer [vcpkg](https://github.com/microsoft/vcpkg).

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

Le comportement par défaut de l' `require-vcpkg` outil consiste à installer vcpkg et à l’ajouter au chemin d’accès (Windows uniquement).

## <a name="example-usage"></a>Exemple d’utilisation
Vous trouverez ci-dessous un exemple de la façon d’exécuter `require-vcpkg` à l’aide d’un `.devinit.json` . 

#### <a name="devinitjson-that-will-install-vcpkg"></a>.devinit.jssur qui installe vcpkg :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-vcpkg"
        }
    ]
}
```
