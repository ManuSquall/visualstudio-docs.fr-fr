---
title: require-azureartifactscredentialprovider
description: l’outil devinit requiert-azureartifactscredentialprovider.
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
ms.openlocfilehash: 0aa0d250289e6bf79467c0a00ddddef5264ed6d2
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671898"
---
# <a name="require-azureartifactscredentialprovider"></a>require-azureartifactscredentialprovider

L' `require-azureartifactscredentialprovider` outil installe le fournisseur d’informations d’identification Azure artifacts. Le fournisseur d’informations d’identification Azure Artifacts automatise l’acquisition des informations d’identification nécessaires pour restaurer les packages NuGet dans le cadre de votre flux de travail de développement .NET. En savoir plus sur Azure Artifacts fournisseur d’informations d’identification [ici](https://github.com/microsoft/artifacts-credprovider/blob/master/README.md).

## <a name="usage"></a>Utilisation

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                             | Type   | Obligatoire | Valeur                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **commentaires**                                     | string | No       | Propriété de commentaires facultative. Non utilisé.                                                |
| [**entrée**](#input)                              | string | No       | Non utilisé. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous. |
| [**additionalOptions**](#additional-options)     | string | No       | Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.                     |

### <a name="input"></a>Entrée

Non utilisé. Ignore toute entrée, si elle est indiquée.

### <a name="additional-options"></a>Options supplémentaires

Des options supplémentaires sont passées en l’absence de la commande du fournisseur d’informations d’identification.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `require-azureartifactscredentialprovider` outil consiste à installer la dernière version du fournisseur d’informations d’identification Azure artifacts.

## <a name="example-usage"></a>Exemple d’utilisation
Vous trouverez ci-dessous un exemple de la façon d’exécuter `require-azureartifactscredentialprovider` à l’aide d’un `.devinit.json` . 

#### <a name="devinitjson-that-will-install-azure-artifacts-credential-provider"></a>.devinit.jssur qui installe le fournisseur d’informations d’identification Azure Artifacts :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-azureartifactscredentialprovider",
        }
    ]
}
```
