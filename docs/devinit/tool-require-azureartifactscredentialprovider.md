---
title: require-azureartifactscredentialprovider
description: l’outil devinit requiert-azureartifactscredentialprovider.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: ad39bc070841dae5202abca8ca4624927a100f23
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440387"
---
# <a name="require-azureartifactscredentialprovider"></a>require-azureartifactscredentialprovider

L' `require-azureartifactscredentialprovider` outil installe le fournisseur d’informations d’identification Azure artifacts. Le fournisseur d’informations d’identification Azure Artifacts automatise l’acquisition des informations d’identification nécessaires pour restaurer les packages NuGet dans le cadre de votre flux de travail de développement .NET. En savoir plus sur Azure Artifacts fournisseur d’informations d’identification [ici](https://github.com/microsoft/artifacts-credprovider/blob/master/README.md).

## <a name="usage"></a>Usage

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                             | Type   | Obligatoire | Valeur                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                                                |
| [**entrée**](#input)                              | string | Non       | Non utilisé. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous. |
| [**additionalOptions**](#additional-options)     | string | Non       | Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.                     |

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
