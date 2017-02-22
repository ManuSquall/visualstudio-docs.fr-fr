---
title: "D&#233;marrer une session de d&#233;bogage dans Visual&#160;Studio (JavaScript) pour des applications du Windows&#160;Store | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.installedapppackagelauncher"
  - "vs.debug.error.wwahost_scriptdebuggingdisabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: fb91203f-2cf4-44d3-8ed9-93bc5aaa50b8
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# D&#233;marrer une session de d&#233;bogage dans Visual&#160;Studio (JavaScript) pour des applications du Windows&#160;Store
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![S'applique à Windows et Windows Phone](../debugger/media/windows_and_phone_content.png "windows\_and\_phone\_content")  
  
 Cette rubrique explique comment démarrer une session de débogage pour les applications du Windows Store écrites en JavaScript et HTML5. Vous pouvez démarrer le débogage avec une seule séquence de touches ou configurer la session de débogage pour des scénarios spécifiques, puis choisir de quelle façon démarrer l'application.  
  
> [!NOTE]
>  Pour les applications écrites en XAML et Visual C\#, Visual C\+\+ ou Visual Basic, consultez [Démarrer une session de débogage \(VB, C\#, C\+\+ et XAML\)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_In_this_topic"></a> Dans cette rubrique  
 [Dans cette rubrique](#BKMK_In_this_topic)  
  
 [La méthode simple pour démarrer le débogage](#BKMK_The_easy_way_to_start_debugging)  
  
 [Configurer la session de débogage](#BKMK_Configure_the_debugging_session)  
  
-   [Ouvrir la page des propriétés de débogage du projet](#BKMK_Open_the_debugging_property_page_for_the_project)  
  
-   [Choisir les options de configuration de build](#BKMK_Choose_the_build_configuration_options)  
  
-   [Sélectionner la cible de déploiement](#BKMK_Choose_the_deployment_target)  
  
-   [Choisir le débogueur à utiliser](#BKMK_Choose_the_debugger_to_use)  
  
-   [(Facultatif) Retarder le démarrage de l'application dans la session de débogage](#BKMK__Optional__Delay_starting_app_in_the_debug_session)  
  
-   [Désactiver les bouclages de réseau (facultatif)](#BKMK__Optional__Disable_network_loopbacks)  
  
 [Démarrer la session de débogage](#BKMK_Start_the_debugging_session)  
  
-   [Démarrer le débogage (F5)](#BKMK_Start_debugging__F5_)  
  
-   [Démarrer le débogage (F5), mais différer le démarrage de l'application](#BKMK_Start_debugging__F5__but_delay_the_app_start)  
  
 [Démarrer une application installée dans le débogueur](#BKMK_Start_an_installed_app_in_the_debugger)  
  
 [Attacher le débogueur à une application en cours d'exécution](#BKMK_Attach_the_debugger_to_a_running_app_)  
  
-   [Configurer l'application pour l'exécuter en mode débogage](#BKMK_Set_the_app_to_run_in_debug_mode)  
  
-   [Attacher le débogueur](#BKMK_Attach_the_debugger)  
  
##  <a name="BKMK_The_easy_way_to_start_debugging"></a> La méthode simple pour démarrer le débogage  
 ![S'applique uniquement à Windows](../debugger/media/windows_only_content.png "windows\_only\_content")  
  
1.  Ouvrez la solution d'application dans Visual Studio.  
  
2.  Si la solution contient des projets pour les applications du Windows Store et du Windows Phone Store, assurez\-vous que le projet à déboguer est le projet de démarrage. Dans l'Explorateur de solutions, sélectionnez le projet et choisissez **Définir comme projet de démarrage** dans le menu contextuel.  
  
3.  Appuyez sur F5.  
  
 ![S'applique uniquement à Windows Phone](../debugger/media/phone_only_content.png "phone\_only\_content")  
  
 Visual Studio génère et démarre l'application avec le débogueur attaché. L'exécution se poursuit jusqu'à ce qu'un point d'arrêt soit atteint, que vous suspendiez manuellement l'exécution, qu'une exception non gérée se produise ou que l'application se termine. Pour plus d'informations, consultez [Démarrage rapide : déboguer du code HTML et CSS](../debugger/quickstart-debug-html-and-css.md).  
  
##  <a name="BKMK_Configure_the_debugging_session"></a> Configurer la session de débogage  
 Comme le script n'est pas compilé, les paramètres de plateforme et de configuration de build ne s'appliquent pas. Si vous déboguez un composant C\+\+ ou un composant managé, affectez la valeur **Déboguer** à **Configuration** et sélectionnez votre plateforme cible dans la boîte de dialogue **Configuration**.  
  
###  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Ouvrir la page des propriétés de débogage du projet  
  
1.  Dans l'Explorateur de solutions, sélectionnez le projet. Dans le menu contextuel, choisissez **Propriétés**.  
  
2.  Développez le nœud **Propriétés de configuration**, puis sélectionnez **Débogage**.  
  
###  <a name="BKMK_Choose_the_build_configuration_options"></a> Choisir les options de configuration de build  
  
1.  Dans la liste **Configuration**, choisissez **Déboguer** ou **\(Actif\) Déboguer**.  
  
2.  Dans la liste **Plateforme**, sélectionnez la plateforme cible pour laquelle générer. Dans la plupart des cas, le meilleur choix est **Any CPU**.  
  
###  <a name="BKMK_Choose_the_deployment_target"></a> Sélectionner la cible de déploiement  
 Vous pouvez déployer et déboguer une application sur l'ordinateur Visual Studio, dans le simulateur Visual Studio sur l'ordinateur local ou sur un appareil distant. Vous choisissez la cible dans la liste **Débogueur à lancer** de la page de propriétés **Débogage** du projet.  
  
 ![S'applique uniquement à Windows](../debugger/media/windows_only_content.png "windows\_only\_content")  
  
 Pour une application du Windows Store, choisissez l'une des options suivantes dans la liste **Appareil cible** :  
  
|||  
|-|-|  
|**Ordinateur local**|Déboguez l'application dans la session active sur votre ordinateur local. Consultez [Exécuter des applications du Windows Store sur un ordinateur local](../debugger/run-windows-store-apps-on-the-local-machine.md).|  
|**Simulateur**|Déboguez l'application dans le simulateur Visual Studio pour les applications [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]. Le simulateur est une fenêtre du Bureau qui permet de déboguer les fonctionnalités de l'appareil, comme les mouvements tactiles et la rotation de l'appareil, qui ne sont pas disponibles sur l'ordinateur local. Consultez [Exécuter des applications du Windows Store dans le simulateur](../debugger/run-windows-store-apps-in-the-simulator.md).|  
|**Ordinateur distant**|Déboguez l'application sur un appareil connecté à l'ordinateur local sur un intranet ou directement connecté via un câble Ethernet. Pour déboguer à distance, les outils de contrôle à distance Visual Studio doivent être installés et en cours d'exécution sur l'appareil distant. Consultez [Exécuter des applications du Windows Store sur un ordinateur distant](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
  
 Si vous choisissez **Ordinateur distant**, spécifiez le nom ou l'adresse IP de l'ordinateur distant de l'une des manières suivantes :  
  
-   Entrez le nom ou l'adresse IP de l'ordinateur distant dans la zone **Nom de l'ordinateur**.  
  
-   Choisissez la flèche Bas dans la zone **Nom de l'ordinateur**, puis sélectionnez **\<Rechercher...\>**. Choisissez ensuite l'ordinateur distant dans la boîte de dialogue **Sélectionner une connexion du débogueur distant**.  
  
     ![Sélectionner la connexion au Remote Debugger](../debugger/media/vsrun_pro_selectremotedebuggerdlg.png "VSRUN\_PRO\_SelectRemoteDebuggerDlg")  
  
    > [!NOTE]
    >  La boîte de dialogue Sélectionner une connexion du débogueur distant affiche les ordinateurs situés sur le sous\-réseau local et les ordinateurs locaux qui sont directement connectés à l'ordinateur Visual Studio via un câble Ethernet. Pour spécifier un autre ordinateur, entrez le nom dans la zone **Nom de l'ordinateur**.  
  
 ![S'applique uniquement à Windows Phone](../debugger/media/phone_only_content.png "phone\_only\_content")  
  
 Pour une application du Windows Phone Store, sélectionnez **Appareil** ou l'un des émulateurs de la liste **Appareil cible**.  
  
###  <a name="BKMK_Choose_the_debugger_to_use"></a> Choisir le débogueur à utiliser  
 Par défaut, le débogueur s'attache au code JavaScript de votre application. Vous pouvez choisir de déboguer le code natif C\+\+ et le code managé des composants de votre application à la place du code JavaScript. Spécifiez le code à déboguer dans la liste **Type de débogueur** de la page de propriétés **Débogage** du projet d'application.  
  
 Choisissez l'un de ces débogueurs dans la liste **Type de débogueur** :  
  
|||  
|-|-|  
|**Script uniquement**|Déboguez le code JavaScript dans votre application. Le code managé et le code natif sont ignorés.|  
|**Natif uniquement**|Déboguez le code natif C\/C\+\+ dans votre application. Le code managé et le code JavaScript sont ignorés.|  
|**Code natif avec script**|Déboguez le code natif C\+\+ et le code JavaScript dans votre application.|  
|**Managé uniquement**|Déboguez le code managé dans votre application. Le code JavaScript et le code natif C\/C\+\+ sont ignorés.|  
|**Mixte \(natif et managé\)**|Déboguez le code natif et managé C\/C\+\+ dans votre application. Le code JavaScript est ignoré.|  
  
###  <a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a> \(Facultatif\) Retarder le démarrage de l'application dans la session de débogage  
 Par défaut, Visual Studio démarre immédiatement l'application lorsque vous démarrez le débogage. Vous pouvez également démarrer une session de débogage et retarder le démarrage de votre application. L'application est lancée dans le débogueur quand elle est elle\-même lancée depuis le menu Démarrer ou par un contrat d'activation, ou qu'elle est démarrée au moyen d'une autre procédure ou méthode. Vous pouvez aussi utiliser le démarrage différé pour déboguer les événements en arrière\-plan de votre application dont vous voulez qu'ils se produisent alors que l'application n'est pas en cours d'exécution.  
  
 Vous spécifiez si le lancement de votre application doit être différé dans la liste **Lancer l'application** de la page de propriétés **Débogage** du projet de l'application. Choisissez l'une des options suivantes :  
  
-   Choisissez **Non** pour différer le lancement de votre application.  
  
-   Choisissez **Oui** pour lancer l'application immédiatement.  
  
###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> Désactiver les bouclages de réseau \(facultatif\)  
 ![S'applique uniquement à Windows](../debugger/media/windows_only_content.png "windows\_only\_content")  
  
 Pour des raisons de sécurité, une application du Windows Store installée en mode standard n'est pas autorisée à effectuer des appels réseau vers l'appareil sur lequel elle est installée. Par défaut, le déploiement Visual Studio crée une exemption à cette règle pour l'application déployée. Cette exemption vous permet de tester les procédures de communication sur un seul ordinateur. Avant de soumettre votre application au Windows Store, vous devez la tester sans l'exemption.  
  
 Pour supprimer l'exemption de bouclage de réseau, choisissez **Non** dans la liste **Autoriser le bouclage de réseau** de la page de propriétés **Débogage**.  
  
##  <a name="BKMK_Start_the_debugging_session"></a> Démarrer la session de débogage  
  
###  <a name="BKMK_Start_debugging__F5_"></a> Démarrer le débogage \(F5\)  
 Quand vous choisissez **Démarrer le débogage** \(clavier : **F5**\) dans le menu Déboguer, Visual Studio lance l'application avec le débogueur attaché. L'exécution se poursuit jusqu'à ce qu'un point d'arrêt soit atteint, que vous suspendiez manuellement l'exécution, qu'une exception non gérée se produise ou que l'application se termine.  
  
###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Démarrer le débogage \(F5\), mais différer le démarrage de l'application  
 Vous pouvez configurer l'application pour qu'elle s'exécute en mode débogage, mais puisse être démarrée par une autre méthode que le débogueur. Vous pouvez par exemple déboguer le lancement de votre application depuis le menu Démarrer ou déboguer un processus en arrière\-plan dans l'application sans la démarrer. Pour retarder le démarrage de l'application, procédez comme suit :  
  
1.  Dans la page **Déboguer** des propriétés de projet de l'application, choisissez **Non** dans la liste **Lancer l'application**.  
  
2.  Choisissez **Démarrer le débogage** dans le menu **Déboguer** \(clavier : F5\).  
  
3.  Démarrez votre application à partir du menu Démarrer, avec un contrat d'exécution ou en suivant une autre procédure.  
  
 L'application démarre en mode débogage. L'exécution se poursuit jusqu'à ce qu'un point d'arrêt soit atteint, que vous suspendiez manuellement l'exécution, qu'une exception non gérée se produise ou que l'application se termine.  
  
 Pour plus d'informations sur le débogage des tâches en arrière\-plan, consultez [Déclencher des événements de suspension, de reprise et d'arrière\-plan pour Windows Store](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
##  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Démarrer une application installée dans le débogueur  
 Quand vous lancez le débogage en appuyant sur la touche F5, Visual Studio génère et déploie l'application, la configure pour s'exécuter en mode débogage, puis la démarre. Pour démarrer une application déjà installée sur un périphérique, utilisez la boîte de dialogue Déboguer le package d'application déjà installé. Cette procédure est utile lorsque vous devez déboguer une application installée depuis Windows Store, ou lorsque vous disposez des fichiers source de l'application, mais pas de projet Visual Studio pour cette dernière. Par exemple, vous pouvez avoir un système de génération personnalisée qui n'utilise pas les projets ou les solutions Visual Studio.  
  
 L'application peut être installée sur l'appareil local ou sur un appareil distant. Vous pouvez démarrer l'application immédiatement, ou bien la configurer pour s'exécuter dans le débogueur au démarrage de ce dernier par un autre processus ou une autre méthode, depuis le menu Démarrer ou par un contrat d'activation, par exemple. Vous pouvez également configurer l'application pour s'exécuter en mode débogage lorsque vous souhaitez déboguer un processus en arrière\-plan sans démarrer l'application. Pour plus d'informations, consultez [Déclencher des événements de suspension, de reprise et d'arrière\-plan pour Windows Store](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
 Pour configurer une application installée pour s'exécuter en mode débogage, procédez comme suit :  
  
> [!NOTE]
>  L'application ne doit pas être en cours d'exécution quand vous lancez cette procédure.  
  
1.  Dans le menu **Débogage**, choisissez **Déboguer le package d'application installé**.  
  
2.  Choisissez l'une des options suivantes dans la liste :  
  
    |||  
    |-|-|  
    |**Ordinateur local**|Déboguez l'application dans la session active sur votre ordinateur local. Consultez [Exécuter des applications du Windows Store sur un ordinateur local](../debugger/run-windows-store-apps-on-the-local-machine.md).|  
    |**Simulateur**|Déboguez l'application dans le simulateur Visual Studio pour les applications [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]. Le simulateur est une fenêtre du Bureau qui permet de déboguer les fonctionnalités du périphérique, comme les mouvements tactiles et la rotation du périphérique, qui ne sont pas disponibles sur l'ordinateur local. Consultez [Exécuter des applications du Windows Store dans le simulateur](../debugger/run-windows-store-apps-in-the-simulator.md).|  
    |**Ordinateur distant**|Déboguez l'application sur un appareil connecté à l'ordinateur local sur un intranet ou directement connecté via un câble Ethernet. Pour déboguer à distance, les outils de contrôle à distance Visual Studio doivent être installés et en cours d'exécution sur le périphérique distant. Consultez [Exécuter des applications du Windows Store sur un ordinateur distant](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
  
3.  Choisissez l'application dans la liste **Packages d'application installés**.  
  
4.  Choisissez le moteur de débogage à utiliser dans la liste **Déboguer ce type de code**.  
  
5.  \(Facultatif\). Choisissez **Ne pas lancer, mais déboguer mon code au démarrage** pour déboguer l'application lorsqu'elle est lancée à l'aide d'une autre méthode ou pour déboguer un processus en arrière\-plan.  
  
 Quand vous cliquez sur **Démarrer**, l'application démarre ou est configurée pour s'exécuter en mode débogage.  
  
##  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Attacher le débogueur à une application en cours d'exécution  
 Pour attacher le débogueur à une application [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)], vous devez utiliser Debuggable Package Manager pour configurer l'application à exécuter en mode débogage. Debuggable Package Manager est installé avec les outils de contrôle à distance Visual Studio.  
  
 Attacher le débogueur à une application est utile lorsque vous devez déboguer une application déjà installée, telle qu'une application qui a été installée à partir du Windows Store. L'attachement est requis lorsque vous possédez les fichiers sources de l'application, mais que vous n'avez pas de projet Visual Studio pour l'application. Par exemple, vous pouvez avoir un système de génération personnalisée qui n'utilise pas les projets ou les solutions Visual Studio.  
  
 Pour attacher à une application  
  
1.  Configurez l'application pour l'exécuter en mode débogage Vous devez effectuer cette opération quand l'application n'est pas en cours d'exécution.  
  
2.  Démarrez l'application. Vous pouvez démarrer l'application à partir du menu Démarrer, d'un contrat d'exécution ou de toute autre méthode.  
  
3.  Attachez le débogueur à l'application en cours d'exécution.  
  
###  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> Configurer l'application pour l'exécuter en mode débogage  
  
1.  Installez les outils de contrôle à distance Visual Studio sur l'appareil où l'application est installée. Consultez [Installation des outils de contrôle à distance](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).  
  
2.  Dans le menu Démarrer, recherchez `Debuggable Package Manager`, puis démarrez\-le.  
  
     Une fenêtre PowerShell correctement configurée pour l'applet de commande AppxDebug s'affiche.  
  
3.  Pour activer le débogage d'une application, vous devez spécifier l'identificateur PackageFullName de l'application. Pour afficher une liste de toutes les applications avec PackageFullName, tapez `Get-AppxPackage` à l'invite PowerShell.  
  
4.  À l'invite PowerShell, entrez `Enable-AppxDebug` *PackageFullName*, où *PackageFullName* est l'identificateur PackageFullName de l'application.  
  
###  <a name="BKMK_Attach_the_debugger"></a> Attacher le débogueur  
  
> [!TIP]
>  Les applications JavaScript s'exécutent dans une instance du processus wwahost.exe. Si d'autres applications JavaScript sont en cours d'exécution pendant l'attachement à l'application, vous devez connaître l'identifiant de processus \(PID\) numérique du processus wwahost.exe dans lequel l'application s'exécute.  
>   
>  La solution la plus simple pour gérer cette situation consiste à fermer toutes les autres applications JavaScript. Sinon, vous pouvez ouvrir le Gestionnaire de tâches Windows avant de démarrer l'application et de noter les identifiants des processus wwahost.exe. Quand vous spécifiez le processus à attacher dans la boîte de dialogue **Processus disponibles**, le processus wwahost.exe de l'application a un identifiant différent de ceux que vous avez déjà notés.  
  
 Pour attacher le débogueur  
  
1.  Dans le menu **Déboguer**, choisissez **Attacher au processus**.  
  
     La boîte de dialogue **Attacher au processus** s'affiche.  
  
2.  Pour attacher une application à un appareil distant, spécifiez l'appareil distant dans la zone **Qualificateur**. Vous pouvez effectuer les tâches suivantes :  
  
    -   entrer le nom dans la zone **Qualificateur** ;  
  
    -   cliquer sur la flèche Bas dans la zone **Qualificateur**, puis choisir l'appareil dans une liste d'appareils que vous avez attachés précédemment ;  
  
    -   choisir **Rechercher** pour sélectionner l'appareil dans une liste d'appareils sur votre sous\-réseau local.  
  
3.  Spécifiez le type de code que vous souhaitez déboguer dans la zone **Attacher à**.  
  
     Choisissez **Sélectionner**, puis effectuez l'une des opérations suivantes :  
  
    -   Choisissez **Déterminer automatiquement le type de code à déboguer**.  
  
    -   Choisissez **Déboguer ces types de codes**, puis sélectionnez un ou plusieurs types dans la liste.  
  
4.  Dans la liste **Processus disponibles**, choisissez le processus **wwahost.exe** approprié. Utilisez la colonne **Titre** pour identifier votre application.  
  
5.  Choisissez **Attacher**.  
  
 Visual Studio attache le débogueur au processus. L'exécution se poursuit jusqu'à ce qu'un point d'arrêt soit atteint, que vous suspendiez manuellement l'exécution, qu'une exception non gérée se produise ou que l'application se termine.  
  
## Voir aussi  
 [Contrôler l'exécution dans une session de débogage \(JavaScript\)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md)   
 [Démarrage rapide : déboguer du code HTML et CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Déclencher des événements de suspension, de reprise et d'arrière\-plan pour Windows Store](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)   
 [Déboguer des applications dans Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)