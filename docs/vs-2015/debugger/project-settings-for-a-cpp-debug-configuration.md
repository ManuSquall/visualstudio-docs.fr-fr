---
title: Paramètres pour une Configuration de débogage C++ du projet | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
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
- FSharp
- VB
- CSharp
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
caps.latest.revision: 52
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05667c982daa35910bb1d4e1d895fb2bef50fb78
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193464"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>Paramètres de projet pour une configuration Debug C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez modifier les paramètres du projet pour une configuration debug C ou Visual C++ dans le **Pages de propriétés** boîte de dialogue, comme indiqué dans [Comment : définir Configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md). Les tableaux suivants indiquent où trouver les paramètres du débogueur dans le **Pages de propriétés** boîte de dialogue.  
  
> [!WARNING]
>  Les paramètres de projet de débogage dans le **propriétés de Configuration/débogage** catégorie pour les applications du Windows Store et les composants qui sont écrits en C++ sont différents. Consultez [démarrer une session de débogage (VB, c#, C++ et XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) dans le centre de développement Windows.  
  
 Spécifiez le débogueur à utiliser dans le **débogueur à lancer** zone de liste. Votre choix affecte la sélection des propriétés affichées.  
  
 Chaque paramètre de propriété de débogage est automatiquement écrit et enregistré dans le fichier individuel (.vcxproj.user) de votre solution chaque fois que vous enregistrez votre solution.  
  
### <a name="configuration-properties-folder-debugging-category"></a>Dossier Propriétés de configuration (catégorie Débogage)  
  
|**Paramètre**|**Description**|  
|-----------------|---------------------|  
|**Débogueur à lancer**|Spécifie le débogueur à exécuter, avec les choix suivants :<br /><br /> -   **Débogueur Windows local**<br />-   **Débogueur de Windows à distance**<br />-   **Débogueur de navigateur Web**<br />-   **Débogueur de Service Web**|  
|**Commande** (débogueur Windows Local)|Spécifie la commande de démarrage du programme que vous déboguez sur l'ordinateur local.|  
|**Commande à distance** (débogueur Windows distant)|Chemin d’accès pour le fichier .exe sur l’ordinateur distant. Entrez le chemin d’accès tel que vous l’entreriez sur l’ordinateur distant.|  
|**Arguments de la commande** (les débogueur Windows Local et débogueur de Windows à distance)|-Spécifie les arguments de la commande spécifiée précédemment.<br /><br /> Vous pouvez utiliser les opérateurs de redirection suivants dans cette zone :<br /><br /> < `file`<br /> Lit stdin à partir du fichier.<br /><br /> > `file`<br /> Écrit stdout dans le fichier.<br /><br /> >> `file`<br /> Ajoute stdout au fichier.<br /><br /> 2> `file`<br /> Écrit stderr dans le fichier.<br /><br /> 2>> `file`<br /> Ajoute stderr au fichier.<br /><br /> 2> &1<br /> Envoie la sortie de stderr (2) au même emplacement que stdout (1).<br /><br /> 1> &2<br /> Envoie la sortie de stdout (1) au même emplacement que stderr (2).<br /><br /> Dans la plupart des cas, ces opérateurs ne peuvent être utilisés que pour les applications console.|  
|**Répertoire de travail**|Spécifie le répertoire de travail du programme en cours de débogage, par rapport au répertoire de projet où se trouve votre fichier .EXE. Si vous laissez cette zone vide, le répertoire de travail est le répertoire du projet. Pour le débogage distant, le répertoire du projet est sur le serveur distant.|  
|**Attacher** (les débogueur Windows Local et débogueur de Windows à distance)|Spécifie s'il faut démarrer ou attacher l'application. Le paramètre par défaut est Non.|  
|**Nom de serveur distant** (débogueur Windows distant)|Spécifie le nom d'un ordinateur (autre que le vôtre) sur lequel vous voulez déboguer une application.<br /><br /> La macro de génération RemoteMachine a est définie sur la valeur de cette propriété ; Pour plus d’informations, consultez [Macros pour les propriétés et les commandes de génération](http://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b).|  
|**Connexion** (débogueur Windows distant)|Vous permet de commuter entre les types de connexion standard et sans authentification pour le débogage distant. Spécifiez un nom d’ordinateur distant dans le **nom de serveur distant** boîte. Les types de connexions incluent les éléments suivants :<br /><br /> -   **À distance avec l’authentification Windows**<br />-   **À distance sans authentification (natif uniquement)**<br /><br /> **Remarque** débogage à distance sans authentification peut laisser l’ordinateur distant vulnérable aux violations de sécurité. Le mode Authentification Windows est plus sécurisé.<br /><br /> Pour plus d’informations, consultez [programme d’installation du débogage distant](../debugger/remote-debugging.md).|  
|**URL HTTP** (Web Service débogueur et le débogueur de navigateur Web)|Spécifie l'URL où le projet que vous déboguez est localisé.|  
|**Type de débogueur**|Spécifie le type de débogueur à utiliser : **natif uniquement**, **managé uniquement**, **GPU uniquement**, **mixte**, **automatique**(valeur par défaut), ou **Script**.<br /><br /> -   **Natif uniquement** est du code C++ non managé.<br />-   **Managé uniquement** pour le code qui s’exécute sous le common language runtime (code managé).<br />-   **Mixte** appelle les débogueurs pour à la fois managé et code non managé.<br />-   **Auto** détermine le type de débogueur en fonction du compilateur et les informations de l’EXE.<br />-   **Script** appelle un débogueur pour les scripts.<br />-   **GPU uniquement** pour le code C++ AMP qui s’exécute sur un périphérique GPU ou sur le rastériseur de référence DirectX. Consultez [débogage du Code GPU](../debugger/debugging-gpu-code.md).|  
|**Environnement** (débogueur Windows Local)|Spécifie les variables d'environnement du programme que vous déboguez. Utilisez la syntaxe de variable d’environnement standard (par exemple, `PATH="%SystemRoot%\..."`). Ces variables se substituent l’environnement du système ou sont fusionnées avec l’environnement du système, selon le **fusion de l’environnement** paramètre. Lorsque vous cliquez dans la colonne de paramètres, « Modifier... » apparaît. Cliquez sur ce lien pour modifier des variables d'environnement.|  
|**Fusion de l’environnement** (débogueur Windows Local)|Détermine si les variables qui sont spécifiés dans le **environnement** boîte est fusionnée avec l’environnement défini par le système d’exploitation. Le paramètre par défaut est Oui.|  
|**Débogage SQL** (tous sauf le débogueur de Cluster MPI)|Active le débogage de procédures SQL à partir de votre application [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]. Le paramètre par défaut est Non.|  
|**Type d’accélérateur de débogage** (débogage GPU uniquement)|Spécifie le périphérique GPU à utiliser pour le débogage. L'installation des pilotes de périphériques GPU compatibles ajoutera des options supplémentaires. Le paramètre par défaut est « GPU - Émulateur de logiciel ».|  
|**Comportement du point d’arrêt par défaut GPU** (débogage GPU uniquement)|Spécifie si un événement de point d'arrêt doit être déclenché pour chaque thread dans une chaîne SIMD. Le paramètre par défaut consiste à déclencher l'événement de point d'arrêt une seule fois par distorsion.|  
|**Accélérateur par défaut de l’amp** (débogage GPU uniquement)|Spécifie l'accélérateur AMP par défaut lors du débogage du code GPU. Choisissez **accélérateur du logiciel WARP** pour déterminer si un problème est causé par le matériel ou un pilote au lieu de votre code.|  
|**Répertoire de déploiement** (débogueur Windows distant)|Spécifie le chemin d’accès sur l’ordinateur distant où la sortie de projet sera copiée avant le lancement. Le chemin d'accès peut être un partage réseau sur l'ordinateur distant, ou il peut s'agir d'un chemin d'accès à un dossier sur l'ordinateur distant. Le paramètre par défaut est vide, ce qui signifie que la sortie du projet n'est pas copiée dans un partage réseau. Pour activer le déploiement des fichiers, vous devez également sélectionner le **déployer** case à cocher dans la boîte de dialogue de Configuration Manager. Pour plus d’informations, consultez [Guide pratique pour créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md).|  
|**Fichiers supplémentaires à déployer** (débogueur Windows distant)|Si le répertoire de déploiement est défini, il s'agit d'une liste délimitée par des points-virgules pour les fichiers supplémentaires à copier vers le répertoire de déploiement. Le paramètre par défaut est vide, ce qui signifie qu'aucun fichier supplémentaire n'est copié dans le répertoire de déploiement. Pour activer le déploiement des fichiers, vous devez également sélectionner le **déployer** case à cocher dans la boîte de dialogue de Configuration Manager. Pour plus d’informations, consultez [Guide pratique pour créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md).|  
|**Déployer les bibliothèques Runtime de débogage Visual C++** (débogueur Windows distant)|Si la propriété du répertoire de déploiement est définie, elle spécifie si les bibliothèques d'exécution du débogage Visual C++ pour la plateforme actuelle doivent être copiées au partage réseau ou non. Le paramètre par défaut est Oui.|  
  
### <a name="cc-folder-general-category"></a>Dossier C/C++ (catégorie Général)  
  
|Paramètre|Description|  
|-------------|-----------------|  
|**Format des informations de débogage** ([/Z7, / Zd, Zi, /ZI](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8))|Spécifie le type d'informations de débogage à créer pour le projet.<br /><br /> L'option par défaut (/ZI) crée une base de données du programme (PDB) pour Modifier & Continuer. Pour plus d’informations, consultez [/Z7, / Zd, / Zi, /ZI (Format des informations de débogage)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8).|  
  
### <a name="cc-folder-optimization-category"></a>Dossier C/C++ (catégorie Optimisation)  
  
|Paramètre|Description|  
|-------------|-----------------|  
|**Optimization**|Spécifie si le compilateur doit optimiser le code qu'il produit. L'optimisation modifie le code exécuté. Le code optimisé ne correspond plus au code source. Par conséquent, le débogage est difficile.<br /><br /> L’option par défaut (**désactivé (/ 0d**) supprime l’optimisation. Vous pouvez développer avec l'optimisation supprimée, puis l'activez lors de la création de la version de production de votre code.|  
  
### <a name="linker-folder-debugging-category"></a>Dossier Éditeur de liens (catégorie Débogage)  
  
|Paramètre|Description|  
|-------------|-----------------|  
|**Générer des infos de débogage** ([/DEBUG](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103))|Indique à l'Éditeur de liens d'inclure les informations de débogage, qui auront le format spécifié par /Z7, /Zd, Zi ou /ZI.|  
|**Générer un fichier de base de données de programme** ([/PDB:name](http://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d))|Spécifiez le nom d'un fichier PDB dans cette zone. Vous devez sélectionner ZI ou /Zi pour Format des informations de débogage.|  
|**Suppression des symboles privés** ([/PDBSTRIPPED:filename](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55))|Spécifiez le nom d'un fichier PDB dans cette zone si vous ne voulez pas inclure de symboles privés dans le fichier PDB. Cette option crée un second fichier PDB (Program Database) lorsque vous générez votre image de programme avec toute option du compilateur ou de l'éditeur de liens générant un fichier PDB, comme /DEBUG, /Z7, /Zd. Ou /Zi. Ce second fichier PDB omet les symboles que vous ne souhaitez pas envoyer à vos clients. Pour plus d’informations, consultez l’article [/PDBSTRIPPED (Supprimer les symboles privés)](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).|  
|**Générer un fichier de mappage** ([/mapper](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63))|Indique à l'Éditeur de liens de générer un fichier de mappage durant l'édition des liens. Le paramètre par défaut est Non. Pour plus d’informations, consultez l’article [/MAP (Générer fichier de mappage)](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Nom de mappage** ([/Map :](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63)*nom*)|Si vous choisissez Génération d'un fichier de mappage, vous pouvez spécifier le fichier de mappage dans cette zone. Pour plus d’informations, consultez l’article [/MAP (Générer fichier de mappage)](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Mappage des exportations** ([/MAPINFO:EXPORTS](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Inclut les fonctions exportées dans le fichier de mappage. Le paramètre par défaut est Non. Pour plus d’informations, consultez [/MAPINFO (inclure des informations dans le fichier de mappage)](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b).|  
|**Assembly pouvant être débogué** ([/ASSEMBLYDEBUG](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Spécifie les paramètres de l'option /ASSEMBLYDEBUG de l'Éditeur de liens. Les valeurs possibles sont les suivantes :<br /><br /> -   **Pas d’attribut debuggable émis**.<br />-   **Runtime suivi et désactiver les optimisations (/ ASSEMBLYDEBUG)**. Il s'agit de l'option par défaut,<br />-   **Aucun optimizations(/ASSEMBLYDEBUG:DISABLE) runtime de suivi et activer**.<br />-   **\<hériter des paramètres par défaut parent ou du projet >**.<br />-Pour plus d’informations, consultez [/ASSEMBLYDEBUG (Ajouter DebuggableAttribute)](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982).|  
  
 Vous pouvez modifier par programme ces paramètres dans le dossier Propriétés de configuration (catégorie Debug) à l’aide de l’interface Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings. Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage du code natif](../debugger/debugging-native-code.md)   
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)   
 [Création et gestion de projets Visual C++](http://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047)   
 [/ASSEMBLYDEBUG (Ajouter DebuggableAttribute)](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982)   
 [Macros courantes pour les propriétés et les commandes de génération](http://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b)



