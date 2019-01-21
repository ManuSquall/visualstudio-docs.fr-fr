---
title: -UseEnv (devenv.exe)
ms.date: 01/10/2019
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f238cb2c426bcb931783b68a1ba0b4f3337e18b2
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2019
ms.locfileid: "54270388"
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

- *ProjectName*

  Chemin complet et nom d’un fichier projet.

## <a name="remarks"></a>Notes

Ce commutateur affecte l’environnement IDE de Visual Studio dans les propriétés du projet de **Répertoires VC++**. Si le commutateur `/UseEnv` est spécifié, le nœud **Répertoires VC++** affiche les valeurs des variables d’environnement PATH, INCLUDE, LIBPATH et LIB. (Il indique également les valeurs de **Répertoires sources** et **Répertoires d’exclusion**.) Sinon, le nœud remplace les variables d’environnement par cinq valeurs de répertoire : **Répertoires d’exécutables**, **Répertoires d’inclusion**, **Répertoires de référence**, **Répertoires de bibliothèques** et **Répertoires de bibliothèques WinRT**.

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
- [Répertoires VC++, page de propriétés (Windows)](/cpp/ide/vcpp-directories-property-page)
