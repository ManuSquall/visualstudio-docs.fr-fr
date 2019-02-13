---
title: -Out (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /Out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /Out Devenv switch
- Out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 039456c10993199ec2265042aabc0ed5c475ccd9
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55954736"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)

Spécifie un fichier pour stocker et afficher les erreurs qui se produisent quand vous [exécutez](run-devenv-exe.md), [exécutez et quittez](runexit-devenv-exe.md), [mettez à niveau](upgrade-devenv-exe.md), [générez](build-devenv-exe.md), [regénérez](rebuild-devenv-exe.md), [nettoyez](clean-devenv-exe.md) ou [déployez](deploy-devenv-exe.md) une solution.

## <a name="syntax"></a>Syntaxe

```shell
devenv /Out FileName
```

## <a name="arguments"></a>Arguments

- *FileName*

  Obligatoire. Chemin et nom du fichier où est enregistrée la sortie au cours de la génération d’un exécutable.

## <a name="remarks"></a>Notes

Si le nom spécifié ne correspond à aucun fichier existant, le fichier est créé automatiquement. Sinon, les résultats sont ajoutés au contenu existant du fichier.

Les erreurs de build en ligne de commande s’affichent dans la fenêtre **Commande** et dans la vue Générateur de solutions de la fenêtre **Sortie**. Ce commutateur est utile pour afficher les résultats des builds sans assistance.

## <a name="example"></a>Exemple

Cet exemple exécute `MySolution` et écrit les erreurs dans le fichier `MyErrorLog.txt`.

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/RunExit (devenv.exe)](runexit-devenv-exe.md)
- [/Upgrade (devenv.exe)](upgrade-devenv-exe.md)
- [/Clean (devenv.exe)](clean-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)