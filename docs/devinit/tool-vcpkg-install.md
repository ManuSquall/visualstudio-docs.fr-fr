---
title: vcpkg-installer
description: devinit outil vcpkg-install.
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
ms.openlocfilehash: 2e6dcad778e89b112a8c851f2f27ac46330466af
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810413"
---
# <a name="vcpkg-install"></a>vcpkg-installer

L' `vcpkg-install` outil permet d’acquérir des bibliothèques C/C++ (appelées ports) à l’aide de [vcpkg](https://github.com/microsoft/vcpkg).

## <a name="usage"></a>Usage

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Name                                             | Type   | Obligatoire | Valeur                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                                                   |
| [**entrée**](#input)                              | string | Oui      | Package (s) à installer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous.                       |
| [**additionalOptions**](#additional-options)     | string | Non       | Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.                        |

### <a name="input"></a>Entrée

La `input` propriété doit être le `name` du `vcpkg` à installer ou une liste de noms séparés par des espaces pour installer plusieurs packages. Vous trouverez une liste des ports disponibles sur le [vcpkg GitHub référentiel](https://github.com/microsoft/vcpkg/tree/master/ports).

### <a name="additional-options"></a>Options supplémentaires

Des options supplémentaires sont transmises directement à la commande [vcpkg](https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true) et sont documentées sur le [référentiel GitHub vcpkg](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md).

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `vcpkg-install` outil est l’erreur, comme cela est `input` nécessaire.

## <a name="example-usage"></a>Exemple d’utilisation

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs the sdl2 port.",
            "tool": "vcpkg-install",
            "input": "sdl2",
        },
        {
            "comments": "Installs the sdl2 and sqlite3 ports.",
            "tool": "vcpkg-install",
            "input": "sdl2 sqlite3"
        }
    ]
}
```
