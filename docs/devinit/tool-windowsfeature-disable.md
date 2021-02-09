---
title: windowsfeature-disable
description: outil devinit WindowsFeature-Disable.
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
ms.openlocfilehash: ba0bcea403033d869d429c2bc85d86434a3b3846
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874511"
---
# <a name="windowsfeature-disable"></a>windowsfeature-disable

L' `windowsfeature-disable` outil est utilisé pour acquérir des fonctionnalités Windows.

## <a name="usage"></a>Utilisation

| Nom                                             | Type   | Obligatoire | Valeur                                                                  |
|--------------------------------------------------|--------|----------|------------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                                  |
| [**entrée**](#input)                              | string | Oui      | Fonctionnalité Windows à installer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous. |
| [**additionalOptions**](#additional-options)     | string | Non       | Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.       |

### <a name="input"></a>Entrée

La `input` propriété doit être du `name` `windows feature` à désactiver.

### <a name="additional-options"></a>Additional-Options

Aucun.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `windowsfeature-disable` outil est l’erreur telle qu’elle est `input` requise.

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
