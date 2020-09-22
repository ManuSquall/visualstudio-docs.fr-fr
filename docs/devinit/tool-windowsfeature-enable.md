---
title: windowsfeature-enable
description: outil devinit WindowsFeature-Enable.
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
ms.openlocfilehash: 115fda00f880e9c2fa1782735dd471fc3df68936
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005973"
---
# <a name="windowsfeature-enable"></a>windowsfeature-enable

L' `windowsfeature-enable` outil est utilisé pour activer les fonctionnalités Windows.

## <a name="usage"></a>Usage

| Nom                                             | Type   | Obligatoire | Valeur                                                                    |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                                    |
| [**entrée**](#input)                              | string | Oui      | Fonctionnalité Windows à installer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous.   |
| [**additionalOptions**](#additional-options)     | string | Non       | Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.         |

### <a name="input"></a>Entrée

La `input` propriété doit être le `name` du `windows feature` à installer. Vous trouverez une liste des fonctionnalités disponibles en exécutant `Get-WindowsFeature` PowerShell cmd.

### <a name="additional-options"></a>Options supplémentaires

Aucun.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `windowsfeature-enable` outil est l’erreur, comme cela est `input` nécessaire.

## <a name="example-usage"></a>Exemple d’utilisation

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs IIS.",
            "tool": "windowsfeature-enable",
            "input": "web-server",
        },
        {
            "comments": "Installs the .NET Framework 3.5.",
            "tool": "windowsfeature-enable",
            "input": "net-framework-features"
        },
        {
            "comments": "Installs the .NET Framework 4.5.",
            "tool": "windowsfeature-enable",
            "input": "net-framework-45-features"
        },
        {
            "comments": "Installs Windows Subsystem for Linux 2.0.",
            "tool": "windowsfeature-enable",
            "input": "Microsoft-Windows-Subsystem-Linux"
        }
    ]
}
```
