---
title: -DebugExe (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
ms.openlocfilehash: 065648588b51ad6c71ae1a10235da4f096470abe
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
Ouvre le fichier exécutable spécifié à déboguer.

## <a name="syntax"></a>Syntaxe

```
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

```
Devenv.exe /debugexe MyApplication.exe
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)