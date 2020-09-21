---
title: require-gitsubmodule
description: l’outil devinit requiert-gitsubmodule.
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
ms.openlocfilehash: fc96c1d0bf278018c370795d6ad5f9d22cb59bcc
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810129"
---
# <a name="require-gitsubmodule"></a>require-gitsubmodule

L' `require-gitsubmodule` outil restaure les sous-modules git pour le `.gitmodules` fichier donné. Utilise le `.gitmodules` fichier local dans le répertoire racine si aucune entrée n’est passée. En savoir plus sur les sous-modules git [ici](https://git-scm.com/book/en/v2/Git-Tools-Submodules).

## <a name="usage"></a>Usage

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Name                                             | Type   | Obligatoire | Valeur                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                                                |
| [**entrée**](#input)                              | string | Non       | `.gitmodules` chemin d’accès complet au fichier. Pour plus d’informations, consultez l' [entrée](#input) ci-dessous.               |
| [**additionalOptions**](#additional-options)     | string | Non       | Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.                     |

### <a name="input"></a>Entrée

Facultatif, `input` est utilisé pour obtenir le `.gitmodules` chemin d’accès de fichier pour la restauration. Si `input` est omis, le fichier de répertoire racine `.gitmodules` est utilisé.

### <a name="additional-options"></a>Options supplémentaires

Non utilisé.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `require-gitsubmodule` outil consiste à restaurer les sous-modules git mentionnés dans le `.gitmodules` fichier.

## <a name="example-usage"></a>Exemple d’utilisation

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "A sample dot-devinit file that restores Git submodules.'",
    "run": [
        {
            "tool": "require-gitsubmodule",
            "input": "RepoThatHasDotGitModulesFile",
            "comments": "Input specifies a folder that contains a .gitmodules file. If no input is specified, then current directory is used."
        }
    ]
}
```
