---
title: require-nuget
description: l’outil devinit requiert-NuGet.
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
ms.openlocfilehash: e4f08e8c3f5967eb2e9db53633a12b304ac23bfb
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671759"
---
# <a name="require-nuget"></a>require-nuget

`require-nuget`Outil permettant de télécharger l’interface CLI NuGet et de l’ajouter à la variable PATH. L’interface CLI NuGet fournit l’extension complète de la fonctionnalité NuGet pour installer, créer, publier et gérer des packages sans apporter de modifications aux fichiers projet. En savoir plus sur NuGet CLI [ici](/nuget/reference/nuget-exe-cli-reference).

## <a name="usage"></a>Utilisation

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                             | Type   | Obligatoire | Valeur                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **commentaires**                                     | string | No       | Propriété de commentaires facultative. Non utilisé.                                                |
| [**entrée**](#input)                              | string | No       | Version de l’interface CLI NuGet à installer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous. |
| [**additionalOptions**](#additional-options)     | string | No       | Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.                     |

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