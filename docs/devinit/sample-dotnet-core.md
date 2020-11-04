---
title: Application .NET Core
description: Exemple de référentiel qui utilise devinit pour installer un kit SDK .NET Core spécifique.
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
ms.openlocfilehash: 35971ac1fde5fc272f22579cc6640cbea6724db5
ms.sourcegitcommit: e132a870ec198fdcec289227f1a0c1c48fef070c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93344517"
---
# <a name="net-core-app"></a>Application .NET Core

Consultez le référentiel [DotnetCoreDevinitExample](https://github.com/microsoft/DotnetCoreDevinitExample) pour obtenir un exemple complet d’utilisation de devinit pour installer la version de kit SDK .net Core requise dans Codespaces.

## <a name="devinitjson"></a>.devinit.json

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "run": [
    {
      "comments": "Installs the .NET Core SDK specified in the global.json file.",
      "tool": "require-dotnetcoresdk"
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

## <a name="globaljson"></a>global.json

Contenu de l' _global.jssur_ le fichier dans la racine référentiel.

```json
{
  "sdk": {
    "version": "3.1.302"
  }
}
```
