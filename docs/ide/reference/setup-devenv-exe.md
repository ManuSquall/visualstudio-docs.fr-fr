---
title: Commutateur setup de devenv.exe
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3f1f801d4da451d9357082359a1cf001915e1041
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53829272"
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)

Le commutateur /Setup amène Visual Studio à fusionner les métadonnées des ressources qui décrivent les menus, les barres d’outils et les groupes de commandes de tous les packages Visual Studio disponibles.

## <a name="syntax"></a>Syntaxe

```shell
devenv /setup
```

## <a name="remarks"></a>Notes

Ce commutateur ne prend aucun argument. La commande `devenv /setup` est généralement utilisée comme dernière étape du processus d’installation. L’utilisation du commutateur `/setup` ne démarre pas Visual Studio.

> [!NOTE]
> Vous devez exécuter `devenv` en tant qu’administrateur pour pouvoir utiliser le commutateur `/setup`.

## <a name="example"></a>Exemple

Cet exemple montre la dernière étape de l’installation d’une version de Visual Studio qui inclut des packages Visual Studio.

```shell
devenv /setup
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)