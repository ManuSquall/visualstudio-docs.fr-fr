---
title: vcpkg-install
description: devinit outil vcpkg-install.
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
ms.openlocfilehash: 8a4cbe6bd1da12985da87d2f872dc74f988ef213
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672651"
---
# <a name="vcpkg-install"></a>vcpkg-install

> [!IMPORTANT]
> Depuis le 12 avril 2021, la connexion à GitHub Codespaces à partir de Visual Studio 2019 ne sera plus prise en charge et cette version préliminaire privée s’est terminée. Nous nous concentrons sur les expériences en constante évolution d’une boucle interne basée sur le Cloud et de solutions VDI optimisées pour un large éventail de charges de travail Visual Studio. Dans le cadre de cet article `devinit` , les outils associés ne seront plus disponibles. Nous vous encourageons à participer au Forum de la communauté des développeurs pour Visual Studio afin d’obtenir des informations sur les futures versions préliminaires et les informations de feuille de route.

L' `vcpkg-install` outil permet d’acquérir des bibliothèques C/C++ (appelées ports) à l’aide de [vcpkg](https://github.com/microsoft/vcpkg).

## <a name="usage"></a>Utilisation

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                             | Type   | Obligatoire | Valeur                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                                                   |
| [**entrée**](#input)                              | string | Oui      | Package (s) à installer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous.                       |
| [**additionalOptions**](#additional-options)     | string | Non       | Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.                        |

### <a name="input"></a>Entrée

La `input` propriété doit être le `name` du `vcpkg` à installer ou une liste de noms séparés par des espaces pour installer plusieurs packages. Vous trouverez une liste des ports disponibles sur le [vcpkg GitHub référentiel](https://github.com/microsoft/vcpkg/tree/master/ports).

### <a name="additional-options"></a>Options supplémentaires

Des options supplémentaires sont transmises directement à la commande [vcpkg](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true) et sont documentées sur le [référentiel GitHub vcpkg](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md).

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `vcpkg-install` outil est l’erreur telle qu’elle est `input` requise.

## <a name="example-usage"></a>Exemple d’utilisation
Vous trouverez ci-dessous des exemples d’exécution à `vcpkg-install` l’aide d’un `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-sdl2-port"></a>.devinit.jssur qui installe le port sdl2 :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "vcpkg-install",
            "input": "sdl2",
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-multiple-ports"></a>.devinit.jssur qui installe plusieurs ports :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [

        {
            "tool": "vcpkg-install",
            "input": "sdl2 sqlite3"
        }
    ]
}
```