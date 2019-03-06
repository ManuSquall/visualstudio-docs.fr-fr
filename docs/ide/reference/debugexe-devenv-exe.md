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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05266a6f1b5ee0be22e2edc8df1c03b720844f4f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55924121"
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

## <a name="example"></a>Exemple

L’exemple suivant ouvre le fichier `MyApplication.exe` pour débogage.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)