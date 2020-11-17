---
title: require-vscomponent
description: l’outil devinit requiert-vscomponent.
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
ms.openlocfilehash: e9d2f546e99f83b4c53d0b76abfdaf8ec91868ac
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672110"
---
# <a name="require-vscomponent"></a>require-vscomponent

L' `require-vscomponent` outil est utilisé pour importer des configurations Visual Studio dans Visual Studio existant. En savoir plus à `.vsconfig` [ce](../install/import-export-installation-configurations.md)sujet.

## <a name="usage"></a>Utilisation

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                     | Type   | Obligatoire | Valeur                                                                |
|------------------------------------------|--------|----------|----------------------------------------------------------------------|
| **commentaires**                             | string | No       | Propriété de commentaires facultative. Non utilisé.                                |
| [**entrée**](#input)                      | string | No       | Chemin d’accès complet de `.vsconfig` . Pour plus d’informations, consultez l' [entrée](#input) ci-dessous. |
| [additionalOptions](#additional-options) | string | No       | Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.     |

### <a name="input"></a>Entrée

La `input` propriété est utilisée pour spécifier le chemin d’accès complet du `.vsconfig` fichier. Si ce n’est pas mentionné, l’outil recherche un `.vsconfig` dans le répertoire actif et transmet la valeur au Visual Studio installer.

### <a name="additional-options"></a>Options supplémentaires

Non utilisé.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `require-vscomponent` outil consiste à rechercher un `.vsconfig` fichier dans le répertoire actif et à exécuter le Visual Studio installer avec ces détails en mode silencieux. `require-vscomponent` prend uniquement en charge la modification d’une installation existante de Visual Studio.

## <a name="example-usage"></a>Exemple d’utilisation
Vous trouverez ci-dessous un exemple de la façon d’exécuter `require-vscomponent` à l’aide d’un `.devinit.json` . 

#### <a name="devinitjson-that-will-import-the-configurations-of-a-given-vsconfig-file-path"></a>.devinit.jssur qui importe les configurations d’un chemin d’accès de fichier. vsconfig donné :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "A sample dot-devinit file.",
    "run": [
        {
            "tool": "require-vscomponent",
            "input": "C:\\.vsconfig"
        }
    ]
}
```