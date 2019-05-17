---
title: -DoNotLoadProjects (devenv.exe)
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a414fde4dee401016e997fa5d6890da2ae8d9d53
ms.sourcegitcommit: db30651dc0ce4d0b274479b23a6bd102a5559098
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65083930"
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
