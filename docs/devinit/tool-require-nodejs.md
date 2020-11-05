---
title: require-nodejs
description: l’outil devinit requiert-NodeJS.
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
ms.openlocfilehash: 6ba6b5a53c6b6f1c67c957c55a612cbe461b108c
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400266"
---
# <a name="require-nodejs"></a>require-nodejs

L' `require-nodejs` outil est utilisé pour installer le [Node.js](https://nodejs.org/) via un MSI distribué par l’organisation Node.js.

## <a name="usage"></a>Usage

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                             | Type   | Obligatoire | Valeur                                                                     |
|--------------------------------------------------|--------|----------|---------------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                                     |
| [**entrée**](#input)                              | string | Non       | Version de Node.JS à installer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous. |
| [**additionalOptions**](#additional-options)     | string | Non       | Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.          |

### <a name="input"></a>Entrée

La `input` propriété est utilisée pour spécifier la version de Node.js. Vous trouverez une liste des versions sur la [ page de téléchargementNode.js](https://nodejs.org/en/download/). Le numéro de version complet est required major. minor. Path (par exemple 14.4.0). s’il est omis, l’installation échoue.

### <a name="additional-options"></a>Options supplémentaires

Des options de configuration supplémentaires peuvent être transmises en tant que valeur de `additionalOptions` . Ces arguments sont directement dirigés vers le programme d’installation MSI pour Node.js.  

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `require-nodejs` outil consiste à installer la dernière version de LTS du nœud, comme indiqué sur le [site Web](https://nodejs.org/en/download/)Node.JS.

## <a name="example-usage"></a>Exemple d’utilisation

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of installing latest LTS of Node.JS.",
            "tool": "require-nodejs"
        },
        {
            "comments": "Example that will install a specific version.",
            "tool": "require-nodejs",
            "input": "14.4.0"
        }
    ]
}
```
