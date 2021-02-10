---
title: require-nuget
description: l’outil devinit requiert-NuGet.
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
ms.openlocfilehash: 38a8ab363fffe1f13651afb4065833cfd3eb840f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950448"
---
# <a name="require-nuget"></a>require-nuget

L' `require-nuget` outil télécharge l’interface CLI NuGet et l’ajoute à `PATH` . L’interface CLI NuGet fournit l’extension complète de la fonctionnalité NuGet pour installer, créer, publier et gérer des packages sans apporter de modifications aux fichiers projet. En savoir plus sur NuGet CLI [ici](/nuget/reference/nuget-exe-cli-reference).

## <a name="usage"></a>Usage

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                             | Type   | Obligatoire | Valeur                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                                                |
| [**entrée**](#input)                              | string | Non       | Version de l’interface CLI NuGet à installer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous. |
| [**additionalOptions**](#additional-options)     | string | Non       | Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.                     |

### <a name="input"></a>Entrée

`input`Est une propriété facultative utilisée pour spécifier la version de l’interface CLI NuGet à installer. Si `input` est omis, la dernière version de l’interface CLI sera installée.

### <a name="additional-options"></a>Options supplémentaires

Non utilisé.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `require-nuget` outil consiste à installer la dernière version de l’interface CLI NuGet.

## <a name="example-usage"></a>Exemple d’utilisation
Vous trouverez ci-dessous un exemple de la façon d’exécuter `require-nuget` à l’aide d’un `.devinit.json` .

#### <a name="devinitjson-that-will-install-a-specified-version-of-nuget"></a>.devinit.jssur qui installe une version spécifiée de NuGet :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-nuget",
            "input": "5.5.1",
        }
    ]
}
```