---
title: Fichier de configuration devinit
description: Documentation relative à la .devinit.jssur le fichier manifeste pour devinit.
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
ms.openlocfilehash: b0cfb1c41d7721598bae44f950ced01d17ff494a
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005359"
---
# <a name="devinit-configuration-file"></a>fichier de configuration devinit

## <a name="file-location"></a>Emplacement du fichier

La `devinit.exe init` commande est pilotée par le _.devinit.jsdans_ le fichier. Par défaut, `devinit.exe` recherche le fichier aux emplacements suivants :

- _{Current-Directory}\\_
- _{Current-Directory} \\ . devinit\\_
- _{Current-Directory} \\ . devcontainer\\_

L’élément de langage _._ dans le répertoire, les noms de fichiers peuvent être omis.

Le _.devinit.jssur_ le fichier peut également être spécifié explicitement à l’aide de l' `--file` / `-f` option.

### <a name="directories-and-relative-paths"></a>Répertoires et chemins d’accès relatifs

Les chemins d’accès sont relatifs à l’emplacement d’exécution de devinit. Il s’agit généralement du répertoire de travail actuel à partir duquel `devinit` a été exécuté.

## <a name="file-format"></a>Format de fichier

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
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
