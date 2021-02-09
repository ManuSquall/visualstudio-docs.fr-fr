---
title: windowsfeature-enable
description: outil devinit WindowsFeature-Enable.
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
ms.openlocfilehash: b24f118613fa1004275702ad27a789ec16e6a347
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874518"
---
# <a name="windowsfeature-enable"></a>windowsfeature-enable

L' `windowsfeature-enable` outil est utilisé pour activer les fonctionnalités Windows.

## <a name="usage"></a>Utilisation

| Nom                                             | Type   | Obligatoire | Valeur                                                                    |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                                    |
| [**entrée**](#input)                              | string | Oui      | Fonctionnalité Windows à installer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous.   |
| [**additionalOptions**](#additional-options)     | string | Non       | Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.         |

### <a name="input"></a>Entrée

La `input` propriété doit être le `name` du `windows feature` à installer. Vous trouverez une liste des fonctionnalités disponibles en exécutant `Get-WindowsFeature` PowerShell cmd.

### <a name="additional-options"></a>Additional-Options

Aucun.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `windowsfeature-enable` outil est l’erreur telle qu’elle est `input` requise.

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
