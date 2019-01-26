---
title: -NoSplash (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /NoSplash switch
- /NoSplash Devenv switch
- NoSplash Devenv switch
author: DennisLee-DennisLee
ms.author: v-dele
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 794934ab0bddcc90a36accf639b26e5ecc6bab30
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54233143"
---
# <a name="nosplash-devenvexe"></a>/NoSplash (devenv.exe)

Empêche l’écran de démarrage de s’afficher.

## <a name="syntax"></a>Syntaxe

```shell
devenv /NoSplash [File1[ FileN]...]
```

## <a name="arguments"></a>Arguments

- *File1*

  Optionnel. Fichier à ouvrir dans une instance existante de Visual Studio. S’il n’en existe pas, une instance est créée avec une disposition de fenêtre simplifiée ; l’outil ouvre *File1* dans cette nouvelle instance.

- *FileN*

  Optionnel. Un ou plusieurs fichiers supplémentaires à ouvrir dans l’instance existante de Visual Studio.

## <a name="remarks"></a>Notes

Ce commutateur masque l’écran de démarrage. S’il est omis, l’écran de démarrage s’affiche. Si vous voulez examiner en détail l’écran de démarrage (par exemple, pour vérifier l’icône de produit VSPackage), utilisez le commutateur [/Splash](../../extensibility/devenv-command-line-switches-for-vspackage-development.md).

Le commutateur `/NoSplash` peut être combiné avec d’autres commutateurs, par exemple, [/Run](run-devenv-exe.md) ou [/DebugExe](debugexe-devenv-exe.md).

## <a name="example"></a>Exemple

Les trois exemples ouvrent l’environnement IDE sans afficher l’écran de démarrage. Le deuxième compile également la solution spécifiée et exécute l’exécutable généré. Le troisième ouvre l’exécutable spécifié pour permettre son débogage dans l’environnement IDE.

```shell
devenv /nosplash

devenv /nosplash /run MySolution.sln

devenv /nosplash /debugexe MySolution.exe
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Commutateurs de ligne de commande devenv pour le développement VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)