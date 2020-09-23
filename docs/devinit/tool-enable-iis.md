---
title: activer-IIS
description: activation de l’outil devinit-IIS.
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
ms.openlocfilehash: 245ea76f988b9a9e320a51ba6b2df01382668cc0
ms.sourcegitcommit: 417ea66a8b07ec102ece2fa00e07b88edc404c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91127828"
---
# <a name="enable-iis"></a>activer-IIS

L' `enable-iis` outil est utilisé pour activer les fonctionnalités IIS et installer le [module ASP.net Core](https://docs.microsoft.com/aspnet/core/host-and-deploy/aspnet-core-module) pour le développement ASP.net avec IIS.

## <a name="usage"></a>Usage

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                             | Type   | Obligatoire | Valeur                                                                               |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                                               |
| [**entrée**](#input)                              | string | Non       | Non utilisé.                                                                           |
| [**additionalOptions**](#additional-options)     | string | Non       | Non utilisé.                                                                           |

### <a name="input"></a>Entrée

Non utilisé.

### <a name="additional-options"></a>Options supplémentaires

Non utilisé.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `enable-iis` outil consiste à activer les fonctionnalités IIS : IIS-serveur, IIS-WebServerRole, IIS-WebSocket et IIS-authentification, puis à installer la dernière version du bundle d’hébergement ASP.net qui comprend le Module ASP.net core. 

## <a name="example-usage"></a>Exemple d’utilisation

```json
{
    "$schema": "./devinit.schema-2.0.json",
    "run": [
        {
            "comments": "Example that will enable IIS features and install the latest ASP.NET hosting bundle.",
            "tool": "enable-iis"
        },
    ]
}
```
