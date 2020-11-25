---
title: -DoNotLoadProjects (devenv.exe)
description: Découvrez comment utiliser le commutateur de ligne de commande DoNotLoadProjects devenv pour ouvrir la solution spécifiée sans charger de projet.
ms.custom: SEO-VS-2020
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef3502a2180f7ae7ed5963deb14844b46f3dbff9
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040626"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

**Nouveau dans Visual Studio 2019 version 16.1**

Ouvre la solution spécifiée sans charger de projets. Pour plus d’informations, consultez [Solutions filtrées dans Visual Studio](../filtered-solutions.md).

## <a name="syntax"></a>Syntaxe

```shell
devenv /DoNotLoadProjects SolutionName
```

## <a name="arguments"></a>Arguments

*SolutionName*

Obligatoire. Chemin complet et nom de la solution à ouvrir.

## <a name="example"></a>Exemple

L’exemple ouvre la solution MySln.sln sans charger de projets.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>Voir aussi

- [Solutions filtrées dans Visual Studio](../filtered-solutions.md)
- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
