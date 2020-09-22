---
title: NuGet-restaurer
description: outil devinit NuGet-Restore.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 446498f77d7f9a26c9876f6a163d819a97df1ff9
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810918"
---
# <a name="nuget-restore"></a>NuGet-restaurer

Les `nuget-restore` dépendances de restauration de l’outil et les outils spécifiques au projet qui sont spécifiés dans le fichier projet. En savoir plus sur la restauration NuGet [ici](https://docs.microsoft.com/nuget/reference/cli-reference/cli-ref-restore).

## <a name="usage"></a>Usage

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Name                                             | Type   | Obligatoire | Valeur                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                                                |
| [**entrée**](#input)                              | string | Non       | Chemin d’accès au fichier projet/solution à restaurer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous. |
| [**additionalOptions**](#additional-options)     | string | Non       | Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.                     |

### <a name="input"></a>Entrée

Chemin d’accès au fichier projet/solution à restaurer.

### <a name="additional-options"></a>Options supplémentaires

Des options supplémentaires sont passées en l’absence de la commande NuGet Restore.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `nuget-restore` outil consiste à exécuter’NuGet Restore’dans le répertoire actif.

## <a name="example-usage"></a>Exemple d’utilisation

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "A sample dot-devinit file that restores NuGet pacakges.",
    "run": [
        {
            "tool": "nuget-restore",
            "comments": "Restores the dependencies and tools of a project using nuget restore.",
            "input": "C:\\nuget\\Nuget.config"
        }
    ]
}
```
