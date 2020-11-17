---
title: dotnet-restore
description: outil devinit dotnet-Restore.
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
ms.openlocfilehash: 51c6ed6576fefe3853bca7f4250c1884bd364f64
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671932"
---
# <a name="dotnet-restore"></a>dotnet-restore

Les `dotnet-restore` dépendances de restauration de l’outil et les outils spécifiques au projet qui sont spécifiés dans le fichier projet. En savoir plus sur dotnet restore [ici](/dotnet/core/tools/dotnet-restore).

## <a name="usage"></a>Utilisation

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                             | Type   | Obligatoire | Valeur                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **commentaires**                                     | string | No       | Propriété de commentaires facultative. Non utilisé.                                                |
| [**entrée**](#input)                              | string | No       | Chemin d’accès au fichier projet/solution à restaurer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous. |
| [**additionalOptions**](#additional-options)     | string | No       | Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.                     |

### <a name="input"></a>Entrée

Chemin d’accès au fichier projet/solution à restaurer.

### <a name="additional-options"></a>Options supplémentaires

Des options supplémentaires sont passées en l’absence de la commande dotnet restore.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `dotnet-restore` outil consiste à exécuter’dotnet Restore’dans le répertoire actif.

## <a name="example-usage"></a>Exemple d’utilisation
Vous trouverez ci-dessous un exemple de la façon d’exécuter `dotnet-restore` à l’aide d’un `.devinit.json` . 

#### <a name="devinitjson-that-will-restore-dependencies-and-tools-of-a-project"></a>.devinit.jssur qui restaure les dépendances et les outils d’un projet :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "dotnet-restore",
            "input": "C:\\app1\\app1.csproj"
        }
    ]
}
```