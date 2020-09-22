---
title: Version préliminaire privée
description: Exemples de personnalisations utilisés dans GitHub Codespaces Visual Studio Preview bêta référentiel.
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
ms.openlocfilehash: 61ef0a0575e5b86ab7cbd7c17e37c552c0c14388
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005630"
---
# <a name="private-preview"></a>Préversion privée

Cet exemple montre comment personnaliser un codeSpace pour Visual Studio pour qu’il ait les mêmes fonctionnalités que la bêta [GitHub Codespaces](https://github.com/features/codespaces) privée initiale.

## <a name="devinitjson"></a>.devinit.json

Contenu du [_.devinit.jssur_](devinit-json.md) le fichier. Ce fichier doit se trouver dans le même dossier que _.devcontainer.js_.

```json
{
    "run": [
        {
            "tool": "choco-install",
            "input": "python2"
        },
        {
            "tool": "choco-install",
            "input": "python3"
        },
        {
            "tool": "require-dotnetcoresdk",
            "input": "2.1.807"
        },
        {
            "tool": "require-dotnetcoresdk"
        },
        {
            "tool": "require-nodejs"
        },
        {
            "tool": "require-azurecli"
        },
        {
            "tool": "require-nodejs"
        },
        {
            "tool": "require-mssql"
        },
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-ef",
            "additionalOptions": "--global"
        },
        {
            "tool": "require-vcpkg"
        }
    ]
}
```

## <a name="devcontainerjson"></a>.devcontainer.js

Contenu de l' _.devcontainer.jssur_ le fichier dans la racine référentiel.

```json
{
  "postCreateCommand": "devinit init"
}
```
