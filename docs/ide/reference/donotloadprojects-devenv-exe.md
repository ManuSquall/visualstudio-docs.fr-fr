---
title: -DoNotLoadProjects (devenv.exe)
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34fe7dfed2774eace7d32b1c9041355b566d4e76
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654491"
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

Requis. Chemin complet et nom de la solution à ouvrir.

## <a name="example"></a>Exemple

L’exemple ouvre la solution MySln.sln sans charger de projets.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>Voir aussi

- [Solutions filtrées dans Visual Studio](../filtered-solutions.md)
- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
