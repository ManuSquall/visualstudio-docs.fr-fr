---
title: -Project (devenv.exe)
description: Découvrez comment utiliser le commutateur de ligne de commande du projet devenv pour identifier un projet unique dans la configuration de solution spécifiée afin de générer, nettoyer, régénérer ou déployer le projet.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /Project Devenv switch
- projects [Visual Studio], rebuilding
- projects [Visual Studio], building
- deployment projects, specifying
- Project Devenv switch (/Project)
- Devenv, /Project switch
- projects [Visual Studio], cleaning
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8f61125c743cb33ccaccbb15c1345aa01fbc57bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952900"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)

Identifie un projet unique dans la configuration de solution spécifiée à générer, nettoyer, regénérer ou déployer.

## <a name="syntax"></a>Syntaxe

```shell
devenv SolutionName {/Build|/Clean|/Deploy|/Rebuild} [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Arguments

- *SolutionName*

  Obligatoire. Chemin complet et nom du fichier solution.

- {`/Build`|`/Clean`|`/Deploy`|`/Rebuild`}

  Obligatoire. [Génère](build-devenv-exe.md), [nettoie](clean-devenv-exe.md), [déploie](deploy-devenv-exe.md) ou [regénère](rebuild-devenv-exe.md) le projet.

- *SolnConfigName*

  Facultatif. Nom de la configuration de solution (par exemple, `Debug` ou `Release`) appliquée à la solution nommée dans *SolutionName*. Si plusieurs plateformes de solution sont disponibles, vous devez également en spécifier une (par exemple, `Debug|Win32`). Si cet argument n’est pas spécifié ou consiste en une chaîne vide (`""`), l’outil utilise la configuration active de la solution.

- `/Project` *NomProjet*

  Facultatif. Chemin et nom d’un fichier projet dans la solution. Vous pouvez entrer le nom d’affichage du projet ou un chemin d’accès relatif du dossier *SolutionName* au fichier projet. Vous pouvez également saisir le chemin d’accès complet et le nom du fichier projet.

- `/ProjectConfig` *ProjConfigName*

  Facultatif. Nom de la configuration de build du projet (par exemple, `Debug` ou `Release`) appliquée au `/Project` nommé. Si plusieurs plateformes de solution sont disponibles, vous devez également en spécifier une (par exemple, `Debug|Win32`).

- `/Out`*OutputFileName*

  Facultatif. Nom du fichier auquel vous souhaitez envoyer la sortie de l’outil. Si le fichier existe déjà, l’outil ajoute la sortie à la fin du fichier.

## <a name="remarks"></a>Notes

- Doit être utilisé dans une `devenv` `/Build` commande, `/Clean` , `/Rebuild` ou `/Deploy` .

- Placez entre guillemets doubles les chaînes contenant des espaces.

- Vous pouvez afficher des informations récapitulatives sur les générations, notamment sur les erreurs, dans la fenêtre **Commande** ou dans tout fichier journal spécifié avec le commutateur `/Out`.

## <a name="example"></a>Exemple

Cet exemple génère le projet `CSharpWinApp` suivant la configuration de build de projet `Debug` présente dans `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
