---
title: Démarrer une session de débogage pour les applications de Store (JavaScript) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: fb91203f-2cf4-44d3-8ed9-93bc5aaa50b8
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 600f44cccd57635cc789e2265fe5451e5674d737
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938436"
---
# <a name="start-a-debugging-session-for-store-apps-in-visual-studio-javascript"></a>Démarrer une session de débogage dans Visual Studio (JavaScript) pour des applications du Windows Store
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

S’applique à Windows et Windows Phone] (.. /Image/windows_and_phone_content.png « windows_and_phone_content »)

 Cette rubrique explique comment démarrer une session de débogage pour les applications du Windows Store écrites en JavaScript et HTML5. Vous pouvez démarrer le débogage avec une seule séquence de touches ou configurer la session de débogage pour des scénarios spécifiques, puis choisir de quelle façon démarrer l'application.

> [!NOTE]
>  Pour les applications écrites en XAML et Visual c#, Visual C++ ou Visual Basic, consultez [démarrer une session de débogage (VB, c#, C++ et XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

##  <a name="BKMK_In_this_topic"></a> Dans cette rubrique
 [Dans cette rubrique](#BKMK_In_this_topic)

 [La méthode simple pour démarrer le débogage](#BKMK_The_easy_way_to_start_debugging)

 [Configurer la session de débogage](#BKMK_Configure_the_debugging_session)

- [Ouvrir la page des propriétés de débogage du projet](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Choisir les options de configuration de build](#BKMK_Choose_the_build_configuration_options)

- [Sélectionner la cible de déploiement](#BKMK_Choose_the_deployment_target)

- [Choisir le débogueur à utiliser](#BKMK_Choose_the_debugger_to_use)

- [(Facultatif) Différer le démarrage de l’application dans la session de débogage](#BKMK__Optional__Delay_starting_app_in_the_debug_session)

- [Désactiver les bouclages de réseau (facultatif)](#BKMK__Optional__Disable_network_loopbacks)

  [Démarrer la session de débogage](#BKMK_Start_the_debugging_session)

- [Démarrer le débogage (F5)](#BKMK_Start_debugging__F5_)

- [Démarrer le débogage (F5), mais différer le démarrage de l'application](#BKMK_Start_debugging__F5__but_delay_the_app_start)

  [Démarrer une application installée dans le débogueur](#BKMK_Start_an_installed_app_in_the_debugger)

  [Attacher le débogueur à une application en cours de exécution](#BKMK_Attach_the_debugger_to_a_running_app_)

- [Configurer l'application pour l'exécuter en mode débogage](#BKMK_Set_the_app_to_run_in_debug_mode)

- [Attacher le débogueur](#BKMK_Attach_the_debugger)

##  <a name="BKMK_The_easy_way_to_start_debugging"></a> La méthode simple pour démarrer le débogage
 ![S’applique uniquement à Windows](../debugger/media/windows-only-content.png "windows_only_content")

1. Ouvrez la solution d'application dans Visual Studio.

2. Si la solution contient des projets pour les applications du Windows Store et du Windows Phone Store, assurez-vous que le projet à déboguer est le projet de démarrage. Dans l’Explorateur de solutions, sélectionnez le projet, puis choisissez **définir comme projet de démarrage** dans le menu contextuel.

3. Appuyez sur F5.

   ![S’applique uniquement à Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

   Visual Studio génère et démarre l'application avec le débogueur attaché. L'exécution se poursuit jusqu'à ce qu'un point d'arrêt soit atteint, que vous suspendiez manuellement l'exécution, qu'une exception non gérée se produise ou que l'application se termine. Pour plus d’informations, consultez [Démarrage rapide : Déboguer le code HTML et CSS](../debugger/quickstart-debug-html-and-css.md).

##  <a name="BKMK_Configure_the_debugging_session"></a> Configurer la session de débogage
 Comme le script n'est pas compilé, les paramètres de plateforme et de configuration de build ne s'appliquent pas. Si vous déboguez un composant C++ ou composant managé, définissez le **Configuration** à **déboguer** et choisissez votre plateforme cible à partir de la **Configuration** boîte de dialogue.

###  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Ouvrir la page des propriétés de débogage du projet

1.  Dans l'Explorateur de solutions, sélectionnez le projet. Dans le menu contextuel, choisissez **Propriétés**.

2.  Développez le **propriétés de Configuration** nœud, puis choisissez **débogage**

###  <a name="BKMK_Choose_the_build_configuration_options"></a> Choisir les options de configuration de build

1.  Dans la liste **Configuration** , choisissez **Déboguer** ou **(Debug) active**.

2.  Dans la liste **Plateforme** , sélectionnez la plateforme cible à générer. Dans la plupart des cas, **Any CPU** est le meilleur choix.

###  <a name="BKMK_Choose_the_deployment_target"></a> Sélectionner la cible de déploiement
 Vous pouvez déployer et déboguer une application sur l’ordinateur Visual Studio, dans le simulateur Visual Studio sur l’ordinateur local ou sur un périphérique distant. Vous choisissez la cible dans le **débogueur à lancer** liste sur le **débogage** page de propriétés pour le projet.

 ![S’applique uniquement à Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Pour une application Windows Store, choisissez une des options suivantes dans le **appareil cible** liste :

|||
|-|-|
|**Ordinateur local**|Déboguez l'application dans la session active sur votre ordinateur local. Consultez [Run Windows Store des applications sur l’ordinateur local](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Simulateur**|Déboguez l'application dans le simulateur Visual Studio pour les applications [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] . Le simulateur est une fenêtre du Bureau qui permet de déboguer les fonctionnalités du périphérique, comme les mouvements tactiles et la rotation du périphérique, qui ne sont pas disponibles sur l'ordinateur local. Consultez [Run Windows Store des applications dans le simulateur](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Ordinateur distant**|Déboguez l'application sur un périphérique qui est connecté à l'ordinateur local sur un intranet ou directement connecté via un câble Ethernet. Pour déboguer à distance, les outils de contrôle à distance Visual Studio doivent être installés et en cours d'exécution sur le périphérique distant. Consultez [applications Run Windows Store sur un ordinateur distant](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 Si vous choisissez **Ordinateur distant**, spécifiez le nom ou l'adresse IP de l'ordinateur distant de l'une des manières suivantes :

- Entrez le nom ou l’adresse IP de l’ordinateur distant dans le **nom_machine** boîte.

- Choisissez la flèche bas dans la **nom_machine** et sélectionnez  **\<rechercher... >**. Choisissez ensuite l’ordinateur distant à partir de **sélectionner une connexion du débogueur distant** boîte de dialogue.

   ![Sélectionnez une connexion du débogueur distant](../debugger/media/vsrun-pro-selectremotedebuggerdlg.png "VSRUN_PRO_SelectRemoteDebuggerDlg")

  > [!NOTE]
  >  La boîte de dialogue Sélectionner une connexion du débogueur distant affiche les ordinateurs situés sur le sous-réseau local et les ordinateurs locaux qui sont directement connectés à l'ordinateur Visual Studio via un câble Ethernet. Pour spécifier un autre ordinateur, entrez le nom dans la zone **Nom de l'ordinateur** .

  ![S’applique uniquement à Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

  Pour une application Windows Store Phone, choisissez **appareil** ou l’un des émulateurs à partir de la **appareil cible** liste.

###  <a name="BKMK_Choose_the_debugger_to_use"></a> Choisir le débogueur à utiliser
 Par défaut, le débogueur s'attache au code JavaScript de votre application. Vous pouvez choisir de déboguer le code natif C++ et le code managé des composants de votre application à la place du code JavaScript. Spécifiez le code à déboguer dans la liste **Type de débogueur** de la page des propriétés de **débogage** du projet d'application.

 Choisissez une de ces débogueurs dans la **Type de débogueur** liste :

|||
|-|-|
|**Script uniquement**|Déboguez le code JavaScript dans votre application. Le code managé et le code natif sont ignorés.|
|**Natif uniquement**|Déboguez le code natif C/C++ dans votre application. Le code managé et le code JavaScript sont ignorés.|
|**Code natif avec script**|Déboguez le code natif C++ et le code JavaScript de votre application.|
|**Managé uniquement**|Déboguez le code managé dans votre application. Le code JavaScript et le code natif C/C++ sont ignorés.|
|**Mixte (natif et managé)**|Déboguez le code natif et managé C/C++ dans votre application. Le code JavaScript est ignoré.|

###  <a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a> (Facultatif) Différer le démarrage de l’application dans la session de débogage
 Par défaut, Visual Studio démarre immédiatement l'application lorsque vous démarrez le débogage. Vous pouvez également démarrer une session de débogage et retarder le démarrage de votre application. L'application est lancée dans le débogueur quand elle est elle-même lancée depuis le menu Démarrer ou par un contrat d'activation, ou qu'elle est démarrée au moyen d'une autre procédure ou méthode. Vous pouvez aussi utiliser le démarrage différé pour déboguer les événements en arrière-plan de votre application dont vous voulez qu'ils se produisent alors que l'application n'est pas en cours d'exécution.

 Vous spécifiez s’il faut différer le lancement de votre application dans le **lancer l’Application** liste sur le **débogage** page de propriétés de projet d’application. Choisissez l'une des options suivantes :

-   Choisissez **non** pour différer le lancement de votre application.

-   Choisissez **Oui** pour lancer l’application immédiatement.

###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> Désactiver les bouclages de réseau (facultatif)
 ![S’applique uniquement à Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Pour des raisons de sécurité, une application Windows Store installée en mode standard n'est pas autorisée à effectuer des appels réseau vers le périphérique sur lequel elle est installée. Par défaut, le déploiement Visual Studio crée une exemption à cette règle pour l'application déployée. Cette exemption vous permet de tester les procédures de communication sur un seul ordinateur. Avant d'envoyer votre application au Windows Store, vous devez la tester sans l'exemption.

 Pour supprimer l’exemption de bouclage de réseau, choisissez **non** à partir de la **autoriser le bouclage de réseau** liste sur le **débogage** page de propriétés.

##  <a name="BKMK_Start_the_debugging_session"></a> Démarrer la session de débogage

###  <a name="BKMK_Start_debugging__F5_"></a> Démarrer le débogage (F5)
 Lorsque vous choisissez **démarrer le débogage** sur le **déboguer** menu (clavier : F5), Visual Studio lance l’application avec le débogueur attaché. L'exécution se poursuit jusqu'à ce qu'un point d'arrêt soit atteint, que vous suspendiez manuellement l'exécution, qu'une exception non gérée se produise ou que l'application se termine.

###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Démarrer le débogage (F5), mais différer le démarrage de l'application
 Vous pouvez configurer l'application pour qu'elle s'exécute en mode débogage, mais puisse être démarrée par une autre méthode que le débogueur. Vous pouvez par exemple déboguer le lancement de votre application depuis le menu Démarrer ou déboguer un processus en arrière-plan dans l'application sans la démarrer. Procédez comme suit pour retarder le démarrage de l'application :

1. Sur le **déboguer** page de l’application propriétés de projet, choisissez **non** à partir de la **lancer l’Application** liste.

2. Choisissez **démarrer le débogage** sur le **déboguer** menu (clavier : F5).

3. Démarrez votre application dans le menu Démarrer, avec un contrat de exécution ou en suivant une autre procédure.

   L'application démarre en mode débogage. L'exécution se poursuit jusqu'à ce qu'un point d'arrêt soit atteint, que vous suspendiez manuellement l'exécution, qu'une exception non gérée se produise ou que l'application se termine.

   . Pour plus d’informations sur le débogage des tâches en arrière-plan, consultez [déclencheur suspendre, reprendre, événements et d’arrière-plan pour le Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

##  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Démarrer une application installée dans le débogueur
 Lorsque vous lancez le débogage en appuyant sur la touche F5, Visual Studio génère et déploie l'application, la configure pour s'exécuter en mode débogage, puis la démarre. Pour démarrer une application déjà installée sur un périphérique, utilisez la boîte de dialogue Déboguer le package d'application déjà installé. Cette procédure est utile lorsque vous devez déboguer une application installée depuis Windows Store, ou lorsque vous disposez des fichiers source de l'application, mais pas de projet Visual Studio pour cette dernière. Par exemple, vous pouvez avoir un système de génération personnalisée qui n'utilise pas les projets ou les solutions Visual Studio.

 Vous pouvez installer l'application sur le périphérique local ou sur un périphérique distant.  Vous pouvez démarrer l'application immédiatement, ou bien la configurer pour s'exécuter dans le débogueur au démarrage de ce dernier par un autre processus ou une autre méthode, depuis le menu Démarrer ou par un contrat d'activation, par exemple. Vous pouvez également configurer l'application pour s'exécuter en mode débogage lorsque vous souhaitez déboguer un processus en arrière-plan sans démarrer l'application. Pour plus d’informations, consultez [déclencheur suspendre, reprendre, événements et d’arrière-plan pour le Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

 Procédez comme suit pour configurer une application installée pour s'exécuter en mode débogage :

> [!NOTE]
>  L'application ne doit pas être en cours d'exécution lorsque vous lancez cette procédure.

1. Dans le menu **Débogage** , choisissez **Déboguer le package d'application installé**

2. Choisissez l'une des options suivantes dans la liste :


   |                    |                                                                                                                                                                                                                                                                                                                                                                                                           |
   |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Ordinateur local**  |                                                                                                                Déboguez l'application dans la session active sur votre ordinateur local. Consultez [Run Windows Store des applications sur l’ordinateur local](../debugger/run-windows-store-apps-on-the-local-machine.md).                                                                                                                 |
   |   **Simulateur**    | Déboguez l'application dans le simulateur Visual Studio pour les applications [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] . Le simulateur est une fenêtre du Bureau qui permet de déboguer les fonctionnalités du périphérique, comme les mouvements tactiles et la rotation du périphérique, qui ne sont pas disponibles sur l'ordinateur local. Consultez [Run Windows Store des applications dans le simulateur](../debugger/run-windows-store-apps-in-the-simulator.md). |
   | **Ordinateur distant** |                          Déboguez l'application sur un périphérique qui est connecté à l'ordinateur local sur un intranet ou directement connecté via un câble Ethernet. Pour déboguer à distance, les outils de contrôle à distance Visual Studio doivent être installés et en cours d'exécution sur le périphérique distant. Consultez [applications Run Windows Store sur un ordinateur distant](../debugger/run-windows-store-apps-on-a-remote-machine.md).                           |


3. Choisissez l'application dans la liste **Packages d'application installés** .

4. Choisissez le moteur de débogage à utiliser dans la liste **Déboguer ce type de code** .

5. (Facultatif). Choisissez **Ne pas lancer, mais déboguer mon code au démarrage** pour déboguer l'application lorsqu'elle est lancée à l'aide d'une autre méthode ou pour déboguer un processus en arrière-plan.

   Lorsque vous cliquez sur **Démarrer**, l'application démarre ou est configurée pour s'exécuter en mode débogage.

##  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Attacher le débogueur à une application en cours de exécution
 Pour attacher le débogueur à une application [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] , vous devez utiliser Debuggable Package Manager pour configurer l'application à exécuter en mode débogage. Debuggable Package Manager est installé avec les outils de contrôle à distance Visual Studio.

 Attacher le débogueur à une application est utile lorsque vous devez déboguer une application déjà installée, telle qu'une application qui a été installée à partir du Windows Store. L'attachement est requis lorsque vous possédez les fichiers sources de l'application, mais que vous n'avez pas de projet Visual Studio pour l'application. Par exemple, vous pouvez avoir un système de génération personnalisée qui n'utilise pas les projets ou les solutions Visual Studio.

 Pour attacher à une application :

1.  Configurez l'application pour l'exécuter en mode débogage. Cela doit s'effectuer lorsque l'application n'est pas en cours d'exécution.

2.  Démarrez l'application. Vous pouvez démarrer l'application à partir du menu Démarrer, d'un contrat d'exécution ou de toute autre méthode.

3.  Attacher le débogueur à l'application en cours d'exécution.

###  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> Configurer l'application pour l'exécuter en mode débogage

1.  Installez les outils de contrôle à distance Visual Studio sur le périphérique où l'application est installée. Consultez [l’installation des outils à distance](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2.  Sur le menu Démarrer, recherchez `Debuggable Package Manager`, puis démarrez-le.

     Une fenêtre PowerShell correctement configurée pour l'applet de commande AppxDebug s'affiche.

3.  Pour activer le débogage d'une application, vous devez spécifier l'identificateur PackageFullName de l'application. Pour afficher une liste de toutes les applications qui incluent PackageFullName, entrez `Get-AppxPackage` à l'invite de PowerShell.

4.  À l'invite de PowerShell, entrez `Enable-AppxDebug` *PackageFullName* , où *PackageFullName* est l'identificateur PackageFullName de l'application.

###  <a name="BKMK_Attach_the_debugger"></a> Attacher le débogueur

> [!TIP]
>  Les applications JavaScript s'exécutent dans une instance du processus wwahost.exe. Si d'autres applications JavaScript sont en cours d'exécution pendant l'attachement à l'application, vous devez connaître l'identifiant de processus (PID) numérique du processus wwahost.exe dans lequel l'application s'exécute.
>
>  La solution la plus simple pour gérer cette situation consiste à fermer toutes les autres applications JavaScript. Sinon, vous pouvez ouvrir le Gestionnaire de tâches Windows avant de démarrer l'application et de noter les identifiants des processus wwahost.exe. Lorsque vous spécifiez le processus à attacher à la **processus disponibles** boîte de dialogue, le wwahost.exe de l’application aura un identifiant qui est différent de ceux que vous avez déjà notés.

 Pour attacher le débogueur :

1. Dans le menu **Débogage** , sélectionnez **Attacher au processus**.

    La boîte de dialogue **Attacher au processus** s'affiche.

2. Pour attacher une application sur un périphérique distant, spécifiez le périphérique distant dans la zone **Qualificateur** . Vous pouvez :

   -   Entrez le nom dans la zone **Qualificateur** .

   -   Cliquez sur la flèche vers le bas dans la **qualificateur** et sélectionnez l’appareil à partir d’une liste de périphériques que vous avez associée précédemment.

   -   Choisissez **trouver** pour sélectionner le périphérique à partir d’une liste de périphériques sur votre sous-réseau local.

3. Spécifiez le type de code à déboguer dans la zone **Attacher à** .

    Choisissez **Sélectionner** , puis effectuez l'une des opérations suivantes :

   -   Choisissez **Déterminer automatiquement le type de code à déboguer**

   -   Choisissez **Déboguer ces types de codes** , puis sélectionnez un ou plusieurs types dans la liste.

4. Dans le **processus disponibles** liste, choisissez le **wwahost.exe** processus. Utilisez le **titre** colonne pour identifier votre application.

5. Choisissez **Attacher**.

   Visual Studio attache le débogueur au processus. L'exécution se poursuit jusqu'à ce qu'un point d'arrêt soit atteint, que vous suspendiez manuellement l'exécution, qu'une exception non gérée se produise ou que l'application se termine.

## <a name="see-also"></a>Voir aussi
 [Contrôler l’exécution dans une session de débogage (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) [Guide de démarrage rapide : Déboguer du code HTML et CSS](../debugger/quickstart-debug-html-and-css.md) [déclencheur suspendre, reprendre, événements et d’arrière-plan pour le Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [déboguer des applications dans Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
