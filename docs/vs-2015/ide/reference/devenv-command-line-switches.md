---
title: Commutateurs de la ligne de commande Devenv │ Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- builds [Team System], command-line
- applications [Visual Studio], executing
- compiling source code, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
- environment, Devenv commands
- compilers, Devenv commands
- switches
- Devenv, syntax and list of switches
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
caps.latest.revision: 36
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c3e6a888a5f904c194bcdb6f5c844dbed3084449
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54754969"
---
# <a name="devenv-command-line-switches"></a>Commutateurs de la ligne de commande de Devenv
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Devenv vous permet de définir diverses options pour l’environnement de développement intégré (IDE) et également de créer, déboguer et déployer des projets à partir de la ligne de commande. Utilisez ces commutateurs pour exécuter l’IDE à partir d’un script ou d’un fichier .bat, par exemple, un script de génération nocturne, ou pour lancer l’IDE avec une configuration particulière.  
  
> [!NOTE]
>  Pour les tâches de génération, nous vous recommandons d’utiliser MSBuild au lieu de devenv. Pour plus d’informations, consultez [Informations de référence sur la ligne de commande](../../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
>  Vous devez exécuter devenv en tant qu’administrateur pour pouvoir utiliser les commutateurs [/setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) et [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md).  
  
## <a name="devenv-switch-syntax"></a>Syntaxe des commutateurs devenv  
 Par défaut, les commandes devenv passent des commutateurs à l’utilitaire devenv.com.  
  
 L’utilitaire devenv.com permet de générer la sortie par le biais de flux système standard, comme `stdout` et `stderr`, et détermine la redirection d’E/S appropriée pendant la capture de la sortie, par exemple, vers un fichier .txt. Les commandes qui commencent plutôt par `devenv.exe` peuvent utiliser les mêmes commutateurs, mais les envoient au programme devenv.exe en contournant l’utilitaire devenv.com.  
  
 Les règles de syntaxe pour les commutateurs `devenv` ressemblent à celles d’autres utilitaires de ligne de commande DOS. Les règles de syntaxe suivantes s’appliquent à tous les commutateurs `devenv` et leurs arguments :  
  
-   Les commandes commencent par `devenv`.  
  
-   Les commutateurs ne respectent pas la casse.  
  
-   Quand vous spécifiez une solution ou un projet, le premier argument est le nom du fichier solution ou projet, y compris le chemin du fichier.  
  
-   Si le premier argument est un fichier qui n’est pas une solution ou un projet, ce fichier s’ouvre dans l’éditeur approprié, dans une nouvelle instance de l’IDE.  
  
-   Quand vous fournissez un nom de fichier projet au lieu d’un nom de fichier solution, une commande `devenv` recherche le dossier parent du fichier projet pour un fichier solution du même nom. Par exemple, la commande `devenv /build myproject1.vbproj` recherche le dossier parent d’un fichier solution nommé « myproject1.sln ».  
  
    > [!NOTE]
    >  Un seul fichier solution référençant ce projet doit se trouver dans son dossier parent. Si le dossier parent ne contient aucun fichier solution référençant ce projet, ou si le dossier parent contient au moins deux fichiers solution qui le référencent, un fichier solution temporaire est créé, qui est nommé pour ce projet et y fait référence.  
  
-   Quand les chemins et les noms de fichier comportent des espaces, vous devez les placer entre guillemets doubles (""). Par exemple, "c:\project a\\".  
  
-   Insérez un espace entre les commutateurs et les arguments de la même ligne. Par exemple, la commande **devenv /log output.txt** ouvre l’IDE et produit toutes les informations de journal de la session dans le fichier output.txt.  
  
-   Vous ne pouvez pas utiliser la syntaxe des critères spéciaux dans les commandes `devenv`.  
  
## <a name="devenv-switches"></a>Commutateurs devenv  
 Utilisez les commutateurs de ligne de commande suivants pour afficher l’IDE et effectuer la tâche décrite.  
  
|Commutateur de ligne de commande|Description|  
|-------------------------|-----------------|  
|[/Command (devenv.exe)](../../ide/reference/command-devenv-exe.md)|Démarre l’IDE et exécute la commande spécifiée.|  
|[/DebugExe (devenv.exe)](../../ide/reference/debugexe-devenv-exe.md)|Charge un exécutable [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] sous le contrôle du débogueur. Ce commutateur n’est pas disponible pour les exécutables [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. Pour plus d’informations, consultez [Démarrer automatiquement un processus dans le débogueur](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).|  
|[/LCID (devenv.exe)](../../ide/reference/lcid-devenv-exe.md) ou `/l`|Spécifie la langue par défaut pour l’IDE. Si la langue spécifiée n’est pas incluse dans votre installation de Visual Studio, ce paramètre est ignoré.|  
|[/Log (devenv.exe)](../../ide/reference/log-devenv-exe.md)|Démarre [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] et enregistre toute l’activité dans le fichier journal.|  
|[/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md) ou `/r`|Compile et exécute la solution spécifiée.|  
|[/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)|Compile et exécute la solution spécifiée, réduit l’IDE pendant l’exécution de la solution et ferme l’IDE une fois la solution exécutée.|  
|[/UseEnv (devenv.exe)](../../ide/reference/useenv-devenv-exe.md)|Force l’IDE à utiliser les variables d’environnement PATH, INCLUDE et LIB pour la compilation de [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] au lieu des paramètres spécifiés dans la section Répertoires VC ++ des options de **Projets** dans la boîte de dialogue **Options**. Pour plus d’informations, consultez [Définition du chemin et des variables d’environnement pour les générations sur la ligne de commande](http://msdn.microsoft.com/library/99389528-deb5-43b9-b99a-03c8773ebaf4)|  
|[/Edit (devenv.exe)](../../ide/reference/edit-devenv-exe.md)|Ouvre les fichiers spécifiés dans une instance en cours d’exécution de cette application. S’il n’existe aucune instance en cours d’exécution, démarre une nouvelle instance avec une disposition de fenêtre simplifiée.|  
|[/ResetAddin (devenv.exe)](../../ide/reference/resetaddin-devenv-exe.md)|Démarre une instance de l’IDE Visual Studio sans charger le complément spécifié.|  
|[/SafeMode (devenv.exe)](../../ide/reference/safemode-devenv-exe.md)|Démarre [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] en mode sans échec et charge uniquement l’environnement et les services par défaut ainsi que les versions commercialisées des packages tiers.|  
|[/ResetSkipPkgs (devenv.exe)](../../ide/reference/resetskippkgs-devenv-exe.md)|Efface toutes les balises SkipLoading qui ont été ajoutées aux packages Visual Studio par les utilisateurs voulant éviter de charger les Packages Visual Studio défectueux.|  
|[/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md)|Force Visual Studio à fusionner les métadonnées de ressources qui décrivent les menus, les barres d’outils et les groupes de commandes de tous les packages Visual Studio disponibles.|  
  
 Utilisez les commutateurs de ligne de commande suivants pour effectuer la tâche décrite. Ces commutateurs de ligne de commande n’affichent pas l’IDE.  
  
|Commutateur de ligne de commande|Description|  
|-------------------------|-----------------|  
|[/? (devenv.exe)](../../ide/reference/q-devenv-exe.md)|Affiche l’aide des commutateurs devenv dans la **fenêtre d’invite de commandes**.<br /><br /> **Devenv /?**|  
|[/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)|Génère la solution ou le projet spécifié en fonction de la configuration de la solution indiquée.<br /><br /> **Devenv myproj.csproj /build**|  
|[/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)|Supprime tous les fichiers créés par la commande build, sans affecter les fichiers sources.<br /><br /> **Devenv myproj.csproj /clean**|  
|[/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)|Génère la solution, ainsi que les fichiers nécessaires pour le déploiement, en fonction de la configuration des solutions.<br /><br /> **Devenv myproj.csproj /deploy**|  
|[/Diff](../../ide/reference/diff.md)|Compare deux fichiers.  Accepte quatre paramètres : SourceFile, TargetFile, SourceDisplayName (facultatif), TargetDisplayName (facultatif).|  
|[/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md)|Enregistre les modèles de projet ou d’élément qui se trouvent dans *\<VisualStudioInstallDir>* \Common7\IDE\ProjectTemplates ou *\<VisualStudioInstallDir>* \Common7\IDE\ItemTemplates pour qu’ils soient accessibles dans les boîtes de dialogue **Nouveau projet** et **Ajouter un nouvel élément**.<br /><br /> **Devenv /InstallVSTemplates**|  
|[/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)|Permet de spécifier un fichier pour recevoir les erreurs pendant la génération.<br /><br /> **Devenv myproj.csproj /build /out log.txt**|  
|[/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)|Projet à générer, nettoyer ou déployer. Vous pouvez utiliser ce commutateur uniquement si vous avez également spécifié le commutateur /build, /rebuild, /clean ou /deploy.|  
|[/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)|Spécifie la configuration de projet à générer ou déployer. Vous pouvez utiliser ce commutateur uniquement si vous avez également spécifié le commutateur /project.|  
|[/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)|Efface, puis génère la solution ou le projet spécifié en fonction de la configuration de la solution indiquée.|  
|[/ResetSettings (devenv.exe)](../../ide/reference/resetsettings-devenv-exe.md)|Restaure les paramètres par défaut de Visual Studio. Éventuellement, réinitialise les paramètres dans le fichier .vssettings spécifié.|  
|[/Updateconfiguration (devenv.exe)](../../ide/reference/updateconfiguration-devenv-exe.md)|Notifie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pour qu’il fusionne les packages [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sur le système et vérifie si des modifications ont été apportées au cache MEF.|  
|[/Upgrade (devenv.exe)](../../ide/reference/upgrade-devenv-exe.md)|Met à niveau le fichier solution spécifié et tous ses fichiers projet, ou le fichier projet spécifié, vers les formats [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] actuels pour ces fichiers.|  
  
## <a name="see-also"></a>Voir aussi  
 [Général, Environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)
