---
title: "D&#233;marrer une session de d&#233;bogage pour une application du Windows Store dans Visual Studio (VB, C#, C++ et XAML) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.IVCAppHostRemoteDebugPageObject.MachineName"
  - "VC.Project.IVCAppHostRemoteDebugPageObject.BreakpointBehavior"
  - "VC.Project.IVCAppHostLocalDebugPageObject.GPUDebuggerTargetType"
  - "VC.Project.IVCAppHostTetheredDebugPageObject.DebuggerType"
  - "VC.Project.IVCAppHostLocalDebugPageObject.BreakpointBehavior"
  - "VC.Project.IVCAppHostRemoteDebugPageObject.LaunchApplication"
  - "VC.Project.IVCAppHostRemoteDebugPageObject.GPUDebuggerTargetType"
  - "VC.Project.IVCAppHostLocalDebugPageObject.DebuggerType"
  - "VC.Project.IVCAppHostSimulatorDebugPageObject.DebuggerType"
  - "ImmersiveProjects.Properties.Debug"
  - "VC.Project.IVCAppHostTetheredDebugPageObject.LaunchApplication"
  - "VC.Project.IVCAppHostSimulatorDebugPageObject.LaunchApplication"
  - "VC.Project.IVCAppHostSimulatorDebugPageObject.GPUDebuggerTargetType"
  - "VC.Project.IVCAppHostLocalDebugPageObject.LaunchApplication"
  - "VC.Project.IVCAppHostLocalDebugPageObject.AllowLocalNetworkLoopback"
  - "AppPackage.Properties.Debug"
  - "VC.Project.IVCAppHostRemoteDebugPageObject.Authentication"
  - "VC.Project.IVCAppHostRemoteDebugPageObject.DebuggerType"
  - "VC.Project.IVCAppHostSimulatorDebugPageObject.BreakpointBehavior"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 66ec0e79-8261-4c19-a618-3fd1b3f71bbd
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# D&#233;marrer une session de d&#233;bogage pour une application du Windows Store dans Visual Studio (VB, C#, C++ et XAML)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![S'applique à Windows et Windows Phone](~/debugger/media/windows_and_phone_content.png "windows\_and\_phone\_content")  
  
 Cette rubrique décrit comment démarrer une session de débogage pour les applications Windows Store écrites en XAML et Visual C\+\+, Visual C\# ou Visual Basic. Le débogage d'une application implique la configuration de la session de débogage et le choix de la méthode de démarrage de l'application.  
  
> [!NOTE]
>  Pour les applications écrites en JavaScript et HTML, voir [Démarrer une session de débogage \(JavaScript\)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md).  
  
##  <a name="BKMK_In_this_topic"></a> Dans cette rubrique  
 [La méthode simple pour démarrer le débogage](#BKMK_The_easy_way_to_start_debugging)  
  
 [Configurer la session de débogage](#BKMK_Configure_the_debugging_session)  
  
-   [Ouvrir la page des propriétés de débogage du projet](#BKMK_Open_the_debugging_property_page_for_the_project)  
  
-   [Choisir les options de configuration de build](#BKMK_Choose_the_build_configuration_options)  
  
-   [Sélectionner la cible de déploiement](#BKMK_Choose_the_deployment_target)  
  
-   [Choisir le débogueur à utiliser](#BKMK_Choose_the_debugger_to_use)  
  
-   [Différer le démarrage de la session de débogage (facultatif)](#BKMK__Optional__Delay_starting_the_debug_session)  
  
-   [Désactiver les bouclages de réseau (facultatif)](#BKMK__Optional__Disable_network_loopbacks)  
  
-   [Réinstaller l'application au démarrage du débogage (facultatif)](#BKMK__Optional__Reinstall_the_app_when_you_start_debugging)  
  
-   [(Facultatif) Désactivez la condition d'authentification pour démarrer le débogueur distant](#BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger)  
  
 [Démarrer la session de débogage](#BKMK_Start_the_debugging_session)  
  
-   [Démarrer le débogage (F5)](#BKMK_Start_debugging__F5_)  
  
-   [Démarrer le débogage (F5), mais différer le démarrage de l'application](#BKMK_Start_debugging__F5__but_delay_the_app_start)  
  
-   [Démarrer une application installée dans le débogueur](#BKMK_Start_an_installed_app_in_the_debugger)  
  
-   [Attacher le débogueur à une application en cours de exécution](#BKMK_Attach_the_debugger_to_a_running_app_)  
  
    -   [Configurer l'application pour l'exécuter en mode débogage](#BKMK_Set_the_app_to_run_in_debug_mode)  
  
    -   [Attacher le débogueur](#BKMK_Attach_the_debugger)  
  
##  <a name="BKMK_The_easy_way_to_start_debugging"></a> La méthode simple pour démarrer le débogage  
  
1.  Ouvrez la solution d'application dans Visual Studio.  
  
2.  Appuyez sur la touche F5.  
  
 Visual Studio génère et démarre l'application avec le débogueur attaché. L'exécution se poursuit jusqu'à ce qu'un point d'arrêt soit atteint, que vous suspendiez manuellement l'exécution, qu'une exception non gérée se produise ou que l'application se termine. Pour plus d'informations, consultez [Parcourir une session de débogage \(XAML et C\#\)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md).  
  
##  <a name="BKMK_Configure_the_debugging_session"></a> Configurer la session de débogage  
  
###  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Ouvrir la page des propriétés de débogage du projet  
  
1.  Dans l'Explorateur de solutions, sélectionnez le projet. Dans le menu contextuel, choisissez **Propriétés**.  
  
2.  Cela permet d'ouvrir la page des propriétés de débogage du projet :  
  
    -   Pour les applications Visual C\# et Visual Basic, choisissez **Déboguer**.  
  
         ![Page de propriétés de débogage de projet C&#35; &#47; VB](~/debugger/media/dbg_csvb_debugpropertypage.png "DBG\_CsVb\_DebugPropertyPage")  
  
    -   Pour les applications Visual C\+\+, développez le nœud **Propriétés de configuration** , puis choisissez **Débogage**.  
  
         ![Page de propriétés de débogage de l’application Windows Store C&#43;&#43;](~/debugger/media/dbg_cpp_debugpropertypage.png "DBG\_CPP\_DebugPropertyPage")  
  
###  <a name="BKMK_Choose_the_build_configuration_options"></a> Choisir les options de configuration de build  
  
1.  Dans la liste **Configuration**, choisissez **Déboguer** ou **\(Debug\) active**.  
  
2.  Dans la liste **Plateforme**, sélectionnez la plateforme cible à générer. Dans la plupart des cas, **Any CPU** \(**Toutes les plateformes** dans Visual C\+\+\) est le meilleur choix.  
  
###  <a name="BKMK_Choose_the_deployment_target"></a> Sélectionner la cible de déploiement  
 ![S'applique uniquement à Windows](~/debugger/media/windows_only_content.png "windows\_only\_content")  
  
 Vous pouvez déployer et déboguer une application Windows Store sur l'ordinateur Visual Studio, dans le simulateur Visual Studio sur l'ordinateur local ou sur un appareil distant.  
  
-   Pour les applications C\# et Visual Basic, choisissez la cible dans la liste **Périphérique cible** sur la page des propriétés **Déboguer** du projet.  
  
-   Pour les applications C\+\+, sélectionnez la cible dans la liste **Débogueur à lancer** sur la page des propriétés **Débogage** :  
  
 Choisissez l'une des options suivantes :  
  
|||  
|-|-|  
|**Ordinateur local**|Déboguez l'application dans la session active sur votre ordinateur local. Consultez [Exécuter des applications du Windows Store sur un ordinateur local](../debugger/run-windows-store-apps-on-the-local-machine.md).|  
|**Simulateur**|Déboguez l'application dans le simulateur Visual Studio pour les applications [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]. Le simulateur est une fenêtre du Bureau qui permet de déboguer les fonctionnalités du périphérique, comme les mouvements tactiles et la rotation du périphérique, qui ne sont pas disponibles sur l'ordinateur local. Consultez [Exécuter des applications du Windows Store dans le simulateur](../debugger/run-windows-store-apps-in-the-simulator.md).|  
|**Ordinateur distant**|Déboguez l'application sur un périphérique qui est connecté à l'ordinateur local sur un intranet ou directement connecté via un câble Ethernet. Pour déboguer à distance, les outils de contrôle à distance Visual Studio doivent être installés et exécutés sur le périphérique distant. Consultez [Exécuter des applications du Windows Store sur un ordinateur distant](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
  
 Si vous choisissez **Ordinateur distant**, spécifiez le nom ou l'adresse IP de l'ordinateur distant de l'une des manières suivantes :  
  
-   Entrez le nom ou l'adresse IP de l'ordinateur distant.  
  
    -   Pour les applications C\# et Visual Basic, entrez le nom ou l'adresse IP dans la zone **Ordinateur distant**.  
  
    -   Pour les applications C\+\+, entrez le nom ou l'adresse IP dans la zone **Nom de l'ordinateur**.  
  
-   Choisissez l'ordinateur distant dans la boîte de dialogue **Sélectionner une connexion du débogueur distant**.  
  
     Pour ouvrir la boîte de dialogue :  
  
    -   Pour les applications C\# et Visual Basic, choisissez **Rechercher**.  
  
    -   Pour les applications C\+\+, choisissez la flèche bas dans la zone **Nom de l'ordinateur** et choisissez **\<Rechercher...\>**.  
  
     ![Boîte de dialogue Sélectionner la connexion au Remote Debugger](~/debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN\_SelectRemoteDebuggerDlg")  
  
    > [!NOTE]
    >  La boîte de dialogue **Sélectionner une connexion du débogueur distant** affiche les ordinateurs situés sur le sous\-réseau et les ordinateurs locaux qui sont directement connectés à l'ordinateur Visual Studio via un câble Ethernet. Pour spécifier un autre ordinateur, entrez le nom dans la zone **Nom de l'ordinateur**.  
  
 ![S'applique uniquement à Windows Phone](~/debugger/media/phone_only_content.png "phone\_only\_content")  
  
 Vous pouvez déployer et déboguer une application Windows Phone Store sur un appareil ou sur l'un des émulateurs Windows Phone de Visual Studio. Sélectionnez l'appareil ou l'émulateur dans la liste **Appareil cible**.  
  
###  <a name="BKMK_Choose_the_debugger_to_use"></a> Choisir le débogueur à utiliser  
 Par défaut, Visual Studio débogue le code managé dans des applications C\# et Visual Basic.  
  
 Pour les applications C\# et Visual Basic, vous pouvez choisir de déboguer le code managé et natif C\/C\+\+ dans votre application. Activez la case à cocher **Activer le débogage de code non managé** pour inclure le code natif dans votre session de débogage.  
  
 Par défaut, Visual Studio débogue le code natif dans votre application C\+\+.  
  
 Pour les applications C\+\+, vous pouvez choisir de déboguer des types de code spécifiques qui se trouvent dans les composants de votre application, à la place ou en plus du code natif. Spécifiez le code à déboguer dans la liste **Type de débogueur** de la page des propriétés de **débogage** du projet d'application.  
  
 Choisissez l'un de ces débogueurs dans la liste **Processus d'application** :  
  
|||  
|-|-|  
|**Script uniquement**|Déboguez le code JavaScript dans votre application. Le code managé et le code natif sont ignorés.|  
|**Natif uniquement**|Déboguez le code natif C\/C\+\+ dans votre application. Le code managé et le code JavaScript sont ignorés.|  
|**Managé uniquement**|Déboguez le code managé dans votre application. Le code JavaScript et le code natif C\/C\+\+ sont ignorés.|  
|**Mixte \(natif et managé\)**|Déboguez le code natif et managé C\/C\+\+ dans votre application. Le code JavaScript est ignoré.|  
|**GPU uniquement**|Déboguez le code C\+\+ natif qui s'exécute sur une unité de traitement graphique \(GPU\).|  
  
 ![S'applique uniquement à Windows Phone](~/debugger/media/phone_only_content.png "phone\_only\_content")  
  
 Pour les applications Windows Phone Store, vous pouvez aussi choisir d'utiliser le débogueur pour les processus en arrière\-plan à partir de **Processus de tâche en arrière\-plan**.  
  
###  <a name="BKMK__Optional__Delay_starting_the_debug_session"></a> Différer le démarrage de la session de débogage \(facultatif\)  
 Par défaut, Visual Studio démarre immédiatement l'application lorsque vous démarrez le débogage. Vous pouvez également démarrer une session de débogage et retarder le démarrage de votre application. Lorsque vous choisissez cette option, l'application est lancée dans le débogueur lorsqu'elle est lancée depuis l'écran Démarrer ou par un contrat d'activation, ou lorsqu'elle est démarrée par un autre processus ou méthode. Vous pouvez également différer le démarrage de votre application lorsque vous souhaitez déboguer une tâche en arrière\-plan alors que l'application proprement dite n'est pas en cours d'exécution.  
  
 Pour différer le lancement de votre application, vous pouvez :  
  
-   Pour les applications Visual C\# et Visual Basic, sélectionnez **Ne pas lancer, mais déboguer mon code au démarrage** dans la page des propriétés **Déboguer**.  
  
-   Pour les applications Visual C\+\+, choisissez **Oui** dans la liste **Lancer l'application** sur la page des propriétés **Débogage**.  
  
###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> Désactiver les bouclages de réseau \(facultatif\)  
 ![S'applique uniquement à Windows](~/debugger/media/windows_only_content.png "windows\_only\_content")  
  
 Pour des raisons de sécurité, une application Windows Store installée en mode standard n'est pas autorisée à effectuer des appels réseau vers le périphérique sur lequel elle est installée. Par défaut, le déploiement Visual Studio crée une exemption à cette règle pour l'application déployée. Cette exemption vous permet de tester les procédures de communication sur un seul ordinateur. Avant d'envoyer votre application au Windows Store, vous devez la tester sans l'exemption.  
  
 Pour supprimer l'exemption du bouclage de réseau :  
  
-   Pour les applications Visual C\# et Visual Basic, désactivez la case à cocher **Autoriser le bouclage de réseau local** sur la page des propriétés **Déboguer**.  
  
-   Pour les applications Visual C\+\+, choisissez **Non** dans la liste **Autoriser le bouclage de réseau local** sur la page des propriétés **Débogage**.  
  
###  <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> Réinstaller l'application au démarrage du débogage \(facultatif\)  
 Pour diagnostiquer les problèmes liés à l'installation et à la configuration initiale de votre application Visual C\# ou Visual Basic, choisissez **Désinstaller et réinstaller mon package** sur la page des propriétés **Déboguer** pour recréer une installation d'origine lorsque vous démarrez le débogage. Cette option n'est pas disponible pour les projets Visual C\+\+.  
  
###  <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> \(Facultatif\) Désactivez la condition d'authentification pour démarrer le débogueur distant  
 ![S'applique uniquement à Windows](~/debugger/media/windows_only_content.png "windows\_only\_content")  
  
 Par défaut, vous devez fournir des informations d'identification pour exécuter le débogueur distant.  
  
> [!IMPORTANT]
>  Vous pouvez choisir d'exécuter le débogueur distant en mode Aucune authentification, mais ce mode est fortement déconseillé. Il n'existe aucune sécurité du réseau lorsque vous lancez l'exécution dans ce mode. Sélectionnez le mode Aucune authentification uniquement si vous êtes sûr que le réseau n'est pas exposé à un problème de sécurité lié à des programmes malveillants ou dangereux.  
  
 Pour annuler la condition d'authentification :  
  
1.  Pour les applications Visual C\# et Visual Basic, désactivez la case à cocher **Utiliser l'authentification** sur la page de propriétés **Déboguer**.  
  
2.  Pour les applications Visual C\+\+, choisissez **Non** dans la liste **Exiger une authentification** sur la page de propriétés **Débogage**.  
  
 [Dans cette rubrique](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Start_the_debugging_session"></a> Démarrer la session de débogage  
  
###  <a name="BKMK_Start_debugging__F5_"></a> Démarrer le débogage \(F5\)  
 Quand vous choisissez **Démarrer le débogage** \(clavier : F5\) dans le menu **Déboguer**, Visual Studio lance l’application avec le débogueur attaché. L'exécution se poursuit jusqu'à ce qu'un point d'arrêt soit atteint, que vous suspendiez manuellement l'exécution, qu'une exception se produise ou que l'application se termine.  
  
###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Démarrer le débogage \(F5\), mais différer le démarrage de l'application  
 Vous pouvez configurer l'application pour s'exécuter en mode débogage, mais la démarrer par une autre méthode que le débogueur. Vous pouvez par exemple déboguer le lancement de votre application depuis le menu Démarrer ou déboguer un processus en arrière\-plan dans l'application sans la démarrer. Procédez comme suit pour retarder le démarrage de l'application :  
  
-   Dans la page des propriétés **Débogage** de l'application \(**Déboguer** dans Visual C\+\+\)  
  
    -   Pour les applications Visual C\# et Visual Basic, choisissez **Ne pas lancer, mais déboguer mon code au démarrage**.  
  
    -   Pour les applications Visual C\+\+, choisissez **Oui** dans la liste **Lancer l'application**.  
  
-   Choisissez **Démarrer le débogage** dans le menu **Déboguer** \(clavier : F5\).  
  
-   Démarrez votre application dans le menu Démarrer, avec un contrat de exécution ou en suivant une autre procédure.  
  
 L'application démarre en mode débogage. L'exécution se poursuit jusqu'à ce qu'un point d'arrêt soit atteint, que vous suspendiez manuellement l'exécution, qu'une exception non gérée se produise ou que l'application se termine.  
  
 . Pour plus d'informations sur le débogage de tâches en arrière\-plan, consultez [Déclencher des événements de suspension, de reprise et d'arrière\-plan pour Windows Store](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
###  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Démarrer une application installée dans le débogueur  
 Lorsque vous lancez le débogage en appuyant sur la touche F5, Visual Studio génère et déploie l'application, la configure pour s'exécuter en mode débogage, puis la démarre. Pour démarrer une application déjà installée sur un périphérique, utilisez la boîte de dialogue Déboguer le package d'application déjà installé. Cette procédure est utile lorsque vous devez déboguer une application installée depuis Windows Store, ou lorsque vous disposez des fichiers source de l'application, mais pas de projet Visual Studio pour cette dernière. Par exemple, vous pouvez avoir un système de génération personnalisée qui n'utilise pas les projets ou les solutions Visual Studio.  
  
 Vous pouvez installer l'application sur le périphérique local ou sur un périphérique distant.  Vous pouvez démarrer l'application immédiatement, ou bien la configurer pour s'exécuter dans le débogueur au démarrage de ce dernier par un autre processus ou une autre méthode, depuis le menu Démarrer ou par un contrat d'activation, par exemple. Vous pouvez également configurer l'application pour s'exécuter en mode débogage lorsque vous souhaitez déboguer un processus en arrière\-plan sans démarrer l'application. Pour plus d'informations, consultez [Déclencher des événements de suspension, de reprise et d'arrière\-plan pour Windows Store](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
 Procédez comme suit pour configurer une application installée pour s'exécuter en mode débogage :  
  
> [!NOTE]
>  L'application ne doit pas être en cours d'exécution lorsque vous lancez cette procédure.  
  
1.  Dans le menu **Débogage**, choisissez **Déboguer le package d'application installé**  
  
2.  Choisissez l'une des options suivantes dans la liste :  
  
    |||  
    |-|-|  
    |**Ordinateur local**|Déboguez l'application dans la session active sur votre ordinateur local. Consultez [Exécuter des applications du Windows Store sur un ordinateur local](../debugger/run-windows-store-apps-on-the-local-machine.md).|  
    |**Simulateur**|Déboguez l'application dans le simulateur Visual Studio pour les applications [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]. Le simulateur est une fenêtre du Bureau qui permet de déboguer les fonctionnalités du périphérique, comme les mouvements tactiles et la rotation du périphérique, qui ne sont pas disponibles sur l'ordinateur local. Consultez [Exécuter des applications du Windows Store dans le simulateur](../debugger/run-windows-store-apps-in-the-simulator.md).|  
    |**Ordinateur distant**|Déboguez l'application sur un périphérique qui est connecté à l'ordinateur local sur un intranet ou directement connecté via un câble Ethernet. Pour déboguer à distance, les outils de contrôle à distance Visual Studio doivent être installés et en cours d'exécution sur le périphérique distant. Consultez [Exécuter des applications du Windows Store sur un ordinateur distant](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
  
3.  Choisissez l'application dans la liste **Packages d'application installés**.  
  
4.  Choisissez le moteur de débogage à utiliser dans la liste **Déboguer ce type de code**.  
  
5.  \(Facultatif\). Choisissez **Ne pas lancer, mais déboguer mon code au démarrage** pour déboguer l'application lorsqu'elle est lancée à l'aide d'une autre méthode ou pour déboguer un processus en arrière\-plan.  
  
 Lorsque vous cliquez sur **Démarrer**, l'application démarre ou est configurée pour s'exécuter en mode débogage.  
  
###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Attacher le débogueur à une application en cours de exécution  
 Pour attacher le débogueur à une application [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)], vous devez utiliser Debuggable Package Manager pour configurer l'application à exécuter en mode débogage. Debuggable Package Manager est installé avec les outils de contrôle à distance Visual Studio.  
  
 Attacher le débogueur à une application est utile lorsque vous devez déboguer une application déjà installée, telle qu'une application qui a été installée à partir de [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]. L'attachement est requis lorsque vous possédez les fichiers sources de l'application, mais que vous n'avez pas de projet Visual Studio pour l'application. Par exemple, vous pouvez avoir un système de génération personnalisée qui n'utilise pas les projets ou les solutions Visual Studio.  
  
 Attacher le débogueur à une application nécessite les étapes suivantes :  
  
1.  Configurez l'application pour l'exécuter en mode débogage. Cela doit s'effectuer lorsque l'application n'est pas en cours d'exécution.  
  
2.  Démarrez l'application. Vous pouvez démarrer l'application à partir de l'écran Démarre, avec un contrat d'exécution ou tout autre méthode.  
  
3.  Attacher le débogueur à l'application en cours d'exécution.  
  
####  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> Configurer l'application pour l'exécuter en mode débogage  
  
1.  Installez les outils de contrôle à distance Visual Studio sur le périphérique où l'application est installée. Consultez la page [Installation des outils de contrôle à distance](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).  
  
2.  Sur l'écran Démarrer, recherchez `Debuggable Package Manager`, puis démarrez\-le.  
  
     Une fenêtre PowerShell correctement configurée pour l'applet de commande AppxDebug s'affiche.  
  
3.  Pour activer le débogage d'une application, vous devez spécifier l'identificateur PackageFullName de l'application. Pour afficher une liste de toutes les applications qui incluent PackageFullName, entrez `Get-AppxPackage` à l'invite de PowerShell.  
  
4.  À l'invite de PowerShell, entrez `Enable-AppxDebug` *PackageFullName*, où *PackageFullName* est l'identificateur PackageFullName de l'application.  
  
####  <a name="BKMK_Attach_the_debugger"></a> Attacher le débogueur  
 Pour attacher le débogueur :  
  
1.  Dans le menu **Débogage**, sélectionnez **Attacher au processus**.  
  
     La boîte de dialogue **Attacher au processus** s'affiche.  
  
2.  Pour attacher une application sur un périphérique distant, spécifiez le périphérique distant dans la zone **Qualificateur**. Vous pouvez :  
  
    -   Entrez le nom dans la zone **Qualificateur**.  
  
    -   Cliquez sur la flèche Bas dans la zone **Qualificateur**, puis choisissez le périphérique dans une liste que vous avez associée précédemment.  
  
    -   Choisissez **Rechercher** pour sélectionner le périphérique dans une liste de périphériques sur votre sous\-réseau local.  
  
3.  Spécifiez le type de code à déboguer dans la zone **Attacher à**.  
  
     Choisissez **Sélectionner**, puis effectuez l'une des opérations suivantes :  
  
    -   Choisissez **Déterminer automatiquement le type de code à déboguer**  
  
    -   Choisissez **Déboguer ces types de codes**, puis sélectionnez un ou plusieurs types dans la liste.  
  
4.  Dans la liste **Processus disponibles** , sélectionnez le processus de l'application.  
  
5.  Choisissez **Attacher**.  
  
 Visual Studio attache le débogueur au processus. L'exécution se poursuit jusqu'à ce qu'un point d'arrêt soit atteint, que vous suspendiez manuellement l'exécution, qu'une exception non gérée se produise ou que l'application se termine.  
  
 [Dans cette rubrique](#BKMK_In_this_topic)  
  
## Voir aussi  
 [Déboguer des applications dans Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   
 [Parcourir une session de débogage \(XAML et C\#\)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)