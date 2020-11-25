---
title: -Command (devenv.exe)
description: Découvrez comment utiliser le commutateur de ligne de commande de la commande devenv pour exécuter une commande spécifiée après avoir lancé l’IDE de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Command switch
- /Command Devenv switch
- Command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bcfff93ac9cb4903c534c0d4d57387a5143b6b40
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040873"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)

Exécute la commande spécifiée après le lancement de l’environnement IDE Visual Studio.

## <a name="syntax"></a>Syntaxe

```shell
devenv /Command CommandName
```

## <a name="arguments"></a>Arguments

*CommandName*

Obligatoire. Nom complet d’une commande Visual Studio ou de son alias, entre guillemets doubles. Pour plus d’informations sur la syntaxe des commandes et des alias, consultez [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Remarques

Une fois le démarrage terminé, l’IDE exécute la commande nommée.

::: moniker range="vs-2017"

Si vous utilisez ce commutateur, l’IDE n’affiche pas la page de démarrage au démarrage.

::: moniker-end

Si un complément expose une commande, vous pouvez utiliser ce commutateur pour lancer le complément à partir de la ligne de commande. Pour plus d’informations, consultez [Comment : contrôler des compléments à l’aide du gestionnaire de compléments](/previous-versions/xwdatdwh(v=vs.140)).

## <a name="example"></a>Exemple

Le premier exemple lance Visual Studio et exécute automatiquement la macro Open Favorite Files.

Le deuxième ouvre un onglet de navigation web dans l’environnement IDE et accède au site Microsoft Docs.

Le troisième exemple crée un fichier nommé `some_file.cs` et l’ouvre dans un éditeur de code.

```shell
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"

devenv /command "navigate https://docs.microsoft.com/"

devenv /command "nf some_file.cs"
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
- [Fenêtre Commande](command-window.md)
