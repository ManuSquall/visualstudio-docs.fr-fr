---
title: -Out (devenv.exe)
description: Découvrez comment utiliser le commutateur de ligne de commande Out devenv pour spécifier un fichier de stockage et d’affichage des erreurs lors de l’exécution, de l’exécution et de la sortie, de la mise à niveau, de la génération, de la régénération, du nettoyage ou du déploiement d’une solution.
ms.custom: SEO-VS-2020
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06409d3b7e3d218fcf2b81dce7ea58d3202b7e21
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040054"
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

## <a name="remarks"></a>Remarques

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
