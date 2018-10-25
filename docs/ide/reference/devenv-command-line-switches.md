---
title: Commutateurs de la ligne de commande devenv de Visual Studio
ms.date: 02/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8a8987354af4a0b62438cea3aab3f18f4def7bfa
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49907038"
---
# <a name="devenv-command-line-switches"></a>Commutateurs de la ligne de commande devenv

devenv vous permet de définir différentes options pour l’IDE, et de créer, déboguer et déployer des projets à partir de la ligne de commande. Utilisez ces commutateurs pour exécuter l’IDE à partir d’un script ou d’un fichier .bat, par exemple un script de génération nocturne ou pour lancer l’IDE dans une configuration particulière.

> [!NOTE]
> Pour les tâches liées à la génération, nous vous recommandons d’utiliser MSBuild au lieu de devenv. Pour plus d’informations, consultez [Informations de référence sur la ligne de commande MSBuild](../../msbuild/msbuild-command-line-reference.md).

## <a name="devenv-switch-syntax"></a>Syntaxe des commutateurs devenv

Par défaut, les commandes devenv passent des commutateurs à l’utilitaire devenv.com. L’utilitaire devenv.com fournit ses sorties via des flux système standard, comme `stdout` et `stderr`. L’utilitaire détermine la redirection d’E/S appropriée lors de la capture de la sortie, par exemple dans un fichier .txt.

En revanche, les commandes qui commencent par `devenv.exe` peuvent utiliser les mêmes commutateurs, mais l’utilitaire devenv.com est alors ignoré.

Les règles de syntaxe pour les commutateurs `devenv` ressemblent à celles d’autres utilitaires de ligne de commande DOS. Les règles de syntaxe suivantes s’appliquent à tous les commutateurs `devenv` et leurs arguments :

- Les commandes commencent par `devenv`.

- Les commutateurs ne respectent pas la casse.

- Quand vous spécifiez une solution ou un projet, le premier argument est le nom du fichier solution ou projet, y compris le chemin du fichier.

- Si le premier argument est un fichier qui n’est pas une solution ou un projet, ce fichier s’ouvre dans l’éditeur approprié, dans une nouvelle instance de l’IDE.

- Quand vous fournissez un nom de fichier projet au lieu d’un nom de fichier solution, une commande `devenv` recherche le dossier parent du fichier projet pour un fichier solution du même nom. Par exemple, la commande `devenv /build myproject1.vbproj` recherche le dossier parent d’un fichier solution nommé « myproject1.sln ».

    > [!NOTE]
    > Un seul fichier solution référençant ce projet doit se trouver dans son dossier parent. Si le dossier parent ne contient aucun fichier solution référençant ce projet, ou si le dossier parent contient deux fichiers solution ou plus qui le référencent, un fichier solution temporaire est créé.

- Quand les chemins et les noms de fichier comportent des espaces, vous devez les placer entre des guillemets doubles (""). Par exemple, "c:\project a\\".

- Insérez un espace entre les commutateurs et les arguments de la même ligne. Par exemple, la commande **devenv /log output.txt** ouvre l’IDE et produit toutes les informations de journal de la session dans le fichier output.txt.

- Vous ne pouvez pas utiliser la syntaxe des critères spéciaux dans les commandes `devenv`.

## <a name="devenv-switches"></a>Commutateurs de devenv

Les commutateurs de ligne de commande suivants affichent l’IDE et effectuent la tâche décrite.

|Commutateur de ligne de commande|Description|
| - |-----------------|
|[/Command](../../ide/reference/command-devenv-exe.md)|Démarre l’IDE et exécute la commande spécifiée.|
|[/DebugExe](../../ide/reference/debugexe-devenv-exe.md)|Charge un exécutable C++ sous le contrôle du débogueur. Ce commutateur n’est pas disponible pour les exécutables Visual Basic ou C#. Pour plus d’informations, consultez [Démarrer automatiquement un processus dans le débogueur](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).|
|[/LCID ou /l](../../ide/reference/lcid-devenv-exe.md)|Spécifie la langue par défaut pour l’IDE. Si la langue spécifiée n’est pas incluse dans votre installation de Visual Studio, ce paramètre est ignoré.|
|[/Log](../../ide/reference/log-devenv-exe.md)|Démarre Visual Studio et enregistre toute l’activité dans le fichier journal.|
|[/Run ou /r](../../ide/reference/run-devenv-exe.md)|Compile et exécute la solution spécifiée.|
|[/Runexit](../../ide/reference/runexit-devenv-exe.md)|Compile et exécute la solution spécifiée, réduit l’IDE pendant l’exécution de la solution et ferme l’IDE une fois la solution exécutée.|
|[/UseEnv](../../ide/reference/useenv-devenv-exe.md)|Force l’IDE à utiliser les variables d’environnement PATH, INCLUDE et LIB pour la compilation de C++, au lieu des paramètres spécifiés dans la section Répertoires VC ++ des options de **Projets** dans la boîte de dialogue **Options**. Ce commutateur est installé avec la charge de travail **Développement Desktop avec C++**. Pour plus d’informations, consultez [Définition du chemin d’accès et des variables d’environnement pour les générations sur la ligne de commande](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds).|
|[/Edit](../../ide/reference/edit-devenv-exe.md)|Ouvre les fichiers spécifiés dans une instance en cours d’exécution de cette application. S’il n’existe aucune instance en cours d’exécution, il démarre une nouvelle instance avec une disposition de fenêtre simplifiée.|
|[/SafeMode](../../ide/reference/safemode-devenv-exe.md)|Démarre Visual Studio en mode sans échec, et charge seulement l’environnement et les services par défaut ainsi que les versions commercialisées des packages tiers.|
|[/ResetSkipPkgs](../../ide/reference/resetskippkgs-devenv-exe.md)|Efface toutes les balises SkipLoading qui ont été ajoutées aux packages Visual Studio par les utilisateurs voulant éviter de charger les Packages Visual Studio défectueux.|
|[/Setup](../../ide/reference/setup-devenv-exe.md)|Force Visual Studio à fusionner les métadonnées de ressources qui décrivent les menus, les barres d’outils et les groupes de commandes de tous les packages Visual Studio disponibles. Vous devez exécuter cette commande en tant qu’administrateur.|

Les commutateurs de ligne de commande suivants n’affichent pas l’IDE.

|Commutateur de ligne de commande|Description|
| - |-----------------|
|[/?](../../ide/reference/q-devenv-exe.md)|Affiche l’aide des commutateurs devenv dans la **fenêtre d’invite de commandes**.<br /><br /> **Devenv /?**|
|[/Build](../../ide/reference/build-devenv-exe.md)|Génère la solution ou le projet spécifié en fonction de la configuration de la solution indiquée.<br /><br /> **Devenv myproj.csproj /build**|
|[/Clean](../../ide/reference/clean-devenv-exe.md)|Supprime tous les fichiers créés par la commande build, sans affecter les fichiers sources.<br /><br /> **Devenv myproj.csproj /clean**|
|[/Deploy](../../ide/reference/deploy-devenv-exe.md)|Génère la solution, ainsi que les fichiers nécessaires pour le déploiement, en fonction de la configuration des solutions.<br /><br /> **Devenv myproj.csproj /deploy**|
|[/Diff](../../ide/reference/diff.md)|Compare deux fichiers. Prend quatre paramètres : SourceFile, TargetFile, SourceDisplayName (facultatif) et TargetDisplayName (facultatif).|
|[/Out](../../ide/reference/out-devenv-exe.md)|Permet de spécifier un fichier pour recevoir les erreurs pendant la génération.<br /><br /> **Devenv myproj.csproj /build /out log.txt**|
|[/Project](../../ide/reference/project-devenv-exe.md)|Projet à générer, nettoyer ou déployer. Vous pouvez utiliser ce commutateur uniquement si vous avez également spécifié le commutateur /build, /rebuild, /clean ou /deploy.|
|[/ProjectConfig](../../ide/reference/projectconfig-devenv-exe.md)|Spécifie la configuration de projet à générer ou déployer. Vous pouvez utiliser ce commutateur uniquement si vous avez également spécifié le commutateur /project.|
|[/Rebuild](../../ide/reference/rebuild-devenv-exe.md)|Efface, puis génère la solution ou le projet spécifié en fonction de la configuration de la solution indiquée.|
|[/ResetSettings](../../ide/reference/resetsettings-devenv-exe.md)|Restaure les paramètres par défaut de Visual Studio. Éventuellement, réinitialise les paramètres dans le fichier .vssettings spécifié.|
|[/Upgrade](../../ide/reference/upgrade-devenv-exe.md)|Met à niveau le fichier solution spécifié et tous ses fichiers projet, ou le fichier projet spécifié, avec les formats Visual Studio actuels pour ces fichiers.|

## <a name="see-also"></a>Voir aussi

* [Général, Environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)