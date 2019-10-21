---
title: -Deploy (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Deploy switch
- Deploy Devenv switch
- deploying applications [Visual Studio], after build
- /Deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ff5f79b2482c2e025957872892a585e08bbfa8d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661662"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)

Déploie une solution après une génération ou une regénération. S’applique aux projets de code managé uniquement.

## <a name="syntax"></a>Syntaxe

```shell
devenv SolutionName /Deploy [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Arguments

- *SolutionName*

  Requis. Chemin complet et nom du fichier solution.

- *SolnConfigName*

  Optionnel. Nom de la configuration de solution (par exemple, `Debug` ou `Release`) à utiliser pour générer la solution nommée dans *SolutionName*. Si plusieurs plateformes de solution sont disponibles, vous devez également en spécifier une (par exemple, `Debug|Win32`). Si cet argument n’est pas spécifié ou consiste en une chaîne vide (`""`), l’outil utilise la configuration active de la solution.

- `/Project` *ProjName*

  Optionnel. Chemin et nom d’un fichier projet dans la solution. Vous pouvez entrer le nom d’affichage du projet ou un chemin d’accès relatif du dossier *SolutionName* au fichier projet. Vous pouvez également saisir le chemin d’accès complet et le nom du fichier projet.

- `/ProjectConfig` *ProjConfigName*

  Optionnel. Nom d’une configuration de build de projet (par exemple, `Debug` ou `Release`) à utiliser lors de la génération du `/Project` nommé. Si plusieurs plateformes de solution sont disponibles, vous devez également en spécifier une (par exemple, `Debug|Win32`). Si ce commutateur est spécifié, il remplace l’argument *SolnConfigName*.

- `/Out` *OutputFilename*

  Optionnel. Nom du fichier auquel vous souhaitez envoyer la sortie de l’outil. Si le fichier existe déjà, l’outil ajoute la sortie à la fin du fichier.

## <a name="remarks"></a>Notes

Le projet spécifié doit être un projet de déploiement. Si ce n’est pas le cas, une erreur se produit au moment du déploiement du projet généré, qui échoue.

Placez entre guillemets doubles les chaînes contenant des espaces.

Il est possible d’afficher une synthèse des informations de build, erreurs incluses, dans la fenêtre **Commande** et dans tous les fichiers journaux spécifiés avec le commutateur [/Out](out-devenv-exe.md).

## <a name="example"></a>Exemple

Cet exemple déploie le projet `CSharpWinApp` suivant la configuration de build de projet `Release` présente dans `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)