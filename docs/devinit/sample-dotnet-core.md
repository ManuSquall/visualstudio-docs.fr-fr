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
ms.openlocfilehash: b3e25835f305a96b2205fc96cc0200d68ad033af
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672459"
---
# <a name="net-core-app"></a>Application .NET Core

> [!IMPORTANT]
> Depuis le 12 avril 2021, la connexion à GitHub Codespaces à partir de Visual Studio 2019 ne sera plus prise en charge et cette version préliminaire privée s’est terminée. Nous nous concentrons sur les expériences en constante évolution d’une boucle interne basée sur le Cloud et de solutions VDI optimisées pour un large éventail de charges de travail Visual Studio. Dans le cadre de cet article `devinit` , les outils associés ne seront plus disponibles. Nous vous encourageons à participer au Forum de la communauté des développeurs pour Visual Studio afin d’obtenir des informations sur les futures versions préliminaires et les informations de feuille de route.

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
