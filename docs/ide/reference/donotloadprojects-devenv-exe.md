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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fb43d3a12e50d3f4a7af43721a5e93b769da28ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907594"
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
