---
title: require-nodejs
description: l’outil devinit requiert-NodeJS.
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
ms.openlocfilehash: ca1d5e48ab61926336aecebb1a2a4b794c704482
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842672"
---
# <a name="require-nodejs"></a>require-nodejs

L' `require-nodejs` outil est utilisé pour installer le [Node.js](https://nodejs.org/) via un MSI distribué par l’organisation Node.js.

## <a name="usage"></a>Utilisation

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
Vous trouverez ci-dessous des exemples d’exécution à `require-nodejs` l’aide d’un `.devinit.json` . 

#### <a name="devinitjson-that-will-install-the-lts-of-nodejs"></a>.devinit.jssur qui installe le LTS de Node.js :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-nodejs"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-nodejs"></a>.devinit.jssur qui installe une version spécifique de Node.js :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-nodejs",
            "input": "14.4.0"
        }
    ]
}
```
