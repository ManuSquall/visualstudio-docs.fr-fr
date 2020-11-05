---
title: choco-upgrade
description: devinit outil Choco-Upgrade.
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
ms.openlocfilehash: 39d30b08e4ca3ba3a3e355fdf123f3a05055c358
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399666"
---
# <a name="choco-upgrade"></a>choco-upgrade

L' `choco-upgrade` outil peut être utilisé pour installer et mettre à jour des packages en [chocolat](https://chocolatey.org/docs/commandsupgrade) .

## <a name="usage"></a>Usage

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil ne fait rien.

| Nom                                             | Type   | Obligatoire | Valeur                                                                                                          |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                                                                          |
| [**entrée**](#input)                              | string | Non       | Package à mettre à niveau. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous.                                                 |
| [**additionalOptions**](#additional-options)     | string | Non       | Options supplémentaires à passer à l’outil. Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.       |

### <a name="input"></a>Entrée

La `input` propriété est utilisée pour spécifier le nom du package à mettre à niveau (par exemple, « MongoDB ») ou le chemin d’accès à un fichier de configuration aux formats suivants _packages.config_ , _. NuSpec_ et _. nupkg_. La valeur de `input` sera ajoutée à une `choco upgrade` commande (par exemple `choco upgrade mongodb` ), ainsi que tous les arguments spécifiques à [`additionalOptions`](#additional-options) et les options intégrées `choco` (définies [ci-dessous](#built-in-options)). Les packages sont disponibles dans la [Galerie](https://chocolatey.org/packages)de packages en chocolat. Lorsque vous utilisez un fichier de configuration, vous pouvez passer le chemin d’accès à ce fichier dans la `input` propriété, par exemple : `"input":"packages.config"` .

### <a name="additional-options"></a>Options supplémentaires

Des options de configuration supplémentaires peuvent être transmises en tant que valeur de `additionalOptions` . Ces arguments sont directement dirigés vers les arguments utilisés par [`choco upgrade`](https://chocolatey.org/docs/commands-upgrade) et sont définis dans la documentation en chocolat.

## <a name="built-in-options"></a>Options intégrées

L' `choco-upgrade` outil définit un certain nombre d' `choco` arguments de ligne de commande pour s’assurer que `choco` peut s’exécuter sans affichage. Ces arguments sont répertoriés ci-dessous et leur documentation est disponible dans la [documentation en chocolat](https://chocolatey.org/docs/).

| Nom                  | Description                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **--Oui**             | Confirmer toutes les invites : choisit la réponse affirmative au lieu de vous demander. Implique `--accept-license` . |
| **--non-Progress**     | Ne pas afficher la progression-les pourcentages de progression ne s’affichent pas.                                         |
| **--Skip-PowerShell** | Ignorer PowerShell-chocolateyInstall.ps1 ne sera pas exécuté.                                              |

## <a name="example-usage"></a>Exemple d’utilisation

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of upgrading packages listed in a packages.config file.",
            "tool": "choco-upgrade",
            "input": "packages.config",
        },
        {
            "comments": "Example that will upgrade the package 'mongodb'.",
            "tool": "choco-upgrade",
            "input": "mongodb"
        },
        {
            "comments": "Example that will upgrade the '4.2.7' version of 'mongodb'.",
            "tool": "choco-upgrade",
            "input": "mongodb",
            "additionalOptions": "--version 4.2.7"
        }
    ]
}
```
