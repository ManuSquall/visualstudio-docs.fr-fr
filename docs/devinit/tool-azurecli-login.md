---
title: azurecli-login
description: devinit outil azurecli-login.
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
ms.openlocfilehash: 304c7b12e3b290c3e47857877b050b18873e3934
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672310"
---
# <a name="azurecli-login"></a>azurecli-login

L' `azurecli-login` outil est utilisé pour se connecter à Azure Active Directory via [Azure CLI](/cli/azure/authenticate-azure-cli?preserve-view=true&view=azure-cli-latest). Cet outil utilise la commande Azure CLI : `az login --use-device-code` , pour terminer la connexion, vous devez suivre les instructions affichées sur la console.

## <a name="usage"></a>Utilisation

Si les deux propriétés sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                             | Type   | Obligatoire | Valeur                                                                          |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------|
| **commentaires**                                     | string | No       | Propriété de commentaires facultative. Non utilisé.                                          |
| [**entrée**](#input)                              | string | No       | Non utilisé. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous.                               |
| [**additionalOptions**](#additional-options)     | string | No       | Non utilisé. Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.     |

### <a name="input"></a>Entrée

Non utilisé.

### <a name="additional-options"></a>Options supplémentaires

Non utilisé.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `azurecli-login` outil consiste à installer la dernière version de la Azure CLI et à l’ajouter au chemin d’accès (Windows uniquement).

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