---
title: require-NodeJS
description: l’outil devinit requiert-NodeJS.
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
ms.openlocfilehash: 6bc2de2e497bd58cfc036e74af3968a2f70d1f52
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808355"
---
# <a name="require-nodejs"></a>require-NodeJS

L' `require-nodejs` outil est utilisé pour installer le [Node.js](https://nodejs.org/) via un MSI distribué par l’organisation Node.js.

## <a name="usage"></a>Usage

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Name                                             | Type   | Obligatoire | Valeur                                                                     |
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
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
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
