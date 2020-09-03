---
title: -Out (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 075746353440462a66133cd83ed9158470d8de5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662211"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Spécifie un fichier pour stocker et afficher les erreurs qui se produisent quand vous exécutez, générez, regénérez ou déployez une solution.

## <a name="syntax"></a>Syntaxe

```
devenv /out FileName
```

## <a name="arguments"></a>Arguments
 `FileName` Obligatoire. Chemin et nom du fichier où seront enregistrées les erreurs rencontrées au cours de la génération d’un exécutable.

## <a name="remarks"></a>Notes
 Si un nom de fichier qui n’existe pas est spécifié, le fichier est créé automatiquement. Si le fichier existe déjà, les résultats sont ajoutés au contenu existant du fichier.

 Les erreurs de build de ligne de commande sont affichées dans la fenêtre **Commande** et dans la vue Générateur de solutions de la fenêtre **Sortie**. Cette option s’avère utile si vous exécutez des générations sans assistance et que vous devez afficher les résultats.

## <a name="example"></a>Exemple
 Cet exemple exécute `MySolution` et écrit les erreurs dans le fichier `MyErrorLog.txt`.

```
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>Voir aussi
 [Commutateurs de ligne de commande devenv](../../ide/reference/devenv-command-line-switches.md) [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md) [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md) [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
