---
title: -DebugExe (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
- debugging executables
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aeae28288936b6723b53e826142a4888ad0bc8b4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570139"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)

Ouvre le fichier exécutable spécifié à déboguer.

## <a name="syntax"></a>Syntaxe

```shell
devenv /DebugExe ExecutableFile
```

## <a name="arguments"></a>Arguments

- *ExecutableFile*

  Obligatoire. Chemin d’accès et nom d’un fichier `.exe`. Si le fichier `.exe` est introuvable ou n’existe pas, aucun avertissement ni erreur ne s’affiche et Visual Studio démarre normalement.

## <a name="remarks"></a>Notes 

Toute chaîne qui suit le paramètre *ExecutableFile* est transmise à ce fichier comme argument.

## <a name="example"></a> Exemple

L’exemple suivant ouvre le fichier `MyApplication.exe` pour débogage.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
