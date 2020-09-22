---
title: Runtime .NET Core
description: Exemple de personnalisation à l’aide de devinit pour le référentiel dotnet/Runtime.
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
ms.openlocfilehash: b38490217a384e748ae97ec4b808f197b4af3b7b
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005651"
---
# <a name="net-core-runtime"></a>Runtime .NET Core

Cet exemple montre comment personnaliser le Runtime .NET Core [dotnet/Runtime](https://github.com/dotnet/runtime) pour qu’il soit automatiquement approvisionné avec [GitHub Codespaces](https://github.com/features/codespaces).

## <a name="postclonesetupps1"></a>PostCloneSetup.ps1

Ce script est appelé à partir de _PostCloneSetup.ps1_ et peut également être exécuté localement pour configurer le référentiel. Ce fichier doit se trouver dans le même dossier que _.devcontainer.js_.

```console
devinit init
git config --system core.longpaths true
```

## <a name="packagesconfig"></a>packages.config

Le fichier _packages.config_ est un fichier en [chocolat](https://chocolatey.org/) qui définit la liste des packages en chocolat à installer. Ce fichier doit se trouver dans le même dossier que _.devcontainer.js_.

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
    <package id="python" version="3.8.3"  />
    <package id="cmake" version="3.17.3"  />
</packages>
```

## <a name="devinitjson"></a>.devinit.json

Contenu du [_.devinit.jssur_](devinit-json.md) le fichier. Ce fichier doit se trouver dans le même dossier que _.devcontainer.jssur_ le fichier.

```json
{
    "run": [
        {
            "tool": "require-dotnetcoresdk"
        },
        {
            "tool": "choco-install",
            "input": "packages.config"
        },
        {
            "tool": "require-vscomponent"
        }
    ]
}
```

## <a name="devcontainerjson"></a>.devcontainer.js

Contenu de l' _.devcontainer.jssur_ le fichier dans la racine référentiel.

```json
{
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File PostCloneSetup.ps1"
}
```
