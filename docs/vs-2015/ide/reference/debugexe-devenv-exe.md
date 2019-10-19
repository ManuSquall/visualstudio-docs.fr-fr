---
title: -DebugExe (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f472add6b821693d1d48397e878db19e707e2868
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660805"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ouvre le fichier exécutable spécifié à déboguer.

## <a name="syntax"></a>Syntaxe

```
Devenv /debugexe ExecutableFile
```

## <a name="arguments"></a>Arguments
 `ExecutableFile` Obligatoire. Chemin et nom d’un fichier .exe.

 Si le fichier .exe est introuvable ou n’existe pas, aucun avertissement ni erreur ne s’affiche et [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] démarre normalement.

## <a name="remarks"></a>Remarques
 Toute chaîne qui suit le paramètre `ExecutableFile` est passée à ce fichier comme argument.

## <a name="example"></a>Exemples
 L’exemple suivant ouvre le fichier `MyApplication.exe` pour débogage.

```
Devenv.exe /debugexe MyApplication.exe
```

## <a name="see-also"></a>Voir aussi
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
