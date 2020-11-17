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
ms.openlocfilehash: 9b6ba2e22484850dd6079cfc7e4ab9cd68371dcb
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671925"
---
# <a name="enable-iis"></a>enable-iis

L' `enable-iis` outil est utilisé pour activer les fonctionnalités IIS et installer le [module ASP.net Core](/aspnet/core/host-and-deploy/aspnet-core-module) pour le développement ASP.net avec IIS.

## <a name="usage"></a>Utilisation

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                             | Type   | Obligatoire | Valeur                                                                               |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------------------------|
| **commentaires**                                     | string | No       | Propriété de commentaires facultative. Non utilisé.                                               |
| [**entrée**](#input)                              | string | No       | Non utilisé.                                                                           |
| [**additionalOptions**](#additional-options)     | string | No       | Non utilisé.                                                                           |

### <a name="input"></a>Entrée

Non utilisé.

### <a name="additional-options"></a>Options supplémentaires

Non utilisé.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `enable-iis` outil consiste à activer les fonctionnalités IIS : IIS-serveur, IIS-WebServerRole, IIS-WebSocket et IIS-authentification, puis à installer la dernière version du bundle d’hébergement ASP.net qui comprend le Module ASP.net core. 

## <a name="example-usage"></a>Exemple d’utilisation
Vous trouverez ci-dessous un exemple de la façon d’exécuter `enable-iis` à l’aide d’un `.devinit.json` . 

#### <a name="devinitjson-that-will-enable-iis-development"></a>.devinit.jssur qui active le développement IIS :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0.json",
    "run": [
        {
            "tool": "enable-iis"
        },
    ]
}
```