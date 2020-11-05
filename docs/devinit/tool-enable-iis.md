---
title: enable-iis
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
ms.openlocfilehash: ec326871f5565ecaabdc8cda369b36df14029414
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399829"
---
# <a name="enable-iis"></a>enable-iis

L' `enable-iis` outil est utilisé pour activer les fonctionnalités IIS et installer le [module ASP.net Core](/aspnet/core/host-and-deploy/aspnet-core-module) pour le développement ASP.net avec IIS.

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
    "$schema": "https://json.schemastore.org/devinit.schema-3.0.json",
    "run": [
        {
            "comments": "Example that will enable IIS features and install the latest ASP.NET hosting bundle.",
            "tool": "enable-iis"
        },
    ]
}
```