---
title: -DebugExe (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 99f256b47125f4e07ca5dc148c4351871389a94b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889408"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
Ouvre le fichier exécutable spécifié à déboguer.

## <a name="syntax"></a>Syntaxe

```cmd
Devenv /debugexe ExecutableFile
```

## <a name="arguments"></a>Arguments
 `ExecutableFile`

 Obligatoire. Chemin et nom d’un fichier .exe.

 Si le fichier .exe est introuvable ou n’existe pas, aucun avertissement ni erreur ne s’affiche et [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] démarre normalement.

## <a name="remarks"></a>Notes
 Toute chaîne qui suit le paramètre `ExecutableFile` est passée à ce fichier comme argument.

## <a name="example"></a>Exemple
 L’exemple suivant ouvre le fichier `MyApplication.exe` pour débogage.

```cmd
Devenv.exe /debugexe MyApplication.exe
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)