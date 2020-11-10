---
title: Version bêta privée
description: Exemples de personnalisations utilisés dans le référentiel bêta GitHub Codespaces Visual Studio preview.
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
ms.openlocfilehash: c79206295615fc984d2a95b52e0ecc0f70814e6f
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437100"
---
# <a name="private-beta"></a>Version bêta privée

Cet exemple montre comment personnaliser un codeSpace pour Visual Studio pour qu’il ait les mêmes fonctionnalités que la bêta [GitHub Codespaces](https://github.com/features/codespaces) privée initiale.

## <a name="devinitjson"></a>.devinit.json

Contenu du [`.devinit.json`](devinit-json.md) fichier. Ce fichier doit se trouver dans le même dossier que _.devcontainer.js_.

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
