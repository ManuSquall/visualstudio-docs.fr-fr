---
title: enable-iis
description: activation de l’outil devinit-IIS.
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
ms.openlocfilehash: 8af1a09ba16c1b51c0ebb443aed65e131bbc6b9f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932805"
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