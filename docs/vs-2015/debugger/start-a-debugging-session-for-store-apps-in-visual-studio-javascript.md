---
title: Démarrer une session de débogage pour Les applications de magasins (JavaScript) Microsoft Docs
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
ms.openlocfilehash: 4b4e861c8985ee37a8c2d9b7f9286d6284bb4f91
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302482"
---
# <a name="start-a-debugging-session-for-store-apps-in-visual-studio-javascript"></a>Démarrer une session de débogage dans Visual Studio (JavaScript) pour des applications du Windows Store
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

S’applique à Windows et Windows Phone)(.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Cette rubrique explique comment démarrer une session de débogage pour les applications du Windows Store écrites en JavaScript et HTML5. Vous pouvez démarrer le débogage avec une seule séquence de touches ou configurer la session de débogage pour des scénarios spécifiques, puis choisir de quelle façon démarrer l'application.

> [!NOTE]
> Pour les applications écrites en XAML et Visual C, Visual CMD, ou Visual Basic, consultez [la session Démarrer un débbug (VB, C, C et XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a>Dans ce sujet
 [Dans ce sujet](#BKMK_In_this_topic)

 [La méthode simple pour démarrer le débogage](#BKMK_The_easy_way_to_start_debugging)

 [Configurer la session de débogage](#BKMK_Configure_the_debugging_session)

- [Ouvrez la page de propriété de débogage pour le projet](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Choisissez les options de configuration de construction](#BKMK_Choose_the_build_configuration_options)

- [Sélectionner la cible de déploiement](#BKMK_Choose_the_deployment_target)

- [Choisissez le débbuggeur à utiliser](#BKMK_Choose_the_debugger_to_use)

- [Retarder le démarrage de l'application dans la session de débogage  (facultatif)](#BKMK__Optional__Delay_starting_app_in_the_debug_session)

- [Désactiver les bouclages de réseau (facultatif)](#BKMK__Optional__Disable_network_loopbacks)

  [Démarrer la session de débogage](#BKMK_Start_the_debugging_session)

- [Commencez à débogage (F5)](#BKMK_Start_debugging__F5_)

- [Démarrer le débogage (F5), mais différer le démarrage de l'application](#BKMK_Start_debugging__F5__but_delay_the_app_start)

  [Démarrer une application installée dans le débbugger](#BKMK_Start_an_installed_app_in_the_debugger)

  [Attachez le débbuggeur à une application en cours d’exécution](#BKMK_Attach_the_debugger_to_a_running_app_)

- [Réglez l’application pour qu’elle s’exécute en mode débogé](#BKMK_Set_the_app_to_run_in_debug_mode)

- [Attacher le débogueur](#BKMK_Attach_the_debugger)

## <a name="the-easy-way-to-start-debugging"></a><a name="BKMK_The_easy_way_to_start_debugging"></a>Le moyen facile de commencer à débogage
 ![S’applique à Windows uniquement](../debugger/media/windows-only-content.png "windows_only_content")

1. Ouvrez la solution d'application dans Visual Studio.

2. Si la solution contient des projets pour les applications du Windows Store et du Windows Phone Store, assurez-vous que le projet à déboguer est le projet de démarrage. Dans Solution Explore, sélectionnez le projet et choisissez ensuite **Set comme startUp Project** dans le menu contextuelle.

3. Appuyez sur F5.

   ![S’applique à Windows Phone uniquement](../debugger/media/phone-only-content.png "phone_only_content")

   Visual Studio génère et démarre l'application avec le débogueur attaché. L'exécution se poursuit jusqu'à ce qu'un point d'arrêt soit atteint, que vous suspendiez manuellement l'exécution, qu'une exception non gérée se produise ou que l'application se termine. Pour plus d’informations, voir [Quickstart: Debug HTML et CSS](../debugger/quickstart-debug-html-and-css.md).

## <a name="configure-the-debugging-session"></a><a name="BKMK_Configure_the_debugging_session"></a>Configurer la session de débogage
 Comme le script n'est pas compilé, les paramètres de plateforme et de configuration de build ne s'appliquent pas. Si vous débogagez un composant C OU géré, définissez la **Configuration** à **Debug** et choisissez votre plate-forme cible à partir du dialogue **Configuration.**

### <a name="open-the-debugging-property-page-for-the-project"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Ouvrir la page des propriétés de débogage du projet

1. Dans l’Explorateur de solutions, sélectionnez le projet. Dans le menu contextuel, choisissez **Propriétés**.

2. Élargir le nœud **Configuration Properties** et ensuite choisir **Debugging**

### <a name="choose-the-build-configuration-options"></a><a name="BKMK_Choose_the_build_configuration_options"></a> Choisir les options de configuration de build

1. Dans la liste **Configuration** , choisissez **Déboguer** ou **(Debug) active**.

2. Dans la liste **Plateforme** , sélectionnez la plateforme cible à générer. Dans la plupart des cas, **tout processeur** est le meilleur choix.

### <a name="choose-the-deployment-target"></a><a name="BKMK_Choose_the_deployment_target"></a>Choisissez la cible de déploiement
 Vous pouvez déployer et déboguer une application sur l’ordinateur Visual Studio, dans le simulateur Visual Studio sur l’ordinateur local ou sur un périphérique distant. Vous choisissez la cible du **Debugger pour lancer** la liste sur la page **propriété Debugging** pour le projet.

 ![S’applique à Windows uniquement](../debugger/media/windows-only-content.png "windows_only_content")

 Pour une application Windows Store, choisissez l’une de ces options dans la liste des **périphériques Target** :

|||
|-|-|
|**Machine locale**|Déboguez l'application dans la session active sur votre ordinateur local. Voir [les applications Run Windows Store sur la machine locale](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Simulateur**|Déboguez l'application dans le simulateur Visual Studio pour les applications [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] . Le simulateur est une fenêtre du Bureau qui permet de déboguer les fonctionnalités du périphérique, comme les mouvements tactiles et la rotation du périphérique, qui ne sont pas disponibles sur l'ordinateur local. Voir [les applications Run Windows Store dans le simulateur](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Machine à distance**|Déboguez l'application sur un périphérique qui est connecté à l'ordinateur local sur un intranet ou directement connecté via un câble Ethernet. Pour déboguer à distance, les outils de contrôle à distance Visual Studio doivent être installés et en cours d'exécution sur le périphérique distant. Voir [les applications Run Windows Store sur une machine distante](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 Si vous choisissez **Ordinateur distant**, spécifiez le nom ou l'adresse IP de l'ordinateur distant de l'une des manières suivantes :

- Entrez le nom ou l’adresse IP de la machine à distance dans la boîte **De nom de la machine.**

- Choisissez la flèche vers le bas dans la boîte **de nom de machine** et choisissez ** \<Localiser... >**. Ensuite, choisissez la machine à distance de **Select Remote Debugger Connection** boîte de dialogue.

   ![Sélectionner la connexion au Remote Debugger](../debugger/media/vsrun-pro-selectremotedebuggerdlg.png "VSRUN_PRO_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > La boîte de dialogue Sélectionner une connexion du débogueur distant affiche les ordinateurs situés sur le sous-réseau local et les ordinateurs locaux qui sont directement connectés à l'ordinateur Visual Studio via un câble Ethernet. Pour spécifier un autre ordinateur, entrez le nom dans la zone **Nom de l'ordinateur** .

  ![S’applique à Windows Phone uniquement](../debugger/media/phone-only-content.png "phone_only_content")

  Pour une application Windows Store Phone, choisissez **l’appareil** ou l’un des émulateurs de la liste **des périphériques Target.**

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a> Choisir le débogueur à utiliser
 Par défaut, le débogueur s'attache au code JavaScript de votre application. Vous pouvez choisir de déboguer le code natif C++ et le code managé des composants de votre application à la place du code JavaScript. Spécifiez le code à déboguer dans la liste **Type de débogueur** de la page des propriétés de **débogage** du projet d'application.

 Choisissez l’un de ces débbuggeurs de la liste **Debugger Type:**

|||
|-|-|
|**Script uniquement**|Déboguez le code JavaScript dans votre application. Le code managé et le code natif sont ignorés.|
|**Autochtone seulement**|Déboguez le code natif C/C++ dans votre application. Le code managé et le code JavaScript sont ignorés.|
|**Code natif avec script**|Déboguez le code natif C++ et le code JavaScript de votre application.|
|**Managé uniquement**|Déboguez le code managé dans votre application. Le code JavaScript et le code natif C/C++ sont ignorés.|
|**Mixte (natif et managé)**|Déboguez le code natif et managé C/C++ dans votre application. Le code JavaScript est ignoré.|

### <a name="optional-delay-starting-the-app-in-the-debug-session"></a><a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a>(Facultatif) Retarder le démarrage de l’application dans la session de déboçon
 Par défaut, Visual Studio démarre immédiatement l'application lorsque vous démarrez le débogage. Vous pouvez également démarrer une session de débogage et retarder le démarrage de votre application. L'application est lancée dans le débogueur quand elle est elle-même lancée depuis le menu Démarrer ou par un contrat d'activation, ou qu'elle est démarrée au moyen d'une autre procédure ou méthode. Vous pouvez aussi utiliser le démarrage différé pour déboguer les événements en arrière-plan de votre application dont vous voulez qu'ils se produisent alors que l'application n'est pas en cours d'exécution.

 Vous précisez s’il faut retarder le lancement de votre application dans la liste **d’application de lancement** sur la page **propriété Debugging** du projet d’application. Choisissez une de ces options :

- Choisissez **Non** pour retarder le lancement de votre application.

- Choisissez **Oui** pour lancer l’application immédiatement.

### <a name="optional-disable-network-loopbacks"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a>(Facultatif) Désactiver les boucles réseau
 ![S’applique à Windows uniquement](../debugger/media/windows-only-content.png "windows_only_content")

 Pour des raisons de sécurité, une application Windows Store installée en mode standard n'est pas autorisée à effectuer des appels réseau vers le périphérique sur lequel elle est installée. Par défaut, le déploiement Visual Studio crée une exemption à cette règle pour l'application déployée. Cette exemption vous permet de tester les procédures de communication sur un seul ordinateur. Avant d'envoyer votre application au Windows Store, vous devez la tester sans l'exemption.

 Pour supprimer l’exemption de loopback réseau, choisissez **No** parmi la liste **Allow Network Loopback** sur la page **propriété Debugging.**

## <a name="start-the-debugging-session"></a><a name="BKMK_Start_the_debugging_session"></a>Démarrer la session de débogage

### <a name="start-debugging-f5"></a><a name="BKMK_Start_debugging__F5_"></a>Commencez à débogage (F5)
 Lorsque vous choisissez **Start Debugging** sur le menu **Debug** (Clavier: F5), Visual Studio lance l’application avec le débogage ci-joint. L'exécution se poursuit jusqu'à ce qu'un point d'arrêt soit atteint, que vous suspendiez manuellement l'exécution, qu'une exception non gérée se produise ou que l'application se termine.

### <a name="start-debugging-f5-but-delay-the-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Commencez à débogage (F5) mais retardez le démarrage de l’application
 Vous pouvez configurer l'application pour qu'elle s'exécute en mode débogage, mais puisse être démarrée par une autre méthode que le débogueur. Vous pouvez par exemple déboguer le lancement de votre application depuis le menu Démarrer ou déboguer un processus en arrière-plan dans l'application sans la démarrer. Procédez comme suit pour retarder le démarrage de l'application :

1. Sur la page **Debug** des propriétés du projet d’application, choisissez **No** parmi la liste **d’application** de lancement.

2. Choisissez **Start Debugging** sur le menu **Debug** (Clavier: F5).

3. Démarrez votre application dans le menu Démarrer, avec un contrat de exécution ou en suivant une autre procédure.

   L'application démarre en mode débogage. L'exécution se poursuit jusqu'à ce qu'un point d'arrêt soit atteint, que vous suspendiez manuellement l'exécution, qu'une exception non gérée se produise ou que l'application se termine.

   . Pour plus d’informations sur les tâches de fond de débogage, voir [Trigger suspendre, reprendre et les événements de fond pour Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

## <a name="start-an-installed-app-in-the-debugger"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Démarrer une application installée dans le débogueur
 Lorsque vous lancez le débogage en appuyant sur la touche F5, Visual Studio génère et déploie l'application, la configure pour s'exécuter en mode débogage, puis la démarre. Pour démarrer une application déjà installée sur un périphérique, utilisez la boîte de dialogue Déboguer le package d'application déjà installé. Cette procédure est utile lorsque vous devez déboguer une application installée depuis Windows Store, ou lorsque vous disposez des fichiers source de l'application, mais pas de projet Visual Studio pour cette dernière. Par exemple, vous pouvez avoir un système de génération personnalisée qui n'utilise pas les projets ou les solutions Visual Studio.

 Vous pouvez installer l'application sur le périphérique local ou sur un périphérique distant.  Vous pouvez démarrer l'application immédiatement, ou bien la configurer pour s'exécuter dans le débogueur au démarrage de ce dernier par un autre processus ou une autre méthode, depuis le menu Démarrer ou par un contrat d'activation, par exemple. Vous pouvez également configurer l'application pour s'exécuter en mode débogage lorsque vous souhaitez déboguer un processus en arrière-plan sans démarrer l'application. Pour plus d’informations, voir [Trigger suspendre, reprendre et les événements de fond pour Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

 Procédez comme suit pour configurer une application installée pour s'exécuter en mode débogage :

> [!NOTE]
> L'application ne doit pas être en cours d'exécution lorsque vous lancez cette procédure.

1. Dans le menu **Débogage** , choisissez **Déboguer le package d'application installé**

2. Choisissez l'une des options suivantes dans la liste :

   |                    |                                                                                                                                                                                                                                                                                                                                                                                                           |
   |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Machine locale**  |                                                                                                                Déboguez l'application dans la session active sur votre ordinateur local. Voir [les applications Run Windows Store sur la machine locale](../debugger/run-windows-store-apps-on-the-local-machine.md).                                                                                                                 |
   |   **Simulateur**    | Déboguez l'application dans le simulateur Visual Studio pour les applications [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] . Le simulateur est une fenêtre du Bureau qui permet de déboguer les fonctionnalités du périphérique, comme les mouvements tactiles et la rotation du périphérique, qui ne sont pas disponibles sur l'ordinateur local. Voir [les applications Run Windows Store dans le simulateur](../debugger/run-windows-store-apps-in-the-simulator.md). |
   | **Machine à distance** |                          Déboguez l'application sur un périphérique qui est connecté à l'ordinateur local sur un intranet ou directement connecté via un câble Ethernet. Pour déboguer à distance, les outils de contrôle à distance Visual Studio doivent être installés et en cours d'exécution sur le périphérique distant. Voir [les applications Run Windows Store sur une machine distante](../debugger/run-windows-store-apps-on-a-remote-machine.md).                           |

3. Choisissez l'application dans la liste **Packages d'application installés** .

4. Choisissez le moteur de débogage à utiliser dans la liste **Déboguer ce type de code** .

5. (Facultatif). Choisissez **Ne pas lancer, mais déboguer mon code au démarrage** pour déboguer l'application lorsqu'elle est lancée à l'aide d'une autre méthode ou pour déboguer un processus en arrière-plan.

   Lorsque vous cliquez sur **Démarrer**, l'application démarre ou est configurée pour s'exécuter en mode débogage.

## <a name="attach-the-debugger-to-a-running-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Attacher le débogueur à une application en cours de exécution
 Pour attacher le débogueur à une application [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] , vous devez utiliser Debuggable Package Manager pour configurer l'application à exécuter en mode débogage. Debuggable Package Manager est installé avec les outils de contrôle à distance Visual Studio.

 Attacher le débogueur à une application est utile lorsque vous devez déboguer une application déjà installée, telle qu'une application qui a été installée à partir du Windows Store. L'attachement est requis lorsque vous possédez les fichiers sources de l'application, mais que vous n'avez pas de projet Visual Studio pour l'application. Par exemple, vous pouvez avoir un système de génération personnalisée qui n'utilise pas les projets ou les solutions Visual Studio.

 Pour attacher à une application :

1. Configurez l'application pour l'exécuter en mode débogage. Cela doit s'effectuer lorsque l'application n'est pas en cours d'exécution.

2. Démarrez l’application. Vous pouvez démarrer l'application à partir du menu Démarrer, d'un contrat d'exécution ou de toute autre méthode.

3. Attacher le débogueur à l'application en cours d'exécution.

### <a name="set-the-app-to-run-in-debug-mode"></a><a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> Configurer l'application pour l'exécuter en mode débogage

1. Installez les outils de contrôle à distance Visual Studio sur le périphérique où l'application est installée. Voir [Installer les outils à distance](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2. Sur le menu Démarrer, recherchez `Debuggable Package Manager`, puis démarrez-le.

     Une fenêtre PowerShell correctement configurée pour l'applet de commande AppxDebug s'affiche.

3. Pour activer le débogage d'une application, vous devez spécifier l'identificateur PackageFullName de l'application. Pour afficher une liste de toutes les applications qui incluent PackageFullName, entrez `Get-AppxPackage` à l'invite de PowerShell.

4. À l'invite de PowerShell, entrez `Enable-AppxDebug` *PackageFullName* , où *PackageFullName* est l'identificateur PackageFullName de l'application.

### <a name="attach-the-debugger"></a><a name="BKMK_Attach_the_debugger"></a>Attachez le débbuggeur

> [!TIP]
> Les applications JavaScript s'exécutent dans une instance du processus wwahost.exe. Si d'autres applications JavaScript sont en cours d'exécution pendant l'attachement à l'application, vous devez connaître l'identifiant de processus (PID) numérique du processus wwahost.exe dans lequel l'application s'exécute.
>
> La solution la plus simple pour gérer cette situation consiste à fermer toutes les autres applications JavaScript. Sinon, vous pouvez ouvrir le Gestionnaire de tâches Windows avant de démarrer l'application et de noter les identifiants des processus wwahost.exe. Lorsque vous spécifiez le processus à joindre dans la boîte de dialogue **des processus disponibles,** le wwahost.exe de l’application aura un id qui est différent de ceux que vous avez noté.

 Pour attacher le débogueur :

1. Dans le menu **Débogage** , sélectionnez **Attacher au processus**.

    La boîte de dialogue **Attacher au processus** s'affiche.

2. Pour attacher une application sur un périphérique distant, spécifiez le périphérique distant dans la zone **Qualificateur** . Vous pouvez :

   - Entrez le nom dans la zone **Qualificateur** .

   - Choisissez la flèche descendante dans la boîte **de qualification** et choisissez l’appareil parmi une liste d’appareils auxquels vous vous êtes joint auparavant.

   - Choisissez **Trouver** pour choisir l’appareil parmi une liste d’appareils sur votre sous-réseau local.

3. Spécifiez le type de code à déboguer dans la zone **Attacher à** .

    Choisissez **Sélectionner** , puis effectuez l'une des opérations suivantes :

   - Choisissez **Déterminer automatiquement le type de code à déboguer**

   - Choisissez **Déboguer ces types de codes** , puis sélectionnez un ou plusieurs types dans la liste.

4. Dans la liste **des processus disponibles,** choisissez le processus **wwahost.exe** approprié. Utilisez la colonne **Titre** pour identifier votre application.

5. Choisissez **Attacher**.

   Visual Studio attache le débogueur au processus. L'exécution se poursuit jusqu'à ce qu'un point d'arrêt soit atteint, que vous suspendiez manuellement l'exécution, qu'une exception non gérée se produise ou que l'application se termine.

## <a name="see-also"></a> Voir aussi
 [Contrôlez l’exécution dans une session de débog (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) [Quickstart: Debug HTML et CSS](../debugger/quickstart-debug-html-and-css.md) [Trigger suspendre, reprendre et les événements de fond pour Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [Debug applications dans Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
