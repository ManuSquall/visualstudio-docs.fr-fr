---
title: Commutateur setup de devenv.exe | Microsoft Docs
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e37fe50eefc36e7b5396f396d2b614851a0bd9cb
ms.sourcegitcommit: 873c0e1a31def013bcca1b0caa0eb0249de89bec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2018
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

[Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)