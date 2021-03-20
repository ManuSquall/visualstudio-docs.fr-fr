---
title: azurecli-login
description: devinit outil azurecli-login.
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
ms.openlocfilehash: 64b215912c21a405c2b2c3a0feb3720a4ab16c44
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671664"
---
# <a name="azurecli-login"></a>azurecli-login

> [!IMPORTANT]
> Depuis le 12 avril 2021, la connexion à GitHub Codespaces à partir de Visual Studio 2019 ne sera plus prise en charge et cette version préliminaire privée s’est terminée. Nous nous concentrons sur les expériences en constante évolution d’une boucle interne basée sur le Cloud et de solutions VDI optimisées pour un large éventail de charges de travail Visual Studio. Dans le cadre de cet article `devinit` , les outils associés ne seront plus disponibles. Nous vous encourageons à participer au Forum de la communauté des développeurs pour Visual Studio afin d’obtenir des informations sur les futures versions préliminaires et les informations de feuille de route.

L' `azurecli-login` outil est utilisé pour se connecter à Azure Active Directory via [Azure CLI](/cli/azure/authenticate-azure-cli?preserve-view=true&view=azure-cli-latest). Cet outil utilise la commande Azure CLI : `az login --use-device-code` , pour terminer la connexion, vous devez suivre les instructions affichées sur la console.

## <a name="usage"></a>Utilisation

Si les deux propriétés sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                             | Type   | Obligatoire | Valeur                                                                          |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                                          |
| [**entrée**](#input)                              | string | Non       | Non utilisé. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous.                               |
| [**additionalOptions**](#additional-options)     | string | Non       | Non utilisé. Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.     |

### <a name="input"></a>Entrée

Non utilisé.

### <a name="additional-options"></a>Options supplémentaires

Non utilisé.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `azurecli-login` outil consiste à installer la dernière version de la Azure CLI et à l’ajouter au `PATH` .

## <a name="example-usage"></a>Exemple d’utilisation
Vous trouverez ci-dessous un exemple de la façon d’exécuter `azurecli-login` à l’aide d’un `.devinit.json` .

#### <a name="devinitjson-that-will-trigger-azure-login"></a>.devinit.jssur qui déclenchera la connexion à Azure :

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "azurecli-login"
        }
    ]
}
```