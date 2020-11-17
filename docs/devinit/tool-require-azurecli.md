---
title: require-azurecli
description: l’outil devinit requiert-azurecli.
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
ms.openlocfilehash: da6ce656e552a7df0b02fd4a0df3a1fb78871607
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672145"
---
# <a name="require-azurecli"></a>require-azurecli

L' `require-azurecli` outil est utilisé pour installer le [Azure CLI](/cli/azure/?view=azure-cli-latest&preserve-view=true) via le Azure CLI msi.

## <a name="usage"></a>Utilisation

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

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

Le comportement par défaut de l' `require-azurecli` outil consiste à installer la dernière version de la Azure CLI et à l’ajouter au chemin d’accès (Windows uniquement).

## <a name="example-usage"></a>Exemple d’utilisation
Vous trouverez ci-dessous un exemple de la façon d’exécuter `require-azurecli` à l’aide d’un `.devinit.json` . 

#### <a name="devinitjson-that-will-install-the-azure-cli"></a>.devinit.jssur qui installe le Azure CLI :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-azurecli"
        }
    ]
}
```