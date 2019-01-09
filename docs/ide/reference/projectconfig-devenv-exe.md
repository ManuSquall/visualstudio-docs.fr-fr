---
title: ProjectConfig, commutateur DevEnv
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- /projectconfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /projectconfig switch
- projectconfig Devenv switch (/projectconfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7ca481d23757cc9022042db42a6d4be477880367
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53967915"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

Spécifie une configuration de build de projet à appliquer quand vous générez, nettoyez, regénérez ou déployez le projet nommé dans l’argument **/project**.

## <a name="syntax"></a>Syntaxe

```cmd
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Arguments

|||
|-|-|
|/build|Génère le projet spécifié par l’argument **/project**.|
|/clean|Nettoie tous les fichiers intermédiaires et répertoires de sortie créés pendant une génération.|
|/rebuild|Nettoie, puis génère le projet spécifié par l’argument **/project**.|
|/deploy|Spécifie que le projet doit être déployé après une génération ou une régénération.|
|*SolnConfigName*|Obligatoire. Nom de la configuration de solution à appliquer à la solution nommée dans *SolutionName*. Si plusieurs plateformes de solution sont disponibles, vous devez également spécifier la plateforme, par exemple **« Debug\|Win32 »**.|
|*SolutionName*|Obligatoire. Chemin complet et nom du fichier solution.|
|/project *ProjName*|Optionnel. Chemin et nom d’un fichier projet dans la solution. Vous pouvez entrer un chemin relatif du dossier *SolutionName* au fichier projet, le nom d’affichage du projet, ou le chemin et le nom complet du fichier projet.|
|/projectconfig *ProjConfigName*|Optionnel. Nom d’une configuration de build de projet à appliquer au projet spécifié par l’argument **/project**. Si plusieurs plateformes de solution sont disponibles, vous devez également spécifier la plateforme, par exemple **« Debug\|Win32 »**.|

## <a name="remarks"></a>Notes

Vous devez utiliser le commutateur **/projectconfig** avec le commutateur **/project** dans une commande **/build**, **/clean**, **/rebuild** ou **/deploy**.

Placez les chaînes contenant des espaces entre des guillemets doubles.

Vous pouvez afficher les informations récapitulatives des builds, notamment les erreurs, dans la fenêtre Commande ou dans un fichier journal spécifié à l’aide du commutateur **/out**.

## <a name="example"></a>Exemple

La commande suivante permet de générer le projet « CSharpConsoleApp », à l’aide de la configuration de build de projet « Debug » dans la configuration de solution « Debug » de « MySolution » :

```cmd
devenv "C:\Visual Studio Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)