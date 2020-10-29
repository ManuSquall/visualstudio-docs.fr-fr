---
title: Application .NET Core
description: Exemple de référentiel qui utilise devinit pour installer un kit SDK .NET Core spécifique.
ms.date: 10/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: ce94dc9cf4b6368a96cc027e1a9fc14e0d7e0650
ms.sourcegitcommit: 7915cedf2f5988db25cb90042aa8466a1d3cee7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "93028146"
---
# <a name="net-core-app"></a>Application .NET Core

Consultez le référentiel [DevinitExample](https://github.com/microsoft/DevinitExample) pour obtenir un exemple complet d’utilisation de devinit pour installer la version de kit SDK .net Core requise dans Codespaces.

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