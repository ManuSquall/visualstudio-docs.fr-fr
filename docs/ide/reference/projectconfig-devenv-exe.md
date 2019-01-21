---
title: -ProjectConfig (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- /ProjectConfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /ProjectConfig switch
- ProjectConfig Devenv switch (/ProjectConfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a199fb7656e36720a6787557e2e0746b79795fd3
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269928"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

Spécifie une configuration de build de projet à appliquer quand vous générez, nettoyez, régénérez ou déployez le projet nommé dans l’argument `/Project`.

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

  Optionnel. Nom de la configuration de solution (par exemple, `Debug` ou `Release`) à appliquer à la solution nommée dans *SolutionName*. Si plusieurs plateformes de solution sont disponibles, vous devez également en spécifier une (par exemple, `Debug|Win32`). Si cet argument n’est pas spécifié ou consiste en une chaîne vide (`""`), l’outil utilise la configuration active de la solution.

- `/Project` *ProjName*

  Optionnel. Chemin et nom d’un fichier projet dans la solution. Vous pouvez entrer le nom d’affichage du projet ou un chemin d’accès relatif du dossier *SolutionName* au fichier projet. Vous pouvez également saisir le chemin d’accès complet et le nom du fichier projet.

- `/ProjectConfig` *ProjConfigName*

  Optionnel. Nom de la configuration de build du projet (par exemple, `Debug` ou `Release`) appliquée au `/Project` nommé. Si plusieurs plateformes de solution sont disponibles, vous devez également en spécifier une (par exemple, `Debug|Win32`).

- `/Out` *OutputFilename*

  Optionnel. Nom du fichier auquel vous souhaitez envoyer la sortie de l’outil. Si le fichier existe déjà, l’outil ajoute la sortie à la fin du fichier.

## <a name="remarks"></a>Notes

Le commutateur `/ProjectConfig` doit être utilisé avec le commutateur `/Project` dans une commande `/Build`, /`Clean`, `/Deploy` ou `/Rebuild`.

Placez les chaînes contenant des espaces entre des guillemets doubles.

Il est possible d’afficher une synthèse des informations de build, erreurs incluses, dans la fenêtre Commande et dans tous les fichiers journaux spécifiés avec le commutateur `/Out`.

## <a name="example"></a>Exemple

La commande suivante génère le projet `CSharpWinApp` suivant la configuration de build de projet `Debug` présente dans `MySolution` :

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)