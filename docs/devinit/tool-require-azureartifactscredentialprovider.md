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
ms.openlocfilehash: c784bb25fe9abc77cfb562ae085930b275d0ef03
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400287"
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

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "A sample dot-devinit file that installs Azure Artifacts Credential Provider.'",
    "run": [
        {
            "tool": "require-azureartifactscredentialprovider",
            "comments": "Installs Azure Artifacts Credential Provider."
        }
    ]
}
```
