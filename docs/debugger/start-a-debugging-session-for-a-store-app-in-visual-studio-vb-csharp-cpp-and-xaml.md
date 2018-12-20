---
title: Démarrer une session de débogage pour une application UWP | Microsoft Docs
ms.custom: seodec18
ms.date: 11/20/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VC.Project.IVCAppHostRemoteDebugPageObject.MachineName
- VC.Project.IVCAppHostRemoteDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostTetheredDebugPageObject.DebuggerType
- VC.Project.IVCAppHostLocalDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostRemoteDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.DebuggerType
- ImmersiveProjects.Properties.Debug
- VC.Project.IVCAppHostTetheredDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostLocalDebugPageObject.AllowLocalNetworkLoopback
- AppPackage.Properties.Debug
- VC.Project.IVCAppHostRemoteDebugPageObject.Authentication
- VC.Project.IVCAppHostRemoteDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.BreakpointBehavior
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 181dec6bfa6ebe96528c39b74d68375b8eb7fcb8
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062407"
---
# <a name="start-a-debugging-session-for-a-uwp-app"></a>Commencer une session de débogage pour une application UWP
  
Cet article décrit comment démarrer une session de débogage de Visual Studio pour une application Universal Windows Platform (UWP). Les applications UWP peuvent être écrites en XAML et C++, XAML et C#/ Visual Basic, ou HTML et JavaScript. Pour démarrer le débogage d’une application UWP, configurer la session de débogage et choisissez la méthode pour démarrer l’application.  
  
##  <a name="BKMK_The_easy_way_to_start_debugging"></a>Démarrer le débogage à partir de la barre d’outils de Visual Studio 
  
Pour configurer et démarrer le débogage, le plus simple consiste à partir de la barre d’outils standard de Visual Studio. 

![Déboguer à partir de la barre d’outils](../debugger/media/vsrun_select_target_device.png)  
  
1. À partir de la **Configuration** liste déroulante sur le **Standard** barre d’outils, sélectionnez **déboguer**.  
  
1. À partir de la **plateforme** liste déroulante, sélectionnez la plateforme cible à générer. 
   
1. Dans la liste déroulante en regard de la flèche verte, sélectionnez la cible de débogage. Vous pouvez choisir un ordinateur local, périphérique connecté en direct, local simulateur de Visual Studio, périphérique distant ou un émulateur. 
   
1. Pour démarrer le débogage, sélectionnez le vert **Démarrer** flèche dans la barre d’outils, ou sélectionnez **déboguer** > **démarrer le débogage**, ou appuyez sur **F5**. 
   
   Visual Studio génère et démarre l'application avec le débogueur attaché. 

Le débogage se poursuit jusqu'à ce qu’un point d’arrêt est atteint, que vous suspendiez manuellement l’exécution, une exception non gérée se produit, ou que l’application se termine.  
  
###  <a name="BKMK_Choose_the_deployment_target"></a> Options de cible de déploiement 
  
Vous pouvez définir la cible de débogage dans la barre d’outils de Visual Studio ou le projet de débogage de page de propriétés. Sélectionnez l'une des options suivantes :

|||  
|-|-|  
|**Ordinateur local**|Déboguez l'application dans la session active sur votre ordinateur local.|  
|**Simulateur**|Déboguez l’application dans le simulateur Visual Studio pour les applications UWP. Le simulateur est une fenêtre du bureau qui simule les fonctions de l’appareil, comme tactiles mouvements et rotation de l’appareil qui ne peut-être pas exister sur l’ordinateur local. L’option de simulateur est disponible uniquement si votre application **minimale de la plateforme cible. Version** est inférieur ou égal au système d’exploitation sur l’ordinateur local. Pour plus d’informations, consultez [exécuter des applications UWP dans le simulateur](../debugger/run-windows-store-apps-in-the-simulator.md).|  
|**Ordinateur distant**|Déboguez l’application sur un appareil connecté à l’ordinateur local sur un réseau ou d’un câble Ethernet. Les outils à distance pour Visual Studio doit être installé et en cours d’exécution sur le périphérique distant. Pour plus d’informations, consultez [exécuter des applications UWP sur un ordinateur distant](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
|**Appareil**|Déboguez l’application sur un périphérique USB connecté. L’appareil doit être déverrouillé de développeur et l’écran déverrouillé.|  
|**Émulateur mobile**|Démarrer l’émulateur spécifié dans le nom de l’émulateur, de déployer l’application et de démarrer le débogage. Émulateurs sont disponibles uniquement sur les machines Hyper-V est activé.|  

##  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Configurer le débogage dans la page de propriétés de projet 

Pour configurer les options de débogage supplémentaires, utilisez la page de propriétés de débogage du projet. 

**Pour ouvrir les propriétés de débogage :**

1. Dans **l’Explorateur de solutions**, sélectionnez le projet et sélectionnez le **propriétés** icône, ou cliquez sur le projet et sélectionnez **propriétés**.  
   
1. Sur le côté gauche de la **propriétés** volet :
   
   - Pour C# et les applications Visual Basic, sélectionnez **déboguer**.  
     
     ![C#et la page de propriétés de débogage de projet Visual Basic](../debugger/media/dbg_csvb_debugpropertypage.png)  
   
   - Pour les applications C++ et JavaScript, sélectionnez **propriétés de Configuration** > **débogage**.  
     
     ![Page de propriétés de débogage de l’application UWP C++](../debugger/media/dbg_cpp_debugpropertypage.png)  

###  <a name="BKMK_Choose_the_debugger_to_use"></a> Choisir le débogueur à utiliser  

Pour C# et les applications Visual Basic, Visual Studio débogue le code managé par défaut. Vous pouvez choisir de déboguer des types de code supplémentaires ou autres. Vous pouvez également définir **type de débogueur** valeurs pour les tâches en arrière-plan qui font partie du projet.

Dans les applications C++, Visual Studio débogue le code natif par défaut. Dans les applications JavaScript, Visual Studio débogue le script par défaut. Vous pouvez choisir de déboguer des types spécifiques de code à la place ou en plus de code natif. 

**Pour spécifier les types de code à déboguer :**

- Pour C# et les applications Visual Basic, sélectionnez une des débogueurs suivantes à partir de la **type d’Application** et **type de processus d’arrière-plan** menus déroulants sous **type de débogueur** sur le **déboguer** page de propriétés.  
  
- Pour C / c++ / applications JavaScript, sélectionnez une des débogueurs suivantes à partir de la **Type de débogueur** liste déroulante sur le **débogage** page de propriétés.

|||  
|-|-|  
|**Managé uniquement**|Déboguez le code managé dans votre application. Le code JavaScript et le code natif C/C++ sont ignorés.|  
|**Natif uniquement**|Déboguez le code natif C/C++ dans votre application. Le code managé et le code JavaScript sont ignorés.|  
|**Mixte (natif et managé)**|Déboguez le code natif et managé C/C++ dans votre application. Le code JavaScript est ignoré. Dans les projets C++, cette option est appelée **managé et natif**.|  
|**Script**|Déboguez le code JavaScript dans votre application. Le code managé et le code natif sont ignorés.|  
|**Code natif avec script**|Déboguer le code C/C++ natif et le code JavaScript dans votre application. Le code managé est ignoré. Disponible dans les projets C++ ou uniquement les tâches en arrière-plan.|  
|**GPU uniquement (C++ AMP)**|Déboguez le code C++ natif qui s'exécute sur une unité de traitement graphique (GPU). Disponible dans les projets C++ uniquement.|  

  
###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> Désactiver les bouclages de réseau (facultatifs) 
  
 Pour la sécurité, une application UWP qui est installée en mode standard ne peut pas effectuer des appels réseau vers l’appareil sur que n’est installé. Exempte de Studio Visual déployé des applications à partir de cette règle par défaut, afin de pouvoir tester les procédures de communication sur un seul ordinateur. Avant de publier votre application, vous devez tester votre application sans l’exemption.  
  
**Pour supprimer l’exemption du bouclage de réseau :**  
  
-   Pour C# et les applications Visual Basic, désélectionnez le **autoriser le bouclage de réseau local** case à cocher sous **options de démarrage** sur le **déboguer** page de propriétés.  
  
-   Pour les applications Visual C++ et JavaScript, sélectionnez **non** à partir de la **autoriser le bouclage de réseau Local** liste déroulante sur le **débogage** page de propriétés.  
  
###  <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> Réinstallez l’application lorsque vous démarrez le débogage (facultatif) 
 Pour diagnostiquer les problèmes d’installation avec un C# ou une application Visual Basic, sélectionnez **désinstaller et réinstaller mon package** sur le **déboguer** page de propriétés. Cette option recrée l’installation d’origine lorsque vous démarrez le débogage. Cette option n’est pas disponible pour les projets C++ et JavaScript.  
  
###  <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> Définir les options d’authentification pour le débogage distant  
  
Par défaut, vous devez fournir des informations d’identification Windows pour exécuter le débogueur distant lorsque vous sélectionnez **Machine distante** comme cible de déploiement. Vous pouvez modifier l’exigence d’authentification. 

Le **universel (protocole non chiffré)** mode d’authentification est pour les appareils IoT, Xbox et HoloLens et l’auteur de la mise à jour ou ultérieure PC Windows 10.  

**Pour modifier la méthode d’authentification :**  

- Pour C# et les applications Visual Basic, sur le **déboguer** page de propriétés, sélectionnez **Machine distante** en tant que le **appareil cible**. Ensuite, sélectionnez **aucun** ou **universel (protocole non chiffré)** pour **Mode d’authentification**. 
  
- Pour les applications C++ et JavaScript, sélectionnez **Machine distante** sous **débogueur à lancer** sur le **débogage** page de propriétés. Ensuite, sélectionnez **aucune authentification** ou **universel (protocole non chiffré)** pour **Type d’authentification**. 
  
> [!CAUTION]
> Il n’existe aucune sécurité du réseau lorsque vous exécutez le débogueur distant dans **aucun** ou **universel (protocole non chiffré)** modes. Choisissez ces modes uniquement sur des réseaux approuvés que vous êtes sûr ne sont pas exposés à un code malveillant ou de trafic hostile.  
  
##  <a name="BKMK_Start_the_debugging_session"></a> Options de démarrage de débogage  
  
Lorsque vous sélectionnez **déboguer** > **démarrer le débogage** ou appuyez sur **F5**, Visual Studio lance l’application avec le débogueur attaché. L'exécution se poursuit jusqu'à ce qu'un point d'arrêt soit atteint, que vous suspendiez manuellement l'exécution, qu'une exception non gérée se produise ou que l'application se termine.  
  
###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Démarrer le débogage mais le démarrage de l’application délai  

Par défaut, Visual Studio démarre l’application immédiatement lorsque vous démarrez le débogage. Vous pouvez également configurer l’application pour exécuter en mode débogage, mais la démarrer l’application en dehors du débogueur. Par exemple, vous souhaiterez peut-être déboguer le lancement de l’application à partir de la Windows **Démarrer** menu ou déboguer un processus en arrière-plan dans l’application. Si vous choisissez cette option, l’application démarre dans le débogueur au lancement. 

**Pour désactiver le démarrage de l’application automatique :**  
  
- Pour C# et les applications Visual Basic, sélectionnez **ne pas lancer, mais déboguer mon code au démarrage** sous **options de démarrage** sur le **déboguer** page de propriétés.  
   
- Pour les applications C++ et JavaScript, sélectionnez **non** à partir de la **lancer l’Application** liste déroulante sur le **débogage** page de propriétés.  
  
Pour plus d’informations sur le débogage des tâches en arrière-plan, consultez [déclencheur suspendre, reprendre, événements et d’arrière-plan pour les applications UWP](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
###  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Déboguer une application UWP installée ou en cours d’exécution 

Vous pouvez utiliser **déboguer le Package d’application installé** pour déboguer une application UWP qui est déjà installé ou en cours d’exécution sur un périphérique local ou distant. L’application a peut-être été installée à partir du Microsoft Store, ou il ne peut pas être un projet Visual Studio. Par exemple, l’application peut avoir un système de génération personnalisée qui n’utilise pas Visual Studio.  
  
Vous pouvez démarrer l’application installée immédiatement, ou vous pouvez définir qu’il s’exécute dans le débogueur au démarrage avec une autre méthode. Pour plus d’informations, consultez [déclencheur suspendre, reprendre, événements et d’arrière-plan pour les applications UWP)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
Pour démarrer une application UWP installée ou en cours d’exécution dans le débogueur, sélectionnez **déboguer** > **autres cibles de débogage** > **déboguer le Package d’application installé**. Pour plus d’instructions, consultez [déboguer un package d’application installé](../debugger/debug-installed-app-package.md).

###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Attacher le débogueur à une exécution de l’application Windows 8.x

Pour attacher le débogueur à une application [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] , vous devez utiliser Debuggable Package Manager pour configurer l'application à exécuter en mode débogage. Debuggable Package Manager est installé avec les outils à distance pour Visual Studio.  
  
1. Installer les outils à distance pour Visual Studio sur l’appareil où l’application est installée. Pour plus d’informations, consultez [l’installation des outils à distance](../debugger/remote-debugging.md).  
   
1. Dans le Windows **Démarrer** écran, recherchez et démarrer **Debuggable Package Manager**.  
   
   Une fenêtre PowerShell correctement configurée pour l'applet de commande AppxDebug s'affiche.  
   
1. Spécifiez l’identificateur PackageFullName de l’application. 
   
   1. Pour afficher une liste qui inclut le PackageFullName de toutes les applications, tapez `Get-AppxPackage` à l’invite de PowerShell.  
   
   1. À l’invite de PowerShell, entrez `Enable-AppxDebug <PackageFullName>`, où \<PackageFullName > est l’identificateur PackageFullName de l’application.  
   
1. Sélectionnez **Déboguer** > **Attacher au processus**.  
   
1. Dans le **attacher au processus** boîte de dialogue, spécifiez le périphérique distant dans le **cible de la connexion** boîte. 
   
   Vous pouvez entrer le nom du périphérique, sélectionnez-le dans la liste déroulante dans le **cible de la connexion** zone, ou sélectionnez **trouver** pour trouver le périphérique dans le **connexions à distance** boîte de dialogue.  
   
1. Pour spécifier le type de code que vous souhaitez déboguer, à côté du **attacher à** boîte, sélectionnez **sélectionnez**.  
   
1. Dans le **sélectionner le Type de Code** boîte de dialogue, sélectionnez soit :
   - **Déterminer automatiquement le type de code à déboguer**, ou 
   - **Déboguer ces types de codes**, puis sélectionnez un ou plusieurs types de code dans la liste.  
   
1. Dans le **processus disponibles** , sélectionnez le processus de l’application à déboguer.  
   
1. Sélectionnez **attacher**.  
  
 Visual Studio attache le débogueur au processus. L'exécution se poursuit jusqu'à ce qu'un point d'arrêt soit atteint, que vous suspendiez manuellement l'exécution, qu'une exception non gérée se produise ou que l'application se termine.

> [!NOTE]
> Les applications JavaScript s’exécutent dans une instance du processus *wwahost.exe*. Si plusieurs applications JavaScript s’exécute, vous devez connaître l’id numérique de processus (PID) de votre application *wwahost.exe* processus à attacher à celui-ci.  
> 
> Pour attacher à votre application JavaScript, le plus simple consiste à fermer toutes les autres applications JavaScript. Ou, vous pouvez noter le PID de l’exécution *wwahost.exe* processus dans le Gestionnaire des tâches Windows avant de démarrer votre application. Lorsque vous démarrez votre application, son *wwahost.exe* PID sera celle qui est différente de celles mentionnées précédemment.  

## <a name="see-also"></a>Voir aussi  
 [Déboguer des applications dans Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   