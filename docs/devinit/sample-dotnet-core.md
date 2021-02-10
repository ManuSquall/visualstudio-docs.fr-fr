---
title: Application .NET Core
description: Exemple de référentiel qui utilise devinit pour installer un kit SDK .NET Core spécifique.
ms.date: 11/04/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 364b3fbb0739891d1ce0f6341bb11af7f0ff76f5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943584"
---
# <a name="net-core-app"></a>Application .NET Core

Consultez le référentiel [devinit-example-dotnet-Core](https://github.com/microsoft/devinit-example-dotnet-core) pour obtenir un exemple complet d’utilisation de devinit pour installer la version de kit SDK .net Core requise dans Codespaces.

## <a name="devinitjson"></a>.devinit.json

Contenu de l' _.devinit.jssur_ le fichier dans la racine référentiel.

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
