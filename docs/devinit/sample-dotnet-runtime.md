---
title: Runtime .NET Core
description: Exemple de personnalisation à l’aide de devinit pour le référentiel dotnet/Runtime.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: d703e71b6f8ab57ab07c4143fdd5435585c6004c
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672452"
---
# <a name="net-core-runtime"></a>Runtime .NET Core

> [!IMPORTANT]
> Depuis le 12 avril 2021, la connexion à GitHub Codespaces à partir de Visual Studio 2019 ne sera plus prise en charge et cette version préliminaire privée s’est terminée. Nous nous concentrons sur les expériences en constante évolution d’une boucle interne basée sur le Cloud et de solutions VDI optimisées pour un large éventail de charges de travail Visual Studio. Dans le cadre de cet article `devinit` , les outils associés ne seront plus disponibles. Nous vous encourageons à participer au Forum de la communauté des développeurs pour Visual Studio afin d’obtenir des informations sur les futures versions préliminaires et les informations de feuille de route.

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

Contenu du [`.devinit.json`](devinit-json.md) fichier. Ce fichier doit se trouver dans le même dossier que le fichier _.devcontainer.js_ .

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
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File .\\PostCloneSetup.ps1"
}
```
