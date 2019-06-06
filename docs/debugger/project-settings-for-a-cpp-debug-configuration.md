---
title: Paramètres de projets pour un C++ déboguer config
ms.custom: seodec18
ms.date: 11/26/2018
ms.topic: reference
f1_keywords:
- VC.Project.VCDebugSettings.WebBrowser.DebuggerType
- VC.Project.IVCGPUDebugPageObject.EnvironmentMerge
- VC.Project.VCDebugSettings.SymbolPath
- VC.Project.IVCClusterDebugPageObject.ApplicationCommand
- VC.Project.IVCRemoteDebugPageObject.WorkingDirectory
- VC.Project.VCDebugSettings.DebuggerType
- VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.SQLDebugging
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCGPUDebugPageObject.CommandArguments
- VC.Project.VCDebugSettings.CommandArguments
- VC.Project.IVCClusterDebugPageObject.MPIRunWorkingDirectory
- VC.Project.IVCLocalDebugPageObject.SQLDebugging
- VC.Project.IVCWebSvcDebugPageObject.HttpUrl
- VC.Project.IVCLocalDebugPageObject.WorkingDirectory
- VC.Project.IVCLocalDebugPageObject.CommandArguments
- VC.Project.IVCClusterDebugPageObject.MPIRunCommand
- VC.Project.IVCGPUDebugPageObject.WorkingDirectory
- VC.Project.IVCWebSvcDebugPageObject.DebuggerType
- VC.Project.IVCRemoteDebugPageObject.CommandArguments
- VC.Project.IVCRemoteDebugPageObject.DebuggerType
- VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCRemoteDebugPageObject.RemoteMachine
- VC.Project.IVCClusterDebugPageObject.MPIRunArguments
- VC.Project.IVCClusterDebugPageObject.MPIAcceptFilter
- VC.Project.IVCGPUDebugPageObject.RemoteConnection
- VC.Project.VCDebugSettings.PDBPath
- VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory
- VC.Project.VCDebugSettings.SQLDebugging
- VC.Project.VCDebugSettings.RemoteCommand
- VC.Project.IVCClusterDebugPageObject.ShimCommand
- VC.Project.IVCLocalDebugPageObject.Command
- VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCLocalDebugPageObject.Attach
- VC.Project.VCDebugSettings.Command
- VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.RemoteCommand
- VC.Project.IVCClusterDebugPageObject.ApplicationArguments
- VC.Project.IVCLocalDebugPageObject.Environment
- VC.Project.IVCGPUDebugPageObject.DeploymentDirectory
- VC.Project.IVCLocalDebugPageObject.EnvironmentMerge
- VC.Project.VCDebugSettings.Environment
- VC.Project.IVCGPUDebugPageObject.BreakpointBehavior
- VC.Project.IVCLocalDebugPageObject.DebuggerType
- VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl
- VC.Project.IVCWebSvcDebugPageObject.SQLDebugging
- VC.Project.IVCGPUDebugPageObject.AcceleratorType
- VC.Project.IVCGPUDebugPageObject.Environment
- VC.Project.VCDebugSettings.RemoteMachine
- VC.Project.IVCGPUDebugPageObject.AdditionalFilesToDeploy
- VC.Project.VCDebugSettings.WorkingDirectory
- vs.debug.builds
- VC.Project.VCDebugSettings.Attach
- VC.Project.VCDebugSettings.HttpUrl
- VC.Project.IVCClusterDebugPageObject.MPIAcceptMode
- VC.Project.IVCGPUDebugPageObject.Attach
- VC.Project.IVCRemoteDebugPageObject.AdditionalFiles
- VC.Project.IVCGPUDebugPageObject.Command
- VC.Project.VCDebugSettings.Remote
- VC.Project.IVCRemoteDebugPageObject.Attach
- VC.Project.VCDebugSettings.EnvironmentMerge
- VC.Project.IVCGPUDebugPageObject.MachineName
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DEBUG linker option
- -PDB linker option
- -Zl compiler option [C++]
- /DEBUG linker option
- /PDBSTRIPPED linker option
- /MAPINFO linker option
- -Zd compiler option [C++]
- -DEBUG linker option
- MAPINFO linker option
- /ZI compiler option [C++]
- ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debugger settings
- project settings [Visual Studio], debug configurations
- mapfiles, project settings
- debug configurations, C++
- project settings [Visual Studio]
- /PDB linker option
- -PDBSTRIPPED linker option
- debug builds, project settings
- PDB linker option
- projects [Visual Studio], debug configurations
- project configurations, debug
- Zd compiler option [C++]
- MAP linker option
- /Z7 compiler option [C++]
- .pdb files, debug build project settings
- -MAP linker option
- -MAPINFO linker option
- /Zd compiler option [C++]
- PDBSTRIPPED linker option
- -Z7 compiler option [C++]
- pdb files, debug build project settings
- /MAP linker option
ms.assetid: 860c7f13-a108-4fe5-8fca-d235cd3ca1cb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: df0b604d865c31bb389fe8955521fb61208e4c11
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66715449"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>Paramètres de projet pour une configuration Debug C++
Vous pouvez modifier les paramètres du projet pour une configuration debug C ou Visual C++ dans le **Pages de propriétés** boîte de dialogue, comme indiqué dans [Comment : Définir des configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md). Les tableaux suivants indiquent où se trouvent les paramètres du débogueur dans la boîte de dialogue **Pages de propriétés**.

> [!NOTE]
> Les paramètres de projet de débogage dans le **propriétés de Configuration/débogage** catégorie sont différentes pour les applications UWP et des composants qui sont écrits en C++. Consultez [démarrer une session de débogage (VB, c#, C++ et XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).

 Chaque paramètre de propriété de débogage est automatiquement écrit et enregistré dans le fichier « par utilisateur » (. vcxproj.user) de votre solution lorsque vous enregistrez votre solution.

 Spécifiez le débogueur à utiliser dans le **débogueur à lancer** zone de liste, comme décrit dans le tableau suivant. Votre choix affecte la sélection des propriétés affichées.

## <a name="configuration-properties-folder-debugging-category"></a>Dossier Propriétés de configuration (catégorie Débogage)

| **Paramètre** | **Description** |
| - | - |
| **Débogueur à lancer** | Spécifie le débogueur à exécuter, avec les choix suivants :<br /><br /> -   **Débogueur Windows local**<br />-   **Débogueur Windows distant**<br />-   **Débogueur de navigateur web**<br />-   **Débogueur de service web** |
| **Commande** (Débogueur Windows local) | Spécifie la commande de démarrage du programme que vous déboguez sur l'ordinateur local. |
| **Commande distante** (Débogueur Windows distant) | Chemin d'accès pour le fichier .exe sur l'ordinateur distant. Entrez le chemin d'accès tel que vous l'entreriez sur l'ordinateur distant. |
| **Arguments de la commande** (débogueur Windows Local)<br /><br /> **Arguments de commande à distance** (débogueur Windows distant) | -   Spécifie les arguments de la commande spécifiée précédemment.<br /><br /> Vous pouvez utiliser les opérateurs de redirection suivants dans cette zone :<br /><br /> < `file`<br /> Lit stdin à partir du fichier.<br /><br /> > `file`<br /> Écrit stdout dans le fichier.<br /><br /> >> `file`<br /> Ajoute stdout au fichier.<br /><br /> 2> `file`<br /> Écrit stderr dans le fichier.<br /><br /> 2>> `file`<br /> Ajoute stderr au fichier.<br /><br /> 2> &1<br /> Envoie la sortie de stderr (2) au même emplacement que stdout (1).<br /><br /> 1> &2<br /> Envoie la sortie de stdout (1) au même emplacement que stderr (2).<br /><br /> Dans la plupart des cas, ces opérateurs ne peuvent être utilisés que pour les applications console. |
| **Répertoire de travail** | Spécifie le répertoire de travail du programme en cours de débogage, par rapport au répertoire de projet où se trouve votre fichier .EXE. Si vous laissez cette zone vide, le répertoire de travail est le répertoire du projet. Pour le débogage distant, le répertoire du projet est sur le serveur distant. |
| **Attacher** (Débogueur Windows local et débogueur Windows distant) | Spécifie s'il faut démarrer ou attacher l'application. Le paramètre par défaut est Non. |
| **Nom de serveur distant** (Débogueur Windows distant) | Spécifie le nom d'un ordinateur (autre que le vôtre) sur lequel vous voulez déboguer une application.<br /><br /> La macro de génération RemoteMachine a la valeur de cette propriété ; pour plus d’informations, consultez [Macros pour les propriétés et les commandes de génération](/cpp/build/reference/common-macros-for-build-commands-and-properties). |
| **Connexion** (débogueur distant Windows) | Vous permet de commuter entre les types de connexion standard et sans authentification pour le débogage distant. Spécifiez un nom d’ordinateur distant dans la zone **Nom de serveur distant**. Les types de connexions incluent les éléments suivants :<br /><br /> -   **À distance avec authentification Windows**<br />-   **À distance sans authentification**<br /><br /> **Remarque** Le débogage distant sans authentification peut rendre l’ordinateur distant vulnérable face aux atteintes à la sécurité. Le mode Authentification Windows est plus sécurisé.<br /><br /> Pour plus d’informations, consultez [Programme d’installation du débogage distant](../debugger/remote-debugging.md). |
| **URL HTTP** (débogueur de service web et débogueur de navigateur web) | Spécifie l'URL où le projet que vous déboguez est localisé. |
| **Type de débogueur** | Spécifie le type de débogueur à utiliser : **Natif uniquement**, **managé uniquement**, **GPU uniquement**, **mixte**, **automatique** (valeur par défaut), ou **Script**.<br /><br /> -   Le type **Natif uniquement** est destiné au code C++ non managé.<br />-   Le type **Managé uniquement** est destiné au code s’exécutant sous le Common Language Runtime (code managé).<br />-   Le type **Mixte** appelle les débogueurs aussi bien pour le code managé que le code non managé.<br />-   Le type **Auto** permet de déterminer le type du débogueur en fonction des informations relatives au compilateur et au fichier .EXE.<br />-   **Script** appelle un débogueur pour les scripts.<br />-   **GPU uniquement** est destiné au code C++ AMP qui s’exécute sur un périphérique GPU ou sur le rastériseur de référence DirectX. Consultez [du code GPU débogage](../debugger/debugging-gpu-code.md). |
| **Environnement** (les débogueur Windows Local et débogueur de Windows à distance) | Spécifie les variables d'environnement du programme que vous déboguez. Utilisez la syntaxe de variable d’environnement standard (par exemple, `PATH="%SystemRoot%\..."`). Ces variables se substituent à l’environnement système ou fusionnent avec lui, selon le paramètre **Fusion de l’environnement**. Lorsque vous cliquez sur dans la colonne Paramètres, une « modification... » s’affiche. Sélectionnez ce lien pour modifier les variables d’environnement. |
| **Fusion de l’environnement** (Débogueur Windows local) | Détermine si les variables spécifiées dans la zone **Environnement** doivent fusionner avec l’environnement défini par le système d’exploitation. Le paramètre par défaut est Oui. |
| **Débogage SQL** (tous sauf le débogueur de cluster MPI) | Active le débogage de procédures SQL à partir de votre application [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]. Le paramètre par défaut est Non. |
| **Type d’accélérateur de débogage** (débogage GPU uniquement) | Spécifie le périphérique GPU à utiliser pour le débogage. L'installation des pilotes de périphériques GPU compatibles ajoutera des options supplémentaires. Le paramètre par défaut est **GPU - Émulateur de logiciel**. |
| **Comportement du point d’arrêt par défaut GPU** (débogage GPU uniquement) | Spécifie si un événement de point d'arrêt doit être déclenché pour chaque thread dans une chaîne SIMD. Le paramètre par défaut consiste à déclencher l'événement de point d'arrêt une seule fois par distorsion. |
| **Accélérateur par défaut de l’AMP** | Spécifie l'accélérateur AMP par défaut lors du débogage du code GPU. Choisissez **Accélérateur logiciel WARP** pour déterminer si un problème est causé par le matériel ou par un pilote, au lieu de votre code. |
| **Répertoire de déploiement** (Débogueur Windows distant) | Spécifie le chemin d’accès sur l’ordinateur distant où la sortie de projet sera copiée avant le lancement. Le chemin d’accès peut être un partage réseau sur l’ordinateur distant, ou il peut s’agir d’un chemin d’accès à un dossier sur l’ordinateur distant. Le paramètre par défaut est vide, ce qui signifie que la sortie du projet n'est pas copiée dans un partage réseau. Pour activer le déploiement des fichiers, vous devez cocher la case **Déployer** dans la boîte de dialogue Gestionnaire de configurations. Pour plus d'informations, voir [Procédure : créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md). |
| **Fichiers supplémentaires à déployer** (débogueur distant Windows) | Si la propriété répertoire de déploiement est définie, il s’agit d’une liste délimitée par des points-virgules des fichiers supplémentaires à copier dans le répertoire de déploiement. Le paramètre par défaut est vide, ce qui signifie qu'aucun fichier supplémentaire n'est copié dans le répertoire de déploiement. Pour activer le déploiement des fichiers, vous devez cocher la case **Déployer** dans la boîte de dialogue Gestionnaire de configurations. Pour plus d'informations, voir [Procédure : créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md). |
| **Déployer les bibliothèques runtime de débogage Visual C++** (Débogueur Windows distant) | Si la propriété du répertoire de déploiement est définie, elle spécifie si les bibliothèques d'exécution du débogage Visual C++ pour la plateforme actuelle doivent être copiées au partage réseau ou non. Le paramètre par défaut est Oui. |

## <a name="cc-folder-general-category"></a>Dossier C/C++ (catégorie Général)

|Paramètre|Description|
|-------------|-----------------|
|**Format des informations de débogage** ([/Z7, /Zd, Zi, /ZI](/cpp/build/reference/z7-zi-zi-debug-information-format))|Spécifie le type d'informations de débogage à créer pour le projet.<br /><br /> L'option par défaut (/ZI) crée une base de données du programme (PDB) pour Modifier &amp; Continuer. Pour plus d’informations, consultez [/Z7, /Zd, /Zi, /ZI (Format des informations de débogage)](/cpp/build/reference/z7-zi-zi-debug-information-format).|

## <a name="cc-folder-optimization-category"></a>Dossier C/C++ (catégorie Optimisation)

|Paramètre|Description|
|-------------|-----------------|
|**Optimization**|Spécifie si le compilateur doit optimiser le code qu'il produit. L'optimisation modifie le code exécuté. Code optimisé ne correspond plus au code source, ce qui rend le débogage plus difficile.<br /><br /> L’option par défaut (**Désactivé (/0d)** ) supprime l’optimisation. Vous pouvez développer avec l'optimisation supprimée, puis l'activez lors de la création de la version de production de votre code.|

## <a name="linker-folder-debugging-category"></a>Dossier Éditeur de liens (catégorie Débogage)

|Paramètre|Description|
|-------------|-----------------|
|**Générer des infos de débogage** ([/DEBUG](/cpp/build/reference/debug-generate-debug-info))|Indique à l’Éditeur de liens d’inclure les informations de débogage, qui auront le format spécifié par [/Z7, /Zd, Zi ou /ZI](/cpp/build/reference/z7-zi-zi-debug-information-format).|
|**Génération d’un fichier de base de données du programme** ([/PDB:nom](/cpp/build/reference/pdb-use-program-database))|Spécifiez le nom d’un fichier du programme (PDB) de la base de données dans cette zone. Vous devez sélectionner ZI ou /Zi pour Format des informations de débogage.|
|**Suppression des symboles privés** ([/PDBSTRIPPED:nomfichier](/cpp/build/reference/pdbstripped-strip-private-symbols))|Spécifiez le nom d'un fichier PDB dans cette zone si vous ne voulez pas inclure de symboles privés dans le fichier PDB. Cette option crée un second fichier PDB lorsque vous générez votre image de programme avec toute du compilateur ou l’éditeur de liens générant un fichier PDB, telles que/Debug, / Z7, / Zd. Ou /Zi. Ce second fichier PDB omet les symboles que vous ne souhaitez pas envoyer à vos clients. Pour plus d’informations, consultez [/PDBSTRIPPED (Supprimer les symboles privés)](/cpp/build/reference/pdbstripped-strip-private-symbols).|
|**Génération d’un fichier de mappage** ([/MAP](/cpp/build/reference/map-generate-mapfile))|Indique à l'Éditeur de liens de générer un fichier de mappage durant l'édition des liens. Le paramètre par défaut est Non. Pour plus d’informations, consultez l’article [/MAP (Générer fichier de mappage)](/cpp/build/reference/map-generate-mapfile).|
|**Nom de mappage** ([/Map :](/cpp/build/reference/map-generate-mapfile)*nom*)|Si vous choisissez Génération d'un fichier de mappage, vous pouvez spécifier le fichier de mappage dans cette zone. Pour plus d’informations, consultez l’article [/MAP (Générer fichier de mappage)](/cpp/build/reference/map-generate-mapfile).|
|**Mappage des exportations** ([/MAPINFO:EXPORTS](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Inclut les fonctions exportées dans le fichier de mappage. Le paramètre par défaut est Non. Pour plus d’informations, consultez [/MAPINFO (inclure des informations dans le fichier de mappage)](/cpp/build/reference/mapinfo-include-information-in-mapfile).|
|**Assembly pouvant être débogué** ([/ASSEMBLYDEBUG](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Spécifie les paramètres de l'option /ASSEMBLYDEBUG de l'Éditeur de liens. Les valeurs possibles sont :<br /><br /> -   **Pas d’attribut Debuggable émis**.<br />-   **Suivi du runtime et désactiver les optimisations (/ASSEMBLYDEBUG)** . Il s'agit de l'option par défaut,<br />-   **Pas de suivi du runtime et activer les optimisations (/ASSEMBLYDEBUG:DISABLE)** .<br />-    **\<hériter des paramètres par défaut du parent ou du projet>** .<br />-   Pour plus d’informations, consultez [/ASSEMBLYDEBUG (Ajouter DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute).|

 Vous pouvez modifier par programme ces paramètres dans le dossier Propriétés de configuration (catégorie Debug) à l’aide de l’interface Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings. Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.

## <a name="other-project-settings"></a>Autres paramètres du projet

Pour déboguer des types de projet tels que les bibliothèques statiques et les DLL, votre projet Visual Studio doit être en mesure de trouver les fichiers appropriés. Lorsque le code source est disponible, vous pouvez ajouter des bibliothèques statiques et des DLL en tant que projets distincts pour la même solution, pour faciliter le débogage. Pour plus d’informations sur la création de ces types de projets, consultez [création et utilisation d’une bibliothèque de liens dynamiques (DLL)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp) et [création d’une bibliothèque statique à l’aide](/cpp/windows/walkthrough-creating-and-using-a-static-library-cpp). Avec le code source disponible, vous pouvez également créer un nouveau projet de Visual Studio en choisissant **fichier** > **New** > **projet à partir de Code existant**.

Pour déboguer des DLL qui sont externes à votre projet, consultez [projets DLL de débogage](../debugger/debugging-dll-projects.md#vxtskdebuggingdllprojectsexternal). Si vous avez besoin de déboguer votre propre projet DLL, mais ne pas avoir accès au projet pour l’application appelante, consultez [comment déboguer à partir d’un projet de DLL](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>Voir aussi
- [Débogage du code natif](../debugger/debugging-native-code.md)
- [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)
- [Créer et gérer Visual C++ projets](/cpp/ide/creating-and-managing-visual-cpp-projects)
- [/ASSEMBLYDEBUG (Ajouter DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute)
- [Macros courantes pour les propriétés et les commandes de build](/cpp/ide/common-macros-for-build-commands-and-properties)