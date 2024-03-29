---
title: Fichier de configuration devinit
description: Documentation relative à la .devinit.jssur le fichier manifeste pour devinit.
ms.date: 11/02/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 4f94ee609ba4c0783a06648ed037e58d864aa2a9
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672206"
---
# <a name="devinit-configuration-file"></a>fichier de configuration devinit

> [!IMPORTANT]
> Depuis le 12 avril 2021, la connexion à GitHub Codespaces à partir de Visual Studio 2019 ne sera plus prise en charge et cette version préliminaire privée s’est terminée. Nous nous concentrons sur les expériences en constante évolution d’une boucle interne basée sur le Cloud et de solutions VDI optimisées pour un large éventail de charges de travail Visual Studio. Nous vous encourageons à participer au Forum de la communauté des développeurs pour Visual Studio afin d’obtenir des informations sur les futures versions préliminaires et les informations de feuille de route.

Le `.devinit.json` fichier définit les dépendances à l’ensemble du système nécessaires à l’exécution et à la génération de votre application. Les dépendances à l’ensemble du système sont des éléments tels que Node.js, SQL Server, IIS, RabbitMQ, docker, etc. Il s’agit de l’ordre des choses que vous devriez normalement installer sur votre boîte de développement qui ne sont pas installées par un référentiel spécifique. Il ne s’agit pas d’un endroit pour définir des dépendances spécifiques à l’application, comme vous le feriez dans des gestionnaires de packages tels que NuGet ou NPM. Toutefois, il s’agit d’un emplacement pour définir que vous avez besoin de ces gestionnaires de packages.

## <a name="file-location"></a>Emplacement du fichier

La `devinit init` commande est pilotée par le `.devinit.json` fichier. Par défaut, `devinit` recherche le fichier aux emplacements suivants :

* {Current-Directory} \\.devinit.js
* {Current-Directory} \\devinit.js
* {Current-Directory} \\ . devinit \\.devinit.js
* {Current-Directory} \\ . devinit \\devinit.js
* {Current-Directory} \\ devinit \\.devinit.js
* {Current-Directory} \\ devinit \\devinit.js
* {Current-Directory} \\ . devcontainer \\.devinit.js
* {Current-Directory} \\ . devcontainer \\devinit.js

> [!NOTE]
> Si plusieurs fichiers par défaut sont trouvés, devinit utilise le fichier qui apparaît en premier dans la liste ci-dessus.

Le `.devinit.json` fichier peut également être spécifié explicitement par le biais de l' `--file` / `-f` option.

### <a name="directories-and-relative-paths"></a>Répertoires et chemins d’accès relatifs

Les chemins d’accès sont relatifs à l’emplacement d’exécution de devinit. Il s’agit généralement du répertoire de travail actuel à partir duquel `devinit` a été exécuté.

## <a name="file-format"></a>Format de fichier
Dans un `.devinit.json` , vous pouvez spécifier plusieurs outils à exécuter. Dans la `run` section, vous pouvez placer n’importe quel nombre d’objets. Un exemple est illustré dans notre exemple [.devinit.js](sample-all-tool.md) avec tous nos outils.

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "string",
    "run": [
        {
            "comments": "string",
            "tool": "string",
            "input": "string|null|undefined",
            "additionalOptions": "string|null|undefined"
        }
    ]
}
```

### <a name="property-values"></a>Valeurs de propriétés

| Nom         | Type   | Obligatoire | Valeur                              |
|--------------|--------|----------|------------------------------------|
| **commentaires** | string | Non       | Commentaires pour le fichier.             |
| **Exécuter**      | tableau  | Oui      | [Objet RunTool](#run-tool-object) |

#### <a name="run-tool-object"></a>Exécuter l’objet outil

| Nom                  | Type   | Obligatoire | Valeur                                                                                                      |
|-----------------------|--------|----------|------------------------------------------------------------------------------------------------------------|
| **commentaires**          | string | Non       | Commentaires pour l’entrée de l’outil.                                                                               |
| **outil**              | string | Oui      | Nom de l'outil. Pour obtenir la `devinit list` liste des outils disponibles, consultez la commande.                            |
| **input**             | string | Non       | Entrée de l’outil. Varie en fonction de l’outil. Par exemple, la version requise, l’ID de package, le nom de fichier ou le dossier.|
| **additionalOptions** | string | Non       | Arguments de ligne de commande supplémentaires à passer à l’outil.                                                |

## <a name="examples"></a>Exemples

Pour obtenir plus d’exemples d’utilisation de devinit, consultez la [section exemples](sample-readme.md).
