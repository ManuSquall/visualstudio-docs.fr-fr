---
title: -Out (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /out Devenv switch
- out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 623f4e8a8a2f6e275c42507aa3839106f3a1dd2f
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704484"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
Spécifie un fichier pour stocker et afficher les erreurs qui se produisent quand vous exécutez, générez, regénérez ou déployez une solution.

## <a name="syntax"></a>Syntaxe

```cmd
devenv /out FileName
```

## <a name="arguments"></a>Arguments
 `FileName`

 Obligatoire. Chemin et nom du fichier où seront enregistrées les erreurs rencontrées au cours de la génération d’un exécutable.

## <a name="remarks"></a>Notes
 Si un nom de fichier qui n’existe pas est spécifié, le fichier est créé automatiquement. Si le fichier existe déjà, les résultats sont ajoutés au contenu existant du fichier.

 Les erreurs de build de ligne de commande sont affichées dans la fenêtre **Commande** et dans la vue Générateur de solutions de la fenêtre **Sortie**. Cette option s’avère utile si vous exécutez des générations sans assistance et que vous devez afficher les résultats.

## <a name="example"></a>Exemple
 Cet exemple exécute `MySolution` et écrit les erreurs dans le fichier `MyErrorLog.txt`.

```cmd
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)