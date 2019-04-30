---
title: -DoNotLoadProjects (devenv.exe)
ms.date: 03/11/2019
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
ms.openlocfilehash: de757e7022339b11f6d7c04ea7315abf685da24c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63428045"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

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
