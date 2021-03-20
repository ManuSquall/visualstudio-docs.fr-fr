---
title: choco-upgrade
description: devinit outil Choco-Upgrade.
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
ms.openlocfilehash: bcd2288ef9399f27f53565ea7ea971579cad7858
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671650"
---
# <a name="choco-upgrade"></a>choco-upgrade

> [!IMPORTANT]
> Depuis le 12 avril 2021, la connexion à GitHub Codespaces à partir de Visual Studio 2019 ne sera plus prise en charge et cette version préliminaire privée s’est terminée. Nous nous concentrons sur les expériences en constante évolution d’une boucle interne basée sur le Cloud et de solutions VDI optimisées pour un large éventail de charges de travail Visual Studio. Dans le cadre de cet article `devinit` , les outils associés ne seront plus disponibles. Nous vous encourageons à participer au Forum de la communauté des développeurs pour Visual Studio afin d’obtenir des informations sur les futures versions préliminaires et les informations de feuille de route.

L' `choco-upgrade` outil peut être utilisé pour installer et mettre à jour des packages en [chocolat](https://chocolatey.org/docs/commandsupgrade) .

## <a name="usage"></a>Utilisation

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil ne fait rien.

| Nom                                             | Type   | Obligatoire  | Valeur                                                                                                          |
|--------------------------------------------------|--------|-----------|----------------------------------------------------------------------------------------------------------------|
| **commentaires**                                     | string | Non        | Propriété de commentaires facultative. Non utilisé.                                                                          |
| [**entrée**](#input)                              | string | Oui       | Package à mettre à niveau. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous.                                                 |
| [**additionalOptions**](#additional-options)     | string | Non        | Options supplémentaires à passer à l’outil. Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.       |

### <a name="input"></a>Entrée

La `input` propriété est utilisée pour spécifier le nom du package à mettre à niveau (par exemple, « MongoDB ») ou le chemin d’accès à un fichier de configuration aux formats suivants _packages.config_, _. NuSpec_ et _. nupkg_. La valeur de `input` sera ajoutée à une `choco upgrade` commande (par exemple `choco upgrade mongodb` ), ainsi que tous les arguments spécifiques à [`additionalOptions`](#additional-options) et les options intégrées `choco` (définies [ci-dessous](#built-in-options)). Les packages sont disponibles dans la [Galerie](https://chocolatey.org/packages)de packages en chocolat. Lorsque vous utilisez un fichier de configuration, vous pouvez passer le chemin d’accès à ce fichier dans la `input` propriété, par exemple : `"input":"packages.config"` .

### <a name="additional-options"></a>Options supplémentaires

Des options de configuration supplémentaires peuvent être transmises en tant que valeur de `additionalOptions` . Ces arguments sont directement dirigés vers les arguments utilisés par [`choco upgrade`](https://chocolatey.org/docs/commands-upgrade) et sont définis dans la documentation en chocolat.

### <a name="built-in-options"></a>Options intégrées

L' `choco-upgrade` outil définit un certain nombre d' `choco` arguments de ligne de commande pour s’assurer que `choco` peut s’exécuter sans affichage. Ces arguments sont répertoriés ci-dessous et leur documentation est disponible dans la [documentation en chocolat](https://chocolatey.org/docs/).

| Nom                  | Description                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **--Oui**             | Confirmer toutes les invites : choisit la réponse affirmative au lieu de vous demander. Implique `--accept-license` . |
| **--non-Progress**     | Ne pas afficher la progression-les pourcentages de progression ne s’affichent pas.                                         |
| **--Skip-PowerShell** | Ignorer PowerShell-chocolateyInstall.ps1 ne sera pas exécuté.                                              |

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `choco-upgrade` outil est d’erreur, car la `input` propriété est requise.

## <a name="example-usage"></a>Exemple d’utilisation
Vous trouverez ci-dessous des exemples d’exécution à `choco-upgrade` l’aide d’un `.devinit.json` .

#### <a name="devinitjson-that-will-update-packages-listed-in-packagesconfig"></a>.devinit.jssur qui met à jour les packages listés dans packages.config :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-upgrade",
            "input": "packages.config",
        }
    ]
}
```

#### <a name="devinitjson-that-will-upgrade-mongodb"></a>.devinit.jssur qui mettra à niveau MongoDB :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-upgrade",
            "input": "mongodb"
        }
    ]
}
```

#### <a name="devinitjson-that-will-upgrade-to-a-specific-version-of-mongodb"></a>.devinit.jssur qui sera mise à niveau vers une version spécifique de MongoDB :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-upgrade",
            "input": "mongodb",
            "additionalOptions": "--version 4.2.7"
        }
    ]
}
```