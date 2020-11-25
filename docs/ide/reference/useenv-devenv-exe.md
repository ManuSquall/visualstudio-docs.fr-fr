---
title: -UseEnv (devenv.exe)
description: Découvrez comment utiliser le commutateur de ligne de commande UseEnv devenv pour démarrer Visual Studio et charger certaines variables d’environnement pour la compilation.
ms.custom: SEO-VS-2020
ms.date: 01/10/2019
ms.topic: reference
f1_keywords:
- VC.Project.UseEnvVars.ExcludePath
- VC.Project.UseEnvVars.LibraryPath
- VC.Project.UseEnvVars.SourcePath
- VC.Project.UseEnvVars.Include
- VC.Project.UseEnvVars.Path
- VC.Project.UseEnvVars.ReferencePath
helpviewer_keywords:
- UseEnv switch
- /UseEnv Devenv switch
- Devenv, /UseEnv
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51b47156b73d81f427c08e62006dc6e457e5780b
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040938"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Lance Visual Studio et charge certaines variables d’environnement pour la compilation.

> [!NOTE]
> Ce commutateur est installé avec la charge de travail **Développement Desktop avec C++**.

## <a name="syntax"></a>Syntaxe

```shell
devenv /UseEnv {SolutionName|ProjectName}
```

## <a name="arguments"></a>Arguments

- *SolutionName*

  Chemin complet et nom d’un fichier solution.

- *Nom du projet*

  Chemin complet et nom d’un fichier projet.

## <a name="remarks"></a>Remarques

Ce commutateur affecte l’environnement IDE de Visual Studio dans les propriétés du projet de **Répertoires VC++**. Si le commutateur `/UseEnv` est spécifié, le nœud **Répertoires VC++** affiche les valeurs des variables d’environnement PATH, INCLUDE, LIBPATH et LIB. (Il affiche également les valeurs des **répertoires sources** et des **répertoires d’exclusion**.) Dans le cas contraire, le nœud remplace les variables d’environnement par cinq valeurs de répertoire : **répertoires exécutables**, **répertoires Include**, répertoires de **référence**, **répertoires de bibliothèques** et **répertoires WinRT** de la bibliothèque.

> [!TIP]
> Pour accéder aux propriétés du projet, cliquez avec le bouton droit sur un projet C++ et sélectionnez **Propriétés**. Dans la boîte de dialogue **Pages de propriétés**, sélectionnez **Propriétés de configuration**, puis **Répertoires VC++**.

Lorsqu’un nom de projet est spécifié avec ce commutateur, l’outil affiche les variables d’environnement de tous les projets de la solution parente du projet.

## <a name="example"></a>Exemple

L’exemple suivant lance Visual Studio et charge les variables d’environnement dans la page de propriétés de la solution `MySolution`.

```shell
devenv.exe /useenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Répertoires VC++, page de propriétés (Windows)](/cpp/build/reference/vcpp-directories-property-page)
