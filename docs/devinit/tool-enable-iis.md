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
ms.openlocfilehash: eecdc2a020117b7345682068cb27509df805ff9b
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671629"
---
# <a name="enable-iis"></a>enable-iis

> [!IMPORTANT]
> Depuis le 12 avril 2021, la connexion à GitHub Codespaces à partir de Visual Studio 2019 ne sera plus prise en charge et cette version préliminaire privée s’est terminée. Nous nous concentrons sur les expériences en constante évolution d’une boucle interne basée sur le Cloud et de solutions VDI optimisées pour un large éventail de charges de travail Visual Studio. Dans le cadre de cet article `devinit` , les outils associés ne seront plus disponibles. Nous vous encourageons à participer au Forum de la communauté des développeurs pour Visual Studio afin d’obtenir des informations sur les futures versions préliminaires et les informations de feuille de route.

L' `enable-iis` outil est utilisé pour activer les fonctionnalités IIS et installer le [module ASP.net Core](/aspnet/core/host-and-deploy/aspnet-core-module) pour le développement ASP.net avec IIS.

## <a name="usage"></a>Utilisation

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