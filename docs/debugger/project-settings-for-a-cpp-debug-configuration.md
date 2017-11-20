---
title: "Paramètres pour une configuration de débogage C++ du projet | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "49"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e32547d66d1bf4de73b209ac0174598da9bbb731
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2017
---
# <a name="project-settings-for-a-c-debug-configuration"></a>Paramètres de projet pour une configuration de débogage C++
Vous pouvez modifier les paramètres de projet pour une configuration debug C ou Visual C++ dans les **Pages de propriétés** boîte de dialogue, comme indiqué dans [Comment : définir Configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md). Les tableaux suivants indiquent où se trouvent les paramètres du débogueur dans le **Pages de propriétés** boîte de dialogue.  
  
> [!WARNING]
>  Les paramètres de projet debug dans le **propriétés de Configuration/débogage** catégorie pour applications UWP et les composants qui sont écrits en C++ sont différents. Consultez [démarrer une session de débogage (VB, c#, C++ et XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).  
  
 Spécifiez le débogueur à utiliser dans le **débogueur à lancer** zone de liste. Votre choix affecte la sélection des propriétés affichées.  
  
 Chaque paramètre de propriété de débogage est automatiquement écrit et enregistré dans le fichier individuel (.vcxproj.user) de votre solution chaque fois que vous enregistrez votre solution.  
  
## <a name="configuration-properties-folder-debugging-category"></a>Dossier Propriétés de configuration (catégorie Débogage)  
  
|**Paramètre**|**Description**|  
|-----------------|---------------------|  
|**Débogueur à lancer**|Spécifie le débogueur à exécuter, avec les choix suivants :<br /><br /> -   **Débogueur Windows local**<br />-   **Débogueur Windows distant**<br />-   **Débogueur de navigateur Web**<br />-   **Débogueur de Service Web**|  
|**Commande** (débogueur Windows Local)|Spécifie la commande de démarrage du programme que vous déboguez sur l'ordinateur local.|  
|**Commande à distance** (débogueur Windows distant)|Chemin d’accès pour le fichier .exe sur l’ordinateur distant. Entrez le chemin d’accès tel que vous l’entreriez sur l’ordinateur distant.|  
|**Arguments de commande** (débogueur Windows Local et débogueur Windows distant)|-Spécifie les arguments de la commande spécifiée précédemment.<br /><br /> Vous pouvez utiliser les opérateurs de redirection suivants dans cette zone :<br /><br /> < `file`<br /> Lit stdin à partir du fichier.<br /><br /> > `file`<br /> Écrit stdout dans le fichier.<br /><br /> >> `file`<br /> Ajoute stdout au fichier.<br /><br /> 2> `file`<br /> Écrit stderr dans le fichier.<br /><br /> 2>> `file`<br /> Ajoute stderr au fichier.<br /><br /> 2> &1<br /> Envoie la sortie de stderr (2) au même emplacement que stdout (1).<br /><br /> 1> &2<br /> Envoie la sortie de stdout (1) au même emplacement que stderr (2).<br /><br /> Dans la plupart des cas, ces opérateurs ne peuvent être utilisés que pour les applications console.|  
|**Répertoire de travail**|Spécifie le répertoire de travail du programme en cours de débogage, par rapport au répertoire de projet où se trouve votre fichier .EXE. Si vous laissez cette zone vide, le répertoire de travail est le répertoire du projet. Pour le débogage distant, le répertoire du projet est sur le serveur distant.|  
|**Attacher** (débogueur Windows Local et débogueur Windows distant)|Spécifie s'il faut démarrer ou attacher l'application. Le paramètre par défaut est Non.|  
|**Nom de serveur distant** (débogueur Windows distant)|Spécifie le nom d'un ordinateur (autre que le vôtre) sur lequel vous voulez déboguer une application.<br /><br /> La macro de génération RemoteMachine a est définie sur la valeur de cette propriété ; Pour plus d’informations, consultez [Macros pour les propriétés et les commandes de génération](/cpp/ide/common-macros-for-build-commands-and-properties).|  
|**Connexion** (débogueur Windows distant)|Vous permet de commuter entre les types de connexion standard et sans authentification pour le débogage distant. Spécifiez un nom d’ordinateur distant dans le **nom de serveur distant** boîte. Les types de connexions incluent les éléments suivants :<br /><br /> -   **À distance avec authentification Windows**<br />-   **À distance sans authentification**<br /><br /> **Remarque** le débogage distant sans authentification peut rendre l’ordinateur distant vulnérable aux violations de sécurité. Le mode Authentification Windows est plus sécurisé.<br /><br /> Pour plus d’informations, consultez [programme d’installation du débogage distant](../debugger/remote-debugging.md).|  
|**URL HTTP** (Web Service débogueur et débogueur de navigateur Web)|Spécifie l'URL où le projet que vous déboguez est localisé.|  
|**Type de débogueur**|Spécifie le type de débogueur à utiliser : **natif uniquement**, **managé uniquement**, **GPU uniquement**, **mixte**, **automatique**(valeur par défaut), ou **Script**.<br /><br /> -   **Natif uniquement** est du code C++ non managé.<br />-   **Managé uniquement** pour le code qui s’exécute sous le common language runtime (code managé).<br />-   **Mixte** appelle les débogueurs pour les managé et code non managé.<br />-   **Auto** détermine le type de débogueur en fonction du compilateur et les informations du fichier EXE.<br />-   **Script** appelle un débogueur pour les scripts.<br />-   **GPU uniquement** pour le code C++ AMP qui s’exécute sur un périphérique GPU ou sur le rastériseur de référence DirectX. Consultez [débogage du Code GPU](../debugger/debugging-gpu-code.md).|  
|**Environnement** (débogueur Windows Local et débogueur Windows distant)|Spécifie les variables d'environnement du programme que vous déboguez. Utilisez la syntaxe de variable d’environnement standard (par exemple, `PATH="%SystemRoot%\..."`). Ces variables se substituent l’environnement du système ou fusionnent avec l’environnement du système, en fonction de la **fusion de l’environnement** paramètre. Lorsque vous cliquez dans la colonne Paramètres, « Modifier... » s’affiche. Cliquez sur ce lien pour modifier des variables d'environnement.|  
|**Fusion de l’environnement** (débogueur Windows Local)|Détermine si les variables qui sont spécifiés dans le **environnement** zone doivent fusionner avec l’environnement défini par le système d’exploitation. Le paramètre par défaut est Oui.|  
|**Le débogage SQL** (tous sauf le débogueur de Cluster MPI)|Active le débogage de procédures SQL à partir de votre application [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]. Le paramètre par défaut est Non.|  
|**Type d’accélérateur de débogage** (débogage GPU uniquement)|Spécifie le périphérique GPU à utiliser pour le débogage. L'installation des pilotes de périphériques GPU compatibles ajoutera des options supplémentaires. Le paramètre par défaut est « GPU - Émulateur de logiciel ».|  
|**Comportement du point d’arrêt par défaut GPU** (débogage GPU uniquement)|Spécifie si un événement de point d'arrêt doit être déclenché pour chaque thread dans une chaîne SIMD. Le paramètre par défaut consiste à déclencher l'événement de point d'arrêt une seule fois par distorsion.|  
|**Accélérateur par défaut de l’amp**|Spécifie l'accélérateur AMP par défaut lors du débogage du code GPU. Choisissez **accélérateur du logiciel WARP** pour déterminer si un problème est causé par le matériel ou un pilote au lieu de votre code.|  
|**Répertoire de déploiement** (débogueur Windows distant)|Spécifie le chemin d’accès sur l’ordinateur distant où la sortie de projet sera copiée avant le lancement. Le chemin d'accès peut être un partage réseau sur l'ordinateur distant, ou il peut s'agir d'un chemin d'accès à un dossier sur l'ordinateur distant. Le paramètre par défaut est vide, ce qui signifie que la sortie du projet n'est pas copiée dans un partage réseau. Pour activer le déploiement des fichiers, vous devez également sélectionner le **déployer** case à cocher dans la boîte de dialogue Gestionnaire de Configuration. Pour plus d’informations, consultez [Guide pratique pour créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md).|  
|**Fichiers supplémentaires à déployer** (débogueur Windows distant)|Si le répertoire de déploiement est défini, il s'agit d'une liste délimitée par des points-virgules pour les fichiers supplémentaires à copier vers le répertoire de déploiement. Le paramètre par défaut est vide, ce qui signifie qu'aucun fichier supplémentaire n'est copié dans le répertoire de déploiement. Pour activer le déploiement des fichiers, vous devez également sélectionner le **déployer** case à cocher dans la boîte de dialogue Gestionnaire de Configuration. Pour plus d’informations, consultez [Guide pratique pour créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md).|  
|**Déployer les bibliothèques Runtime de débogage Visual C++** (débogueur Windows distant)|Si la propriété du répertoire de déploiement est définie, elle spécifie si les bibliothèques d'exécution du débogage Visual C++ pour la plateforme actuelle doivent être copiées au partage réseau ou non. Le paramètre par défaut est Oui.|  
  
## <a name="cc-folder-general-category"></a>Dossier C/C++ (catégorie Général)  
  
|Paramètre|Description|  
|-------------|-----------------|  
|**Format des informations de débogage** ([/Z7, / Zd, Zi, /ZI](/cpp/build/reference/z7-zi-zi-debug-information-format))|Spécifie le type d'informations de débogage à créer pour le projet.<br /><br /> L'option par défaut (/ZI) crée une base de données du programme (PDB) pour Modifier & Continuer. Pour plus d’informations, consultez [/Z7, / Zd, / Zi, /ZI (Format des informations de débogage)](/cpp/build/reference/z7-zi-zi-debug-information-format).|  
  
## <a name="cc-folder-optimization-category"></a>Dossier C/C++ (catégorie Optimisation)  
  
|Paramètre|Description|  
|-------------|-----------------|  
|**Optimization**|Spécifie si le compilateur doit optimiser le code qu'il produit. L'optimisation modifie le code exécuté. Le code optimisé ne correspond plus au code source. Par conséquent, le débogage est difficile.<br /><br /> L’option par défaut (**désactivé (/ 0d**) supprime l’optimisation. Vous pouvez développer avec l'optimisation supprimée, puis l'activez lors de la création de la version de production de votre code.|  
  
## <a name="linker-folder-debugging-category"></a>Dossier Éditeur de liens (catégorie Débogage)  
  
|Paramètre|Description|  
|-------------|-----------------|  
|**Générer des infos de débogage** ([/DEBUG](/cpp/build/reference/debug-generate-debug-info))|Indique à l'Éditeur de liens d'inclure les informations de débogage, qui auront le format spécifié par /Z7, /Zd, Zi ou /ZI.|  
|**Générer le fichier de base de données de programme** ([/PDB:name](/cpp/build/reference/pdb-use-program-database))|Spécifiez le nom d'un fichier PDB dans cette zone. Vous devez sélectionner ZI ou /Zi pour Format des informations de débogage.|  
|**Suppression des symboles privés** ([/PDBSTRIPPED:filename](/cpp/build/reference/pdbstripped-strip-private-symbols))|Spécifiez le nom d'un fichier PDB dans cette zone si vous ne voulez pas inclure de symboles privés dans le fichier PDB. Cette option crée un second fichier PDB (Program Database) lorsque vous générez votre image de programme avec toute option du compilateur ou de l'éditeur de liens générant un fichier PDB, comme /DEBUG, /Z7, /Zd. Ou /Zi. Ce second fichier PDB omet les symboles que vous ne souhaitez pas envoyer à vos clients. Pour plus d’informations, consultez l’article [/PDBSTRIPPED (Supprimer les symboles privés)](/cpp/build/reference/pdbstripped-strip-private-symbols).|  
|**Générer fichier de mappage** ([mappage](/cpp/build/reference/map-generate-mapfile))|Indique à l'Éditeur de liens de générer un fichier de mappage durant l'édition des liens. Le paramètre par défaut est Non. Pour plus d’informations, consultez l’article [/MAP (Générer fichier de mappage)](/cpp/build/reference/map-generate-mapfile).|  
|**Nom de fichier de mappage** ([mappage :](/cpp/build/reference/map-generate-mapfile)*nom*)|Si vous choisissez Génération d'un fichier de mappage, vous pouvez spécifier le fichier de mappage dans cette zone. Pour plus d’informations, consultez l’article [/MAP (Générer fichier de mappage)](/cpp/build/reference/map-generate-mapfile).|  
|**Mappage des exportations** ([/MAPINFO:EXPORTS](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Inclut les fonctions exportées dans le fichier de mappage. Le paramètre par défaut est Non. Pour plus d’informations, consultez [/MAPINFO (inclure les informations dans le fichier de mappage)](/cpp/build/reference/mapinfo-include-information-in-mapfile).|  
|**Assembly pouvant être débogué** ([/ASSEMBLYDEBUG](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Spécifie les paramètres de l'option /ASSEMBLYDEBUG de l'Éditeur de liens. Les valeurs possibles sont les suivantes :<br /><br /> -   **Pas d’attribut debuggable émis**.<br />-   **Runtime suivi et désactiver les optimisations (/ ASSEMBLYDEBUG)**. Il s'agit de l'option par défaut,<br />-   **Aucun optimizations(/ASSEMBLYDEBUG:DISABLE) runtime de suivi et activer**.<br />-   **\<hériter des paramètres par défaut parent ou du projet >**.<br />-Pour plus d’informations, consultez [/ASSEMBLYDEBUG (Ajouter DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute).|  
  
 Vous pouvez modifier par programme ces paramètres dans le dossier Propriétés de configuration (catégorie Debug) à l’aide de l’interface Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings. Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.

## <a name="other-project-settings"></a>Autres paramètres de projet

Pour déboguer des types de projet tels que des bibliothèques statiques et les DLL, votre projet Visual Studio doit être en mesure de trouver les fichiers appropriés. Lorsque le code source est disponible, vous pouvez ajouter des bibliothèques statiques et les DLL en tant que projets distincts à la même solution (Cela rend facile de débogage). Pour plus d’informations sur la création de ces types de projets, consultez [création et à l’aide d’une bibliothèque de liens dynamiques (DLL)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp) et [création d’une bibliothèque statique à l’aide](/cpp/windows/walkthrough-creating-and-using-a-static-library-cpp). Avec le code source disponible, vous pouvez également créer un nouveau projet Visual Studio en choisissant **fichier > Nouveau > projet à partir de Code existant**.

Pour déboguer des DLL qui sont externes à votre projet, consultez [projets DLL de débogage](../debugger/debugging-dll-projects.md#vxtskdebuggingdllprojectsexternal). Si vous devez déboguer votre propre projet DLL, mais ne pas avoir accès au projet pour l’application appelante, consultez [le débogage à partir d’un projet de DLL](../debugger/how-to-debug-from-a-dll-project.md).
  
## <a name="see-also"></a>Voir aussi  
 [Débogage du code natif](../debugger/debugging-native-code.md)   
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)   
 [Création et gestion de projets Visual C++](/cpp/ide/creating-and-managing-visual-cpp-projects)   
 [/ASSEMBLYDEBUG (Ajouter DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute)   
 [Macros courantes pour les propriétés et les commandes de génération](/cpp/ide/common-macros-for-build-commands-and-properties)