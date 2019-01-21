---
title: -Rebuild (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /rebuild switch
- Rebuild Devenv switch (/Rebuild)
- projects [Visual Studio], rebuilding
- /Rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 208bc533578d116fe55ad336f4aaee72eec94c3f
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2019
ms.locfileid: "54268567"
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)

Nettoie, puis génère la configuration de solution spécifiée.

## <a name="syntax"></a>Syntaxe

```shell
devenv SolutionName /Rebuild [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Arguments

- *SolutionName*

  Obligatoire. Chemin complet et nom du fichier solution.

- *SolnConfigName*

  Optionnel. Nom de la configuration de solution (par exemple, `Debug` ou `Release`) à utiliser pour regénérer la solution nommée dans *SolutionName*. Si plusieurs plateformes de solution sont disponibles, vous devez également en spécifier une (par exemple, `Debug|Win32`). Si cet argument n’est pas spécifié ou consiste en une chaîne vide (`""`), l’outil utilise la configuration active de la solution.

- `/Project` *ProjName*

  Optionnel. Chemin et nom d’un fichier projet dans la solution. Vous pouvez entrer le nom d’affichage du projet ou un chemin d’accès relatif du dossier *SolutionName* au fichier projet. Vous pouvez également saisir le chemin d’accès complet et le nom du fichier projet.

- `/ProjectConfig` *ProjConfigName*

  Optionnel. Nom de la configuration de build du projet (par exemple, `Debug` ou `Release`) à utiliser lors de la regénération du `/Project` nommé. Si plusieurs plateformes de solution sont disponibles, vous devez également en spécifier une (par exemple, `Debug|Win32`). Si ce commutateur est spécifié, il remplace l’argument *SolnConfigName*.

- `/Out` *OutputFilename*

  Optionnel. Nom du fichier auquel vous souhaitez envoyer la sortie de l’outil. Si le fichier existe déjà, l’outil ajoute la sortie à la fin du fichier.

## <a name="remarks"></a>Notes

- Ce commutateur a la même fonction que la commande de menu **Régénérer la solution** dans l’environnement IDE.

- Placez entre guillemets doubles les chaînes contenant des espaces.

- Il est possible d’afficher une synthèse des informations de nettoyage et de build, erreurs incluses, dans la fenêtre **Commande** et dans tous les fichiers journaux spécifiés avec le commutateur [/Out](out-devenv-exe.md).

## <a name="example"></a>Exemple

Cet exemple nettoie et regénère le projet `CSharpWinApp` suivant la configuration de build de projet `Debug` présente dans `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)