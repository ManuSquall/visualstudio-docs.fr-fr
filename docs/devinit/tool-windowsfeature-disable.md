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
ms.openlocfilehash: 1f06f89a61b77bd4c323303ca796252d4874b3cc
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671731"
---
# <a name="windowsfeature-disable"></a>windowsfeature-disable

L' `windowsfeature-disable` outil est utilisé pour acquérir des fonctionnalités Windows.

## <a name="usage"></a>Utilisation

| Nom                                             | Type   | Obligatoire | Valeur                                                                  |
|--------------------------------------------------|--------|----------|------------------------------------------------------------------------|
| **commentaires**                                     | string | No       | Propriété de commentaires facultative. Non utilisé.                                  |
| [**entrée**](#input)                              | string | Oui      | Fonctionnalité Windows à installer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous. |
| [**additionalOptions**](#additional-options)     | string | No       | Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.       |

### <a name="input"></a>Entrée

La `input` propriété doit être du `name` `windows feature` à désactiver.

### <a name="additional-options"></a>Additional-Options

Aucun.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `windowsfeature-disable` outil est l’erreur, comme cela est `input` nécessaire.

## <a name="example-usage"></a>Exemple d’utilisation
Vous trouverez ci-dessous un exemple de la façon d’exécuter `windowsfeature-disable` à l’aide d’un `.devinit.json` . 

#### <a name="devinitjson-that-will-disable-a-specified-feature"></a>.devinit.jssur qui désactive une fonctionnalité spécifiée :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-windowsfeature",
            "input": "web-server",
        }
    ]
}
```
