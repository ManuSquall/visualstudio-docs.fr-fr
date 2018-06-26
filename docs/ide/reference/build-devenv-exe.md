---
title: Build, commutateur DevEnv
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds, command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
- command-line builds
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 777347ba36cf3443a509d1d6c8c44c23a86901e0
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764967"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)

Génère une solution à l’aide d’un fichier de configuration de solution spécifié.

## <a name="syntax"></a>Syntaxe

```cmd
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]
```

## <a name="arguments"></a>Arguments

|||
|-|-|
|*SolutionName*|Obligatoire. Chemin complet et nom du fichier solution.|
|*SolnConfigName*|Obligatoire. Nom de la configuration de solution à utiliser pour générer la solution nommée dans *SolutionName*. Si plusieurs plateformes de solution sont disponibles, vous devez également spécifier la plateforme, par exemple **« Debug\|Win32 »**.|
|/project *ProjName*|Facultative. Chemin et nom d’un fichier projet dans la solution. Vous pouvez entrer un chemin relatif du dossier *SolutionName* au fichier projet, le nom d’affichage du projet, ou le chemin et le nom complet du fichier projet.|
|/projectconfig *ProjConfigName*|Facultative. Nom d’une configuration de build de projet à utiliser durant la génération du projet nommé. Si plusieurs plateformes de projet sont disponibles, vous devez également spécifier la plateforme, par exemple **« Debug\|Win32 »**.|

## <a name="remarks"></a>Notes

- Le commutateur **/build** a la même fonction que la commande de menu **Générer la solution** dans l’IDE (environnement de développement intégré).

- Placez les chaînes contenant des espaces entre des guillemets doubles.

- Vous pouvez afficher les informations récapitulatives des builds, notamment les erreurs, dans la fenêtre Commande ou dans un fichier journal spécifié à l’aide du commutateur **/out**.

- Le commutateur **/build** génère uniquement les projets qui ont changé depuis la dernière build. Pour générer tous les projets d’une solution, utilisez plutôt [/rebuild](../../ide/reference/rebuild-devenv-exe.md).

- Si vous obtenez un message d’erreur indiquant **Configuration de projet non valide**, vérifiez que vous avez spécifié une plateforme de solution ou une plateforme de projet, par exemple **« Debug\|Win32 »**.

## <a name="example"></a>Exemple

La commande suivante permet de générer le projet « CSharpConsoleApp », à l’aide de la configuration de build de projet « Debug » dans la configuration de solution « Debug » de « MySolution ».

```cmd
devenv "C:\Visual Studio Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Voir aussi

- [Générer et nettoyer des projets et des solutions](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)