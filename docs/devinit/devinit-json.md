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
ms.openlocfilehash: 2b6cc27d2614f71c85988457ab9bb64228bbaebb
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399965"
---
# <a name="devinit-configuration-file"></a>fichier de configuration devinit

## <a name="file-location"></a>Emplacement du fichier

La `devinit.exe init` commande est pilotée par le _.devinit.jsdans_ le fichier. Par défaut, `devinit.exe` recherche le fichier aux emplacements suivants :

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

Le _.devinit.jssur_ le fichier peut également être spécifié explicitement à l’aide de l' `--file` / `-f` option.

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
