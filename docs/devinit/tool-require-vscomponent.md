---
title: require-vscomponent
description: l’outil devinit requiert-vscomponent.
ms.date: 02/08/2021
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 50172f96a49e2384553a372ded0c889b30a23fff
ms.sourcegitcommit: e262f4c2a147c3fa2d27de666aae3a0497317867
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2021
ms.locfileid: "100006394"
---
# <a name="require-vscomponent"></a>require-vscomponent

L' `require-vscomponent` outil est utilisé pour importer des configurations Visual Studio dans Visual Studio existant. En savoir plus à `.vsconfig` [ce](../install/import-export-installation-configurations.md)sujet.

## <a name="usage"></a>Usage

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                     | Type   | Obligatoire | Valeur                                                                |
|------------------------------------------|--------|----------|----------------------------------------------------------------------|
| **commentaires**                             | string | Non       | Propriété de commentaires facultative. Non utilisé.                                |
| [**entrée**](#input)                      | string | Non       | Chemin d’accès complet de `.vsconfig` . Pour plus d’informations, consultez l' [entrée](#input) ci-dessous. |
| [additionalOptions](#additional-options) | string | Non       | Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.     |

### <a name="input"></a>Entrée

La `input` propriété est utilisée pour spécifier le chemin d’accès complet du `.vsconfig` fichier. Si ce n’est pas mentionné, l’outil recherche un `.vsconfig` dans le répertoire actif et transmet la valeur au Visual Studio installer.

### <a name="additional-options"></a>Options supplémentaires

Des options de configuration supplémentaires peuvent être transmises en tant que valeur de `additionalOptions` . 

| Nom                      | Type      | Obligatoire | Valeur                                                                                                                                                                                    |
|---------------------------|-----------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --installPath             | string    | Non       | Chemin d’installation de l’instance de Visual Studio que vous souhaitez modifier.                                                                                                                       |

Si aucun chemin d’installation n’est spécifié, l’outil modifie le Visual Studio installé le plus tôt sur votre ordinateur s’il y a plusieurs instances sur votre ordinateur. 

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

#### <a name="devinitjson-that-will-import-the-configurations-of-a-given-vsconfig-file-path-to-the-visual-studio-instance-specified-via-an-install-path"></a>.devinit.jssur qui importera les configurations d’un chemin d’accès de fichier. vsconfig donné vers l’instance de Visual Studio spécifiée via un chemin d’installation :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "A sample dot-devinit file.",
    "run": [
        {
            "tool": "require-vscomponent",
            "input": "C:\\.vsconfig",
            "additionalOptions": "--installPath 'C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\Enterprise'"
        }
    ]
}
```