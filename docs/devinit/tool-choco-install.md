---
title: choco-install
description: devinit Tool Choco-install pour installer les packages en chocolat.
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
ms.openlocfilehash: c1f5b1c587ea8d1d6335e19b2e7303cc12ad9783
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671657"
---
# <a name="choco-install"></a>choco-install

> [!IMPORTANT]
> Depuis le 12 avril 2021, la connexion à GitHub Codespaces à partir de Visual Studio 2019 ne sera plus prise en charge et cette version préliminaire privée s’est terminée. Nous nous concentrons sur les expériences en constante évolution d’une boucle interne basée sur le Cloud et de solutions VDI optimisées pour un large éventail de charges de travail Visual Studio. Dans le cadre de cet article `devinit` , les outils associés ne seront plus disponibles. Nous vous encourageons à participer au Forum de la communauté des développeurs pour Visual Studio afin d’obtenir des informations sur les futures versions préliminaires et les informations de feuille de route.

L' `choco-install` outil peut être utilisé pour installer et mettre à jour des packages en [chocolat](https://chocolatey.org/) .

## <a name="usage"></a>Utilisation

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil ne fait rien.

| Nom                                             | Type   | Obligatoire  | Valeur                                                                                                          |
|--------------------------------------------------|--------|-----------|----------------------------------------------------------------------------------------------------------------|
| **commentaires**                                     | string | Non        | Propriété de commentaires facultative. Non utilisé.                                                                          |
| [**entrée**](#input)                              | string | Oui       | Le package à installer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous.                                                 |
| [**additionalOptions**](#additional-options)     | string | Non        | Options supplémentaires à passer à l’outil. Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.       |

### <a name="input"></a>Entrée

La `input` propriété est utilisée pour spécifier le nom du package à installer (par exemple, « MongoDB ») ou le chemin d’accès à un fichier de configuration aux formats suivants _packages.config_, _. NuSpec_ et _. nupkg_. La valeur de `input` sera ajoutée à une `choco install` commande (par exemple `choco install mongodb` ), ainsi que tous les arguments spécifiques à [`additionalOptions`](#additional-options) et les options intégrées `choco` (définies [ci-dessous](#built-in-options)). Des packages se trouvent dans la Galerie de packages en [chocolat](https://chocolatey.org/packages). Lorsque vous utilisez un fichier de configuration, vous pouvez transmettre le chemin d’accès à ce fichier dans la `input` propriété, par exemple `"input":"packages.config"` .

### <a name="additional-options"></a>Options supplémentaires

Des options de configuration supplémentaires peuvent être transmises en tant que valeur de `additionalOptions` . Ces arguments sont directement dirigés vers les arguments utilisés par [`choco install`](https://chocolatey.org/docs/commands-install) et sont définis dans la documentation en chocolat.

#### <a name="adding-new-feeds-to-chocolatey"></a>Ajout de nouveaux flux à chocolat
Si vous souhaitez ajouter un nouveau flux à un chocolat, à l’instar d’une `choco source add` commande, vous pouvez passer à cette étape `additionalOptions` . Un exemple d’ajout d’un nouveau flux est un [exemple d’utilisation](#example-usage). Si vous souhaitez ajouter un flux privé, nous vous recommandons d’exécuter l’outil dans l’invite de commandes, car il nécessite des informations d’identification. Par exemple, `devinit run -t choco-install -i {package} -s "{feed link}" -u {user} -p {password}` , où `{package}` , `{feed link}` , `{user}` et `{password}` font référence à votre package spécifique, à un lien de flux, un nom d’utilisateur et un mot de passe. Pour plus d’informations, consultez la documentation sur le chocolat référencé ci-dessus. 

### <a name="built-in-options"></a>Options intégrées

L' `choco-install` outil définit un certain nombre d' `choco` arguments de ligne de commande pour s’assurer que `choco` peut s’exécuter sans affichage. Ces arguments sont répertoriés ci-dessous et leur documentation est disponible dans la [documentation en chocolat](https://chocolatey.org/docs/).

| Nom                  | Description                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **--Oui**             | Confirmer toutes les invites : choisit la réponse affirmative au lieu de vous demander. Entraîne `--accept-license.` |
| **--non-Progress**     | Ne pas afficher la progression-les pourcentages de progression ne s’affichent pas.                                         |
| **--Skip-PowerShell** | Ignorer PowerShell-chocolateyInstall.ps1 ne sera pas exécuté.                                              |

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `choco-install` outil est d’erreur, car la `input` propriété est requise.

## <a name="example-usage"></a>Exemple d’utilisation
Vous trouverez ci-dessous des exemples d’exécution à `choco-install` l’aide d’un `.devinit.json` .

#### <a name="devinitjson-that-will-install-packages-listed-in-packagesconfig"></a>.devinit.jssur qui installe les packages listés dans packages.config :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "packages.config",
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-mongodb"></a>.devinit.jssur qui installe MongoDB :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "mongodb"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-mongodb"></a>.devinit.jssur qui installe une version spécifique de MongoDB :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "mongodb",
            "additionalOptions": "--version 4.2.7"
        }
    ]
}
```

#### <a name="devinitjson-that-adds-a-new-feed-to-chocolatey"></a>.devinit.jssur qui ajoute un nouveau flux au chocolat :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "packages.config",
            "additionalOptions": "-s '{feed link}'"
        }
    ]
}
```