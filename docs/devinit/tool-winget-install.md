---
title: winget-installer
description: outil devinit pour winget.
ms.date: 02/08/2021
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 4a2ad1ef30692d7d23f2d450f0ba32d6f38f8262
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672623"
---
# <a name="winget-install"></a>winget-installer

> [!IMPORTANT]
> Depuis le 12 avril 2021, la connexion à GitHub Codespaces à partir de Visual Studio 2019 ne sera plus prise en charge et cette version préliminaire privée s’est terminée. Nous nous concentrons sur les expériences en constante évolution d’une boucle interne basée sur le Cloud et de solutions VDI optimisées pour un large éventail de charges de travail Visual Studio. Dans le cadre de cet article `devinit` , les outils associés ne seront plus disponibles. Nous vous encourageons à participer au Forum de la communauté des développeurs pour Visual Studio afin d’obtenir des informations sur les futures versions préliminaires et les informations de feuille de route.

L' `winget-install` outil est utilisé pour installer des [packages Winget](https://docs.microsoft.com/windows/package-manager/winget/).

## <a name="usage"></a>Utilisation

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil génère une erreur.

| Nom                                         | Type   | Obligatoire | Valeur                                                                             |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------------|
| **commentaires**                                 | string | Non       | Propriété de commentaires facultative. Non utilisé.                                             |
| [**entrée**](#input)                          | string | Non       | Le package à installer. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous.                    |
| [**additionalOptions**](#additional-options) | string | Non       | Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.                  |

### <a name="input"></a>Entrée

La propriété d’entrée est utilisée pour spécifier le `Id` ou le `Name` du package à installer (par exemple, MongoDB. Server'). La valeur d’entrée sera ajoutée à une `winget install` commande (par exemple `winget install MongoDB.Server` ). Si le nom du package n’est pas unique et correspond à d’autres packages, vous pouvez spécifier le `Id` du package et ajouter l' `--exact` indicateur à pour `additionalOptions` vérifier que l’identité du package correspond exactement. Le `Id` d’un package peut être trouvé en exécutant la `winget search` commande et en utilisant le `Id` paramètre d’un package.  

### <a name="additional-options"></a>Options supplémentaires

Des options de configuration supplémentaires peuvent être transmises en tant que valeur de additionalOptions. Ces arguments sont directement dirigés vers les arguments utilisés par `winget install` et sont définis dans la `winget install` [documentation](https://docs.microsoft.com/windows/package-manager/winget/install).

#### <a name="manifests"></a>Manifestes

Un autre facultatif qui `winget` prend en charge la possibilité de fournir un [fichier manifeste](https://docs.microsoft.com/windows/package-manager/winget/install#local-install) pour détailler le package à installer. Pour utiliser cette fonctionnalité avec devinit `input` , le paramètre doit être vide et la `additionalOptions` propriété doit inclure l' `--manifest` option suivie du chemin d’accès au manifeste (par exemple `--manifest path.to.manifest.yml` ).

### <a name="built-in-options"></a>Options intégrées

L’outil Winget-install définit un certain nombre d’arguments de ligne de commande Winget pour s’assurer que Winget peut s’exécuter sans écran. Ces arguments sont répertoriés ci-dessous et leur documentation est disponible dans la `winget install` [documentation](https://docs.microsoft.com/windows/package-manager/winget/install).

| Nom     | Description                                                                                                                       |
|----------|-----------------------------------------------------------------------------------------------------------------------------------|
| --Silent | Exécute le programme d’installation en mode silencieux. Vous ne voyez aucune invite s’afficher. L’expérience par défaut montre la progression du programme d’installation.                       | 

## <a name="example-usage"></a>Exemple d’utilisation

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-6.0",
    "run": [
        {
            "comments": "Installs Microsoft PowerToys.",
            "tool": "winget-install",
            "input": "Microsoft.PowerToys",
            "additionalOptions": "--version 0.15.2",
        },
        {
            "comments": "Installs PostgreSQL.",
            "tool": "winget-install",
            "input": "PostgreSQL.PostgreSQL",
            "additionalOptions": "--exact"
        },
        {
            "comments": "Installs the package defined in winget-manifest.yml.",
            "tool": "winget-install",
            "additionalOptions": "--manifest winget-manifest.yml"
        }
    ]
}
```
