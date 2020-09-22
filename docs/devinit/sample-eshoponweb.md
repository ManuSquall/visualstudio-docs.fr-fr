---
title: eShopOnWeb
description: Exemple de personnalisation à l’aide de devinit pour la référentiel dotnet-architecture/eShopOnWeb.
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
ms.openlocfilehash: 052e89d276e122ebf44c2b541771bbb314f48ade
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809103"
---
# <a name="eshoponweb"></a>eShopOnWeb

Cet exemple montre comment personnaliser l’exemple d’architecture dotnet [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb) pour le configurer automatiquement avec [GitHub Codespaces](https://github.com/features/codespaces).

## <a name="postclonesetupps1"></a>PostCloneSetup.ps1

Ce script est appelé à partir de _PostCloneSetup.ps1_ et peut également être exécuté localement pour configurer le référentiel. Ce fichier doit se trouver dans le même dossier que _.devcontainer.js_.

```batch
devinit init
dotnet ef database update -c catalogcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
dotnet ef database update -c appidentitydbcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
```

## <a name="devinitjson"></a>.devinit.js

Contenu du [_.devinit.jssur_](devinit-json.md) le fichier. Ce fichier doit se trouver dans le même dossier que _.devcontainer.js_.

```json
{
    "run": [
        {
            "tool": "require-dotnetcoresdk"
        },
        {
            "tool": "require-mssql"
        },
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-ef",
            "additionalOptions": "--global"
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
