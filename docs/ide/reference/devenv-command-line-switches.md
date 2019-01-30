---
title: Commutateurs de la ligne de commande devenv
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0bc159ffb4fe330f52cf8364fc9f0d07b4bc5979
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55016198"
---
# <a name="devenv-command-line-switches"></a>Commutateurs de ligne de commande Devenv

Devenv permet de définir différentes options pour l’environnement IDE et de générer, déboguer et déployer des projets en ligne de commande. Utilisez ces commutateurs pour exécuter l’environnement IDE à partir d’un script ou d’un fichier .bat (par exemple, un script de build nocturne) ou pour le lancer dans une configuration particulière.

> [!NOTE]
> Pour les tâches de build, nous recommandons d’utiliser MSBuild plutôt que devenv. Pour plus d’informations, consultez [Informations de référence sur la ligne de commande MSBuild](../../msbuild/msbuild-command-line-reference.md).

Pour plus d’informations sur les commutateurs liés au développement VSPackage, voir aussi [Commutateurs de ligne de commande devenv pour le développement VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md).

## <a name="devenv-switch-syntax"></a>Syntaxe des commutateurs devenv

Les commandes qui commencent par `devenv` sont gérées par l’utilitaire `devenv.com`, qui fournit ses sorties via des flux système standard, tels que `stdout` et `stderr`. L’utilitaire détermine la redirection d’E/S appropriée lors de la capture de la sortie, par exemple dans un fichier .txt.

Les commandes qui commencent par `devenv.exe` peuvent utiliser les mêmes commutateurs, mais l’utilitaire `devenv.com` est alors ignoré. L’utilisation de `devenv.exe` empêche l’affichage direct de la sortie sur la console.

Les règles syntaxiques des commutateurs `devenv` ressemblent à celles d’autres utilitaires de ligne de commande DOS. Les règles de syntaxe suivantes s’appliquent à tous les commutateurs `devenv` et leurs arguments :

- Les commandes commencent par `devenv`.

- Les commutateurs ne respectent pas la casse.

- Pour spécifier un commutateur, on utilise un trait d’union («- ») ou une barre oblique (« / »).

- Quand vous spécifiez une solution ou un projet, le premier argument est le nom du fichier solution ou projet, y compris le chemin du fichier.

- Si le premier argument est un fichier qui n’est ni une solution ni un projet, ce fichier s’ouvre dans l’éditeur adapté, dans une nouvelle instance de l’environnement IDE.

- Quand vous fournissez un nom de fichier projet au lieu d’un nom de fichier solution, une commande `devenv` recherche le dossier parent du fichier projet pour un fichier solution du même nom. Par exemple, la commande `devenv myproject1.vbproj /build` recherche le dossier parent d’un fichier solution nommé `myproject1.sln`.

  > [!NOTE]
  > Un seul fichier solution référençant ce projet doit se trouver dans son dossier parent. Si le dossier parent ne contient aucun fichier solution référençant ce projet, ou si le dossier parent contient deux fichiers solution ou plus qui le référencent, un fichier solution temporaire est créé.

- Quand les chemins et les noms de fichier comportent des espaces, vous devez les placer entre des guillemets doubles (""). Par exemple, `"c:\project a\"`.

- Insérez un espace entre les commutateurs et les arguments de la même ligne. Par exemple, la commande `devenv /log output.txt` ouvre l’environnement IDE et écrit toutes les informations de journal de cette session dans le fichier output.txt.

- Il n’est pas possible d’utiliser une syntaxe de type critères spéciaux dans les commandes `devenv`.

## <a name="devenv-switches"></a>Commutateurs de devenv

Les commutateurs de ligne de commande suivants affichent l’environnement IDE et effectuent la tâche décrite.

|Commutateur de ligne de commande|Description|
| - |-----------------|
|[/Command](command-devenv-exe.md)|Démarre l’IDE et exécute la commande spécifiée.<br /><br /> `devenv /command "nav https://docs.microsoft.com/"`|
|[/DebugExe](debugexe-devenv-exe.md)|Charge un exécutable C++ sous le contrôle du débogueur. Ce commutateur n’est pas disponible pour les exécutables Visual Basic ou C#. Pour plus d’informations, consultez [Démarrer automatiquement un processus dans le débogueur](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).<br /><br /> `devenv /debugexe mysln.exe`|
|[/Diff](diff.md)|Compare deux fichiers. Accepte quatre paramètres : *SourceFile*, *TargetFile*, *SourceDisplayName* (facultatif) et *TargetDisplayName* (facultatif).<br /><br /> `devenv /diff File1 File2 Alias1 Alias2`|
|[/Edit](edit-devenv-exe.md)|Ouvre les fichiers spécifiés dans une instance en cours d’exécution de cette application. S’il n’existe aucune instance en cours d’exécution, il démarre une nouvelle instance avec une disposition de fenêtre simplifiée.<br /><br /> `devenv /edit File1 File2`|
|[/LCID ou /L](lcid-devenv-exe.md)|Spécifie la langue par défaut pour l’IDE. Si la langue spécifiée n’est pas incluse dans votre installation de Visual Studio, ce paramètre est ignoré.<br /><br /> `devenv /l 1033`|
|[/Log](log-devenv-exe.md)|Démarre Visual Studio et enregistre toute l’activité dans le fichier journal.<br /><br /> `devenv /log mylogfile.xml`|
|[/NoSplash](nosplash-devenv-exe.md)|Ouvre l’environnement IDE sans afficher l’écran de démarrage.<br /><br /> `devenv /nosplash File1 File2`|
|[/Run ou /R](run-devenv-exe.md)|Compile et exécute la solution spécifiée.<br /><br /> `devenv /run mysln.sln`|
|[/RunExit](runexit-devenv-exe.md)|Compile et exécute la solution spécifiée, réduit l’IDE pendant l’exécution de la solution et ferme l’IDE une fois la solution exécutée.<br /><br /> `devenv /runexit mysln.sln`|
|[/SafeMode](safemode-devenv-exe.md)|Lance Visual Studio en mode sans échec. Ce commutateur charge uniquement l’environnement par défaut, les services par défaut et les versions commercialisées des packages tiers.<br /><br /> Ce commutateur ne prend aucun argument.|
|[/UseEnv](useenv-devenv-exe.md)|Force l’environnement IDE à utiliser les variables d’environnement PATH, INCLUDE, LIBPATH et LIB pour la compilation C++. Ce commutateur est installé avec la charge de travail **Développement Desktop avec C++**. Pour plus d’informations, consultez [Définition du chemin d’accès et des variables d’environnement pour les générations sur la ligne de commande](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds).|

Les commutateurs de ligne de commande suivants n’affichent pas l’environnement IDE.

|Commutateur de ligne de commande|Description|
| - |-----------------|
|[/?](q-devenv-exe.md)|Affiche l’aide des commutateurs `devenv` dans la **fenêtre d’invite de commandes**.<br /><br /> Ce commutateur ne prend aucun argument.|
|[/Build](build-devenv-exe.md)|Génère la solution ou le projet spécifié en fonction de la configuration de la solution indiquée.<br /><br /> `devenv mysln.sln /build`|
|[/Clean](clean-devenv-exe.md)|Supprime tous les fichiers créés par la commande build, sans affecter les fichiers sources.<br /><br /> `devenv mysln.sln /clean`|
|[/Deploy](deploy-devenv-exe.md)|Génère la solution, ainsi que les fichiers nécessaires au déploiement, en fonction de la configuration de la solution.<br /><br /> `devenv mysln.sln /deploy`|
|[/Out](out-devenv-exe.md)|Permet de spécifier un fichier pour recevoir les erreurs pendant la génération.<br /><br /> `devenv mysln.sln /build Debug /out log.txt`|
|[/Project](project-devenv-exe.md)|Projet à générer, nettoyer ou déployer. Ce commutateur n’est utilisable que si le commutateur `/Build`, `/Rebuild`, `/Clean` ou `/Deploy` est également indiqué.<br /><br /> `devenv mysln.sln /build Debug /project proj1`|
|[/ProjectConfig](projectconfig-devenv-exe.md)|Spécifie la configuration de projet à générer ou déployer. Ce commutateur n’est utilisable que si le commutateur `/Project` est également indiqué.<br /><br /> `devenv mysln.sln /build Release /project proj1 /projectconfig Release`|
|[/Rebuild](rebuild-devenv-exe.md)|Efface, puis génère la solution ou le projet spécifié en fonction de la configuration de la solution indiquée.<br /><br /> `devenv mysln.sln /rebuild`|
|[/ResetSettings](resetsettings-devenv-exe.md)|Restaure les paramètres par défaut de Visual Studio. Éventuellement, réinitialise les paramètres dans le fichier `.vssettings` spécifié.<br /><br /> `devenv /resetsettings mysettings.vssettings`|
|[/Upgrade](upgrade-devenv-exe.md)|Met à niveau le fichier solution spécifié et tous ses fichiers projet, ou le fichier projet spécifié, avec les formats Visual Studio actuels pour ces fichiers.<br /><br /> `devenv mysln.sln /upgrade`|

## <a name="see-also"></a>Voir aussi

- [Général, Environnement, boîte de dialogue Options](general-environment-options-dialog-box.md)
- [Commutateurs de ligne de commande devenv pour le développement VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
