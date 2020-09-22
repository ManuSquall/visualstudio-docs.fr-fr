---
title: windowsfeature-disable
description: outil devinit WindowsFeature-Disable.
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
ms.openlocfilehash: 8a649cec23a8f0090500a493fe577b3ba41788f9
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005980"
---
# <a name="windowsfeature-disable"></a>windowsfeature-disable

L' `windowsfeature-disable` outil est utilisé pour acquérir des fonctionnalités Windows.

## <a name="usage"></a>Usage

| Nom                                             | Type   | Obligatoire | Valeur                                                                  |
|--------------------------------------------------|--------|----------|------------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                                  |
| [**entrée**](#input)                              | string | Oui      | Fonctionnalité Windows à installer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous. |
| [**additionalOptions**](#additional-options)     | string | Non       | Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.       |

### <a name="input"></a>Entrée

La `input` propriété doit être du `name` `windows feature` à désactiver.

### <a name="additional-options"></a>Options supplémentaires

Aucun.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `windowsfeature-disable` outil est l’erreur, comme cela est `input` nécessaire.

## <a name="example-usage"></a>Exemple d’utilisation

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs IIS.",
            "tool": "require-windowsfeature",
            "input": "web-server",
        }
    ]
}
```
