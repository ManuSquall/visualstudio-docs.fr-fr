---
title: -Build (devenv.exe)
description: Découvrez le commutateur de ligne de commande de génération devenv et comment l’utiliser pour générer une solution ou un projet avec un fichier de configuration de solution spécifié.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- builds, command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
- command-line builds
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 32e7f14647729f167b4dc816519d398a00467547
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836435"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)

Génère une solution ou un projet à l’aide d’un fichier de configuration de solution spécifié.

## <a name="syntax"></a>Syntaxe

```shell
devenv SolutionName /Build [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Arguments

- *SolutionName*

  Obligatoire. Chemin complet et nom du fichier solution.

- *SolnConfigName*

  Facultatif. Nom de la configuration de solution (par exemple, `Debug` ou `Release`) à utiliser pour générer la solution nommée dans *SolutionName*. Si plusieurs plateformes de solution sont disponibles, vous devez également en spécifier une (par exemple, `Debug|Win32`). Si cet argument n’est pas spécifié ou consiste en une chaîne vide (`""`), l’outil utilise la configuration active de la solution.

- `/Project` *NomProjet*

  Facultatif. Chemin et nom d’un fichier projet dans la solution. Vous pouvez entrer un chemin relatif du dossier *SolutionName* au fichier projet, le nom d’affichage du projet, ou le chemin et le nom complet du fichier projet.

- `/ProjectConfig` *ProjConfigName*

  Facultatif. Nom d’une configuration de build de projet (par exemple, `Debug` ou `Release`) à utiliser lors de la génération du projet nommé. Si plusieurs plateformes de solution sont disponibles, vous devez également en spécifier une (par exemple, `Debug|Win32`). Si ce commutateur est spécifié, il remplace l’argument *SolnConfigName*.

- `/Out`*OutputFileName*

  Facultatif. Nom du fichier auquel vous souhaitez envoyer la sortie de l’outil. Si le fichier existe déjà, l’outil ajoute la sortie à la fin du fichier.

## <a name="remarks"></a>Remarques

- Le commutateur `/Build` a la même fonction que la commande de menu **Générer la solution** dans l’environnement de développement intégré (IDE).

- Placez les chaînes contenant des espaces entre des guillemets doubles.

- Il est possible d’afficher une synthèse des informations de build, erreurs incluses, dans la fenêtre Commande et dans tous les fichiers journaux spécifiés avec le commutateur `/Out`.

- Le commutateur `/Build` ne génère que les projets qui ont changé depuis la dernière build. Pour générer tous les projets d’une solution, utilisez plutôt [/rebuild](../../ide/reference/rebuild-devenv-exe.md).

- Si vous obtenez un message d’erreur indiquant **Configuration de projet non valide**, vérifiez que vous avez spécifié une plateforme de solution ou de projet (par exemple, `Debug|Win32`).

## <a name="example"></a>Exemple

La commande suivante génère le projet `CSharpWinApp` suivant la configuration de build de projet `Debug` présente dans `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Voir aussi

- [Générer et nettoyer des projets et des solutions](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
