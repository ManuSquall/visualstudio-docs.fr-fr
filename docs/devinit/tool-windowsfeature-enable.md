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
ms.openlocfilehash: 9ed1cc5379cc28c3932c96271fda27e23f4cd27c
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672005"
---
# <a name="windowsfeature-enable"></a>windowsfeature-enable

L' `windowsfeature-enable` outil est utilisé pour activer les fonctionnalités Windows.

## <a name="usage"></a>Utilisation

| Nom                                             | Type   | Obligatoire | Valeur                                                                    |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------|
| **commentaires**                                     | string | No       | Propriété de commentaires facultative. Non utilisé.                                    |
| [**entrée**](#input)                              | string | Oui      | Fonctionnalité Windows à installer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous.   |
| [**additionalOptions**](#additional-options)     | string | No       | Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.         |

### <a name="input"></a>Entrée

La `input` propriété doit être le `name` du `windows feature` à installer. Vous trouverez une liste des fonctionnalités disponibles en exécutant `Get-WindowsFeature` PowerShell cmd.

### <a name="additional-options"></a>Additional-Options

Aucun.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `windowsfeature-enable` outil est l’erreur, comme cela est `input` nécessaire.

## <a name="example-usage"></a>Exemple d’utilisation
Vous trouverez ci-dessous des exemples d’exécution à `windowsfeature-enable` l’aide d’un `.devinit.json` . 

#### <a name="devinitjson-that-will-install-iis"></a>.devinit.jssur qui installe IIS :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "windowsfeature-enable",
            "input": "web-server",
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-net-framework"></a>.devinit.jssur qui installe le .NET Framework :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "windowsfeature-enable",
            "input": "net-framework-features"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-net-framework-45"></a>.devinit.jssur qui installe le .NET Framework 4,5 :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "windowsfeature-enable",
            "input": "net-framework-45-features"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-windows-subsystem-for-linux-20"></a>.devinit.jssur qui installe le sous-système Windows pour Linux 2,0 :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "windowsfeature-enable",
            "input": "Microsoft-Windows-Subsystem-Linux"
        }
    ]
}
```
