---
title: "Param&#232;tres de projet pour une configuration Debug&#160;C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCDebugSettings.WebBrowser.DebuggerType"
  - "VC.Project.IVCGPUDebugPageObject.EnvironmentMerge"
  - "VC.Project.VCDebugSettings.SymbolPath"
  - "VC.Project.IVCClusterDebugPageObject.ApplicationCommand"
  - "VC.Project.IVCRemoteDebugPageObject.WorkingDirectory"
  - "VC.Project.VCDebugSettings.DebuggerType"
  - "VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType"
  - "VC.Project.IVCRemoteDebugPageObject.SQLDebugging"
  - "VC.Project.IVCRemoteDebugPageObject.Remote"
  - "VC.Project.IVCGPUDebugPageObject.CommandArguments"
  - "VC.Project.VCDebugSettings.CommandArguments"
  - "VC.Project.IVCClusterDebugPageObject.MPIRunWorkingDirectory"
  - "VC.Project.IVCLocalDebugPageObject.SQLDebugging"
  - "VC.Project.IVCWebSvcDebugPageObject.HttpUrl"
  - "VC.Project.IVCLocalDebugPageObject.WorkingDirectory"
  - "VC.Project.IVCLocalDebugPageObject.CommandArguments"
  - "VC.Project.IVCClusterDebugPageObject.MPIRunCommand"
  - "VC.Project.IVCGPUDebugPageObject.WorkingDirectory"
  - "VC.Project.IVCWebSvcDebugPageObject.DebuggerType"
  - "VC.Project.IVCRemoteDebugPageObject.CommandArguments"
  - "VC.Project.IVCRemoteDebugPageObject.DebuggerType"
  - "VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads"
  - "VC.Project.IVCRemoteDebugPageObject.RemoteMachine"
  - "VC.Project.IVCClusterDebugPageObject.MPIRunArguments"
  - "VC.Project.IVCClusterDebugPageObject.MPIAcceptFilter"
  - "VC.Project.IVCGPUDebugPageObject.RemoteConnection"
  - "VC.Project.VCDebugSettings.PDBPath"
  - "VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory"
  - "VC.Project.VCDebugSettings.SQLDebugging"
  - "VC.Project.VCDebugSettings.RemoteCommand"
  - "VC.Project.IVCClusterDebugPageObject.ShimCommand"
  - "VC.Project.IVCLocalDebugPageObject.Command"
  - "VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads"
  - "VC.Project.IVCLocalDebugPageObject.Attach"
  - "VC.Project.VCDebugSettings.Command"
  - "VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType"
  - "VC.Project.IVCRemoteDebugPageObject.RemoteCommand"
  - "VC.Project.IVCClusterDebugPageObject.ApplicationArguments"
  - "VC.Project.IVCLocalDebugPageObject.Environment"
  - "VC.Project.IVCGPUDebugPageObject.DeploymentDirectory"
  - "VC.Project.IVCLocalDebugPageObject.EnvironmentMerge"
  - "VC.Project.VCDebugSettings.Environment"
  - "VC.Project.IVCGPUDebugPageObject.BreakpointBehavior"
  - "VC.Project.IVCLocalDebugPageObject.DebuggerType"
  - "VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl"
  - "VC.Project.IVCWebSvcDebugPageObject.SQLDebugging"
  - "VC.Project.IVCGPUDebugPageObject.AcceleratorType"
  - "VC.Project.IVCGPUDebugPageObject.Environment"
  - "VC.Project.VCDebugSettings.RemoteMachine"
  - "VC.Project.IVCGPUDebugPageObject.AdditionalFilesToDeploy"
  - "VC.Project.VCDebugSettings.WorkingDirectory"
  - "vs.debug.builds"
  - "VC.Project.VCDebugSettings.Attach"
  - "VC.Project.VCDebugSettings.HttpUrl"
  - "VC.Project.IVCClusterDebugPageObject.MPIAcceptMode"
  - "VC.Project.IVCGPUDebugPageObject.Attach"
  - "VC.Project.IVCRemoteDebugPageObject.AdditionalFiles"
  - "VC.Project.IVCGPUDebugPageObject.Command"
  - "VC.Project.VCDebugSettings.Remote"
  - "VC.Project.IVCRemoteDebugPageObject.Attach"
  - "VC.Project.VCDebugSettings.EnvironmentMerge"
  - "VC.Project.IVCGPUDebugPageObject.MachineName"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "fichiers .pdb, paramètres de projet des versions debug"
  - "/DEBUG (option de l'éditeur de liens)"
  - "/MAP (option de l'éditeur de liens)"
  - "/MAPINFO (option de l'éditeur de liens)"
  - "/PDB (option de l'éditeur de liens)"
  - "/PDBSTRIPPED (option de l'éditeur de liens)"
  - "/Z7 (option du compilateur C++)"
  - "/Zd (option du compilateur C++)"
  - "/ZI (option du compilateur C++)"
  - "versions debug, paramètres de projet"
  - "configurations de débogage, C++"
  - "DEBUG (option de l'éditeur de liens)"
  - "-DEBUG (option de l'éditeur de liens)"
  - "déboguer (C++), paramètres du débogueur"
  - "MAP (option de l'éditeur de liens)"
  - "-MAP (option de l'éditeur de liens)"
  - "fichiers de mappage, paramètres de projet"
  - "MAPINFO (option de l'éditeur de liens)"
  - "-MAPINFO (option de l'éditeur de liens)"
  - "fichiers pdb, paramètres de projet des versions debug"
  - "PDB (option de l'éditeur de liens)"
  - "-PDB (option de l'éditeur de liens)"
  - "PDBSTRIPPED (option de l'éditeur de liens)"
  - "-PDBSTRIPPED (option de l'éditeur de liens)"
  - "configurations de projet, déboguer"
  - "paramètres du projet (Visual Studio)"
  - "paramètres du projet (Visual Studio), configurations de débogage"
  - "projets (Visual Studio), configurations de débogage"
  - "Z7 (option du compilateur C++)"
  - "-Z7 (option du compilateur C++)"
  - "Zd (option du compilateur C++)"
  - "-Zd (option du compilateur C++)"
  - "ZI (option du compilateur C++)"
  - "-Zl (option du compilateur C++)"
ms.assetid: 860c7f13-a108-4fe5-8fca-d235cd3ca1cb
caps.latest.revision: 49
caps.handback.revision: 49
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Param&#232;tres de projet pour une configuration Debug&#160;C++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez modifier les paramètres de projet pour une configuration de débogage C ou Visual C\+\+ dans la boîte de dialogue **Pages de propriétés**, comme indiqué dans [Comment : définir des configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md).  Les tableaux suivants indiquent où se trouvent les paramètres du débogueur dans la boîte de dialogue **Pages de propriétés**.  
  
> [!WARNING]
>  Les paramètres du projet de débogage dans la catégorie **Propriétés de configuration\/Débogage** pour les applications Windows Store et les composants écrits en C\+\+ sont différents.  Voir [Démarrer une session de débogage \(VB, C\#, C\+\+ et XAML\)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) dans le Centre de développement Windows.  
  
 Spécifiez le débogueur à utiliser dans la zone de liste **Débogueur à lancer**.  Votre choix affecte la sélection des propriétés affichées.  
  
 Chaque paramètre de propriété de débogage est automatiquement écrit et enregistré dans le fichier individuel \(.vcxproj.user\) de votre solution chaque fois que vous enregistrez votre solution.  
  
### Dossier Propriétés de configuration \(catégorie Débogage\)  
  
|**Paramètre**|**Description**|  
|-------------------|---------------------|  
|**Débogueur à lancer**|Spécifie le débogueur à exécuter, avec les choix suivants :<br /><br /> -   **Débogueur Windows local**<br />-   **Débogueur Windows distant**<br />-   **Débogueur de navigateur Web**<br />-   **Débogueur de service Web**|  
|**Commande** \(Débogueur Windows local\)|Spécifie la commande de démarrage du programme que vous déboguez sur l'ordinateur local.|  
|**Commande distante** \(Débogueur Windows distant\)|Chemin d'accès pour le fichier .exe sur l'ordinateur distant.  Entrez le chemin d'accès tel que vous l'entreriez sur l'ordinateur distant.|  
|**Arguments de la commande** \(Débogueur Windows local et débogueur Windows distant\)|-   Spécifie les arguments de la commande spécifiée précédemment.<br /><br /> Vous pouvez utiliser les opérateurs de redirection suivants dans cette zone :<br /><br /> \< `file`<br /> Lit stdin à partir du fichier.<br /><br /> \> `file`<br /> Écrit stdout dans le fichier.<br /><br /> \>\> `file`<br /> Ajoute stdout au fichier.<br /><br /> 2\> `file`<br /> Écrit stderr dans le fichier.<br /><br /> 2\>\> `file`<br /> Ajoute stderr au fichier.<br /><br /> 2\> &1<br /> Envoie la sortie de stderr \(2\) au même emplacement que stdout \(1\).<br /><br /> 1\> &2<br /> Envoie la sortie de stdout \(1\) au même emplacement que stderr \(2\).<br /><br /> Dans la plupart des cas, ces opérateurs ne peuvent être utilisés que pour les applications console.|  
|**Répertoire de travail**|Spécifie le répertoire de travail du programme en cours de débogage, par rapport au répertoire de projet où se trouve votre fichier .EXE.  Si vous laissez cette zone vide, le répertoire de travail est le répertoire du projet.  Pour le débogage distant, le répertoire du projet est sur le serveur distant.|  
|**Attacher** \(Débogueur Windows local et débogueur Windows distant\)|Spécifie s'il faut démarrer ou attacher l'application.  Le paramètre par défaut est Non.|  
|**Nom de serveur distant** \(Débogueur Windows distant\)|Spécifie le nom d'un ordinateur \(autre que le vôtre\) sur lequel vous voulez déboguer une application.<br /><br /> La macro de génération RemoteMachine a la valeur de cette propriété ; pour plus d'informations, consultez [Macros pour les propriétés et les commandes de génération](/visual-cpp/ide/common-macros-for-build-commands-and-properties).|  
|**Connexion** \(débogueur distant Windows\)|Vous permet de commuter entre les types de connexion standard et sans authentification pour le débogage distant.  Spécifiez un nom d'ordinateur distant dans la zone **Nom de serveur distant**.  Les types de connexions incluent les éléments suivants :<br /><br /> -   **À distance avec authentification Windows**<br />-   **À distance sans authentification \(Natif uniquement\)**<br /><br /> **Remarque** Le débogage distant sans authentification peut rendre l'ordinateur distant vulnérable face aux atteintes à la sécurité.  Le mode Authentification Windows est plus sécurisé.<br /><br /> Pour plus d'informations, consultez [Programme d'installation du débogage distant](../debugger/remote-debugging.md).|  
|**URL HTTP** \(débogueur de service Web et débogueur de navigateur Web\)|Spécifie l'URL où le projet que vous déboguez est localisé.|  
|**Type de débogueur**|Spécifie le type de débogueur à utiliser : **Natif uniquement**, **Managé uniquement**, **GPU uniquement**, **Mixte**, **Auto** \(par défaut\) ou **Script**.<br /><br /> -   Le type **Natif uniquement** est destiné au code C\+\+ non managé.<br />-   Le type **Managé uniquement** est destiné au code s'exécutant sous le Common Language Runtime \(code managé\).<br />-   Le type **Mixte** appelle les débogueurs aussi bien pour le code managé que le code non managé.<br />-   Le type **Auto** permet de déterminer le type du débogueur en fonction des informations relatives au compilateur et au fichier .EXE.<br />-   **Script** appelle un débogueur pour les scripts.<br />-   **GPU uniquement** pour le code C\+\+ AMP qui s'exécute sur un périphérique GPU ou sur le rastériseur de référence DirectX.  Consultez [Débogage du code GPU](../debugger/debugging-gpu-code.md).|  
|**Environnement** \(Débogueur Windows local\)|Spécifie les variables d'environnement du programme que vous déboguez.  Utilisez la syntaxe de variable d'environnement standard \(par exemple, `PATH="%SystemRoot%\..."`\).  Ces variables se substituent à l'environnement système ou fusionnent avec lui, selon le paramètre **Fusion de l'environnement**.  Lorsque vous cliquez dans la colonne de paramètres, « Modifier... » apparaît.  Cliquez sur ce lien pour modifier des variables d'environnement.|  
|**Fusion de l'environnement** \(Débogueur Windows local\)|Détermine si les variables spécifiées dans la zone **Environnement** doivent fusionner avec l'environnement défini par le système d'exploitation.  Le paramètre par défaut est Oui.|  
|**Débogage SQL** \(tous sauf le débogueur de cluster MPI\)|Active le débogage de procédures SQL à partir de votre application [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)].  Le paramètre par défaut est Non.|  
|**Type d'accélérateur de débogage** \(débogage GPU uniquement\)|Spécifie le périphérique GPU à utiliser pour le débogage.  L'installation des pilotes de périphériques GPU compatibles ajoutera des options supplémentaires.  Le paramètre par défaut est « GPU \- Émulateur de logiciel ».|  
|**Comportement du point d'arrêt par défaut GPU** \(débogage GPU uniquement\)|Spécifie si un événement de point d'arrêt doit être déclenché pour chaque thread dans une chaîne SIMD.  Le paramètre par défaut consiste à déclencher l'événement de point d'arrêt une seule fois par distorsion.|  
|**Accélérateur par défaut de l'AMP** \(Débogage GPU uniquement\)|Spécifie l'accélérateur AMP par défaut lors du débogage du code GPU.  Choisissez **Accélérateur logiciel WARP** pour déterminer si un problème est causé par le matériel ou un pilote au lieu de votre code.|  
|**Répertoire de déploiement** \(Débogueur Windows distant\)|Spécifie le chemin d'accès sur l'ordinateur distant où la sortie de projet sera copiée avant le lancement.  Le chemin d'accès peut être un partage réseau sur l'ordinateur distant, ou il peut s'agir d'un chemin d'accès à un dossier sur l'ordinateur distant.  Le paramètre par défaut est vide, ce qui signifie que la sortie du projet n'est pas copiée dans un partage réseau.  Pour activer le déploiement des fichiers, vous devez également activer la case à cocher **Déployer** dans la boîte de dialogue Gestionnaire de configurations.  Pour plus d'informations, consultez [Comment : créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md).|  
|**Fichiers supplémentaires à déployer** \(débogueur distant Windows\)|Si le répertoire de déploiement est défini, il s'agit d'une liste délimitée par des points\-virgules pour les fichiers supplémentaires à copier vers le répertoire de déploiement.  Le paramètre par défaut est vide, ce qui signifie qu'aucun fichier supplémentaire n'est copié dans le répertoire de déploiement.  Pour activer le déploiement des fichiers, vous devez également activer la case à cocher **Déployer** dans la boîte de dialogue Gestionnaire de configurations.  Pour plus d'informations, consultez [Comment : créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md).|  
|**Déployer les bibliothèques runtime de débogage Visual C\+\+** \(Débogueur Windows distant\)|Si la propriété du répertoire de déploiement est définie, elle spécifie si les bibliothèques d'exécution du débogage Visual C\+\+ pour la plateforme actuelle doivent être copiées au partage réseau ou non.  Le paramètre par défaut est Oui.|  
  
### Dossier C\/C\+\+ \(catégorie Général\)  
  
|Paramètre|Description|  
|---------------|-----------------|  
|**Format des informations de débogage** \([\/Z7, \/Zd, Zi, \/ZI](/visual-cpp/build/reference/z7-zi-zi-debug-information-format)\)|Spécifie le type d'informations de débogage à créer pour le projet.<br /><br /> L'option par défaut \(\/ZI\) crée une base de données du programme \(PDB\) pour Modifier & Continuer.  Pour plus d'informations, consultez [\/Z7, \/Zd, \/Zi, \/ZI \(Format des informations de débogage\)](/visual-cpp/build/reference/z7-zi-zi-debug-information-format).|  
  
### Dossier C\/C\+\+ \(catégorie Optimisation\)  
  
|Paramètre|Description|  
|---------------|-----------------|  
|**Optimisation**|Spécifie si le compilateur doit optimiser le code qu'il produit.  L'optimisation modifie le code exécuté.  Le code optimisé ne correspond plus au code source.  Par conséquent, le débogage est difficile.<br /><br /> L'option par défaut \(**Désactivé \(\/0d**\) supprime l'optimisation.  Vous pouvez développer avec l'optimisation supprimée, puis l'activez lors de la création de la version de production de votre code.|  
  
### Dossier Éditeur de liens \(catégorie Débogage\)  
  
|Paramètre|Description|  
|---------------|-----------------|  
|**Générer des infos de débogage** \([\/DEBUG](/visual-cpp/build/reference/debug-generate-debug-info)\)|Indique à l'Éditeur de liens d'inclure les informations de débogage, qui auront le format spécifié par \/Z7, \/Zd, Zi ou \/ZI.|  
|**Génération d'un fichier de base de données du programme** \([\/PDB:name](/visual-cpp/build/reference/pdb-use-program-database)\)|Spécifiez le nom d'un fichier PDB dans cette zone.  Vous devez sélectionner ZI ou \/Zi pour Format des informations de débogage.|  
|**Suppression des symboles privés** \([\/PDBSTRIPPED:nomfichier](/visual-cpp/build/reference/pdbstripped-strip-private-symbols)\)|Spécifiez le nom d'un fichier PDB dans cette zone si vous ne voulez pas inclure de symboles privés dans le fichier PDB.  Cette option crée un second fichier PDB \(Program Database\) lorsque vous générez votre image de programme avec toute option du compilateur ou de l'éditeur de liens générant un fichier PDB, comme \/DEBUG, \/Z7, \/Zd.  Ou \/Zi.  Ce second fichier PDB omet les symboles que vous ne souhaitez pas envoyer à vos clients.  Pour plus d'informations, consultez [\/PDBSTRIPPED \(Supprimer les symboles privés\)](/visual-cpp/build/reference/pdbstripped-strip-private-symbols).|  
|**Génération d'un fichier de mappage** \([\/MAP](/visual-cpp/build/reference/map-generate-mapfile)\)|Indique à l'Éditeur de liens de générer un fichier de mappage durant l'édition des liens.  Le paramètre par défaut est Non.  Pour plus d'informations, consultez [\/MAP \(Générer fichier de mappage\)](/visual-cpp/build/reference/map-generate-mapfile).|  
|**Nom de mappage** \([\/MAP :](/visual-cpp/build/reference/map-generate-mapfile)*nom*\)|Si vous choisissez Génération d'un fichier de mappage, vous pouvez spécifier le fichier de mappage dans cette zone.  Pour plus d'informations, consultez [\/MAP \(Générer fichier de mappage\)](/visual-cpp/build/reference/map-generate-mapfile).|  
|**Mappage des exportations** \([\/MAPINFO:EXPORTS](/visual-cpp/build/reference/mapinfo-include-information-in-mapfile)\)|Inclut les fonctions exportées dans le fichier de mappage.  Le paramètre par défaut est Non.  Pour plus d'informations, consultez [\/MAPINFO \(Inclure des informations dans le fichier de mappage\)](/visual-cpp/build/reference/mapinfo-include-information-in-mapfile).|  
|**Assembly pouvant être débogué** \([\/ASSEMBLYDEBUG](/visual-cpp/build/reference/mapinfo-include-information-in-mapfile)\)|Spécifie les paramètres de l'option \/ASSEMBLYDEBUG de l'Éditeur de liens.  Les valeurs possibles sont les suivantes :<br /><br /> -   **Pas d'attribut Debuggable émis**.<br />-   **Suivi du runtime et désactiver les optimisations \(\/ASSEMBLYDEBUG\)**.  Il s'agit de l'option par défaut,<br />-   **Pas de suivi du runtime et activer les optimisations \(\/ASSEMBLYDEBUG : DISABLE\)**.<br />-   **\<hériter des paramètres par défaut du parent ou du projet\>**.<br />-   Pour plus d'informations, consultez [\/ASSEMBLYDEBUG \(Ajouter DebuggableAttribute\)](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute).|  
  
 Vous pouvez modifier par programme ces paramètres dans le dossier Propriétés de configuration \(catégorie Debug\) à l'aide de l'interface Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings.  Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.  
  
## Voir aussi  
 [Débogage du code natif](../debugger/debugging-native-code.md)   
 [Paramètres et préparation du débogage](../debugger/debugger-settings-and-preparation.md)   
 [Création et gestion de projets Visual C\+\+](/visual-cpp/ide/creating-and-managing-visual-cpp-projects)   
 [\/ASSEMBLYDEBUG \(Ajouter DebuggableAttribute\)](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute)   
 [Macros pour les propriétés et les commandes de génération](/visual-cpp/ide/common-macros-for-build-commands-and-properties)