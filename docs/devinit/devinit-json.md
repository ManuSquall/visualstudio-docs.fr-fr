---
title: Fichier de configuration devinit
description: Documentation relative à la .devinit.jssur le fichier manifeste pour devinit.
ms.date: 11/02/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: acd3b65f520a9be048fe2d0209a85a85d086df2f
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438228"
---
# <a name="devinit-configuration-file"></a>fichier de configuration devinit

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
| **Utilisez**      | tableau  | Oui      | [Objet RunTool](#run-tool-object) |

#### <a name="run-tool-object"></a>Exécuter l’objet outil

| Nom                  | Type   | Obligatoire | Valeur                                                                                                      |
|-----------------------|--------|----------|------------------------------------------------------------------------------------------------------------|
| **commentaires**          | string | Non       | Commentaires pour l’entrée de l’outil.                                                                               |
| **outil**              | string | Oui      | Nom de l'outil. Pour obtenir la `devinit list` liste des outils disponibles, consultez la commande.                            |
| **input**             | string | Non       | Entrée de l’outil. Varie en fonction de l’outil. Par exemple, la version requise, l’ID de package, le nom de fichier ou le dossier.|
| **additionalOptions** | string | Non       | Arguments de ligne de commande supplémentaires à passer à l’outil.                                                |

## <a name="examples"></a>Exemples

Pour obtenir plus d’exemples d’utilisation de devinit, consultez la [section exemples](sample-readme.md).
