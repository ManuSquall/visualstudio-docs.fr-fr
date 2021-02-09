---
title: nuget-restore
description: outil devinit NuGet-Restore.
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
ms.openlocfilehash: f805b5c1c7b3b994c984dfdb6ce937f8cd51edf1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99848231"
---
# <a name="nuget-restore"></a>nuget-restore

Les `nuget-restore` dépendances de restauration de l’outil et les outils spécifiques au projet qui sont spécifiés dans le fichier projet. En savoir plus sur la restauration NuGet [ici](/nuget/reference/cli-reference/cli-ref-restore).

## <a name="usage"></a>Utilisation

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                             | Type   | Obligatoire | Valeur                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                                                |
| [**entrée**](#input)                              | string | Non       | Chemin d’accès au fichier projet/solution à restaurer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous. |
| [**additionalOptions**](#additional-options)     | string | Non       | Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.                     |

### <a name="input"></a>Entrée

Chemin d’accès au fichier projet/solution à restaurer.

### <a name="additional-options"></a>Options supplémentaires

Des options supplémentaires sont passées en l’absence de la commande NuGet Restore.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `nuget-restore` outil est l’exécution `NuGet restore` dans le répertoire actif.

## <a name="example-usage"></a>Exemple d’utilisation
Vous trouverez ci-dessous un exemple de la façon d’exécuter `nuget-restore` à l’aide d’un `.devinit.json` .

#### <a name="devinitjson-that-will-restore-dependencies-and-tools-of-a-project"></a>.devinit.jssur qui restaure les dépendances et les outils d’un projet :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "nuget-restore",
            "input": "C:\\nuget\\Nuget.config"
        }
    ]
}
```