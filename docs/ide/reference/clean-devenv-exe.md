---
title: -Clean (devenv.exe)
description: Découvrez comment utiliser le commutateur de ligne de commande Clean devenv pour nettoyer tous les fichiers intermédiaires et les répertoires de sortie.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- builds [Team System], cleaning files
- Clean Devenv switch
- /Clean Devenv switch
- Devenv, /Clean switch
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d4c3fdc30737a2266241e19ae40f840a41784cc1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963287"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)

Nettoie tous les fichiers et répertoires de sortie intermédiaires.

## <a name="syntax"></a>Syntaxe

```shell
devenv SolutionName /Clean [Config [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Arguments

- *SolutionName*

  Obligatoire. Chemin complet et nom du fichier solution.

- *Config*

  Facultatif. Configuration (par exemple, `Debug` ou `Release`) à appliquer pour nettoyer les fichiers intermédiaires de la solution nommée dans *SolutionName*. Si plusieurs plateformes de solution sont disponibles, vous devez également en spécifier une (par exemple, `Debug|Win32`). Si cet argument n’est pas spécifié ou consiste en une chaîne vide (`""`), l’outil utilise la configuration active de la solution.

- `/Project` *NomProjet*

  Facultatif. Chemin et nom d’un fichier projet dans la solution. Vous pouvez entrer le nom d’affichage du projet ou un chemin d’accès relatif du dossier *SolutionName* au fichier projet. Vous pouvez également saisir le chemin d’accès complet et le nom du fichier projet.

- `/ProjectConfig` *ProjConfigName*

  Facultatif. Nom de la configuration de build du projet (par exemple, `Debug` ou `Release`) à utiliser lors du nettoyage du `/Project` nommé. Si plusieurs plateformes de solution sont disponibles, vous devez également en spécifier une (par exemple, `Debug|Win32`). Si ce commutateur est spécifié, il remplace l’argument *Config*.

- `/Out`*OutputFileName*

  Facultatif. Nom du fichier auquel vous souhaitez envoyer la sortie de l’outil. Si le fichier existe déjà, l’outil ajoute la sortie à la fin du fichier.

## <a name="remarks"></a>Notes

Ce commutateur a la même fonction que la commande de menu **Nettoyer la Solution** dans l’environnement IDE.

Placez entre guillemets doubles les chaînes contenant des espaces.

Il est possible d’afficher une synthèse des informations de nettoyage et de build, erreurs incluses, dans la fenêtre **Commande** et dans tous les fichiers journaux spécifiés avec le commutateur [/Out](out-devenv-exe.md).

Si le commutateur `/Project` n’est pas spécifié, l’action de nettoyage est effectuée sur tous les projets de la solution, même si *FileName* a été spécifié comme fichier projet.

## <a name="example"></a>Exemple

Le premier exemple nettoie la solution `MySolution` à l’aide de la configuration par défaut spécifiée dans le fichier solution.

Le second exemple nettoie le projet `CSharpWinApp` suivant la configuration de build de projet `Debug` présente dans `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean

devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean "Debug" /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
