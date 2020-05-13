---
title: -UseEnv (devenv.exe)
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
ms.openlocfilehash: 35808b27964b3ca8fa0488f1be2ce6dc5530b3dd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596392"
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

- *Projectname*

  Chemin complet et nom d’un fichier projet.

## <a name="remarks"></a>Notes 

Ce commutateur affecte l’environnement IDE de Visual Studio dans les propriétés du projet de **Répertoires VC++**. Si le commutateur `/UseEnv` est spécifié, le nœud **Répertoires VC++** affiche les valeurs des variables d’environnement PATH, INCLUDE, LIBPATH et LIB. (Il montre également des valeurs pour **les annuaires source** et **exclure les annuaires**.) Sinon, le nœud remplace les variables de l’environnement par cinq valeurs d’annuaire : **Répertoires exécutables,** **Inclure des annuaires, annuaires** **de référence,** **annuaires de bibliothèque,** et **répertoires de la bibliothèque WinRT**.

> [!TIP]
> Pour accéder aux propriétés du projet, cliquez avec le bouton droit sur un projet C++ et sélectionnez **Propriétés**. Dans la boîte de dialogue **Pages de propriétés**, sélectionnez **Propriétés de configuration**, puis **Répertoires VC++**.

Lorsqu’un nom de projet est spécifié avec ce commutateur, l’outil affiche les variables d’environnement de tous les projets de la solution parente du projet.

## <a name="example"></a> Exemple

L’exemple suivant lance Visual Studio et charge les variables d’environnement dans la page de propriétés de la solution `MySolution`.

```shell
devenv.exe /useenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Répertoires VC++, page de propriétés (Windows)](/cpp/build/reference/vcpp-directories-property-page)
