---
title: -Command (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Command switch
- /Command Devenv switch
- Command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf8f72f0d9b0c2d847ddb2c5e7e6c3c8d4ae4467
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55932493"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)

Exécute la commande spécifiée après le lancement de l’environnement IDE Visual Studio.

## <a name="syntax"></a>Syntaxe

```shell
devenv /Command CommandName
```

## <a name="arguments"></a>Arguments

- *CommandName*

  Obligatoire. Nom complet d’une commande Visual Studio ou de son alias, entre guillemets doubles. Pour plus d’informations sur la syntaxe des commandes et des alias, consultez [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Notes

Une fois le démarrage terminé, l’IDE exécute la commande nommée. Si vous utilisez ce commutateur, l’environnement IDE n’affiche pas la page initiale de Visual Studio au démarrage.

Si un complément expose une commande, vous pouvez utiliser ce commutateur pour lancer le complément à partir de la ligne de commande. Pour plus d'informations, voir [Procédure : Contrôler les compléments avec le Gestionnaire de compléments](/previous-versions/xwdatdwh(v=vs.140)).

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
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
- [Commande, fenêtre](command-window.md)