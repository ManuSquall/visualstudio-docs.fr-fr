---
title: Démarrer une session de débogage pour les applications du Windows Store (JavaScript) | Microsoft Docs
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78406347"
---
# <a name="start-a-debugging-session-for-store-apps-in-visual-studio-javascript"></a>Démarrer une session de débogage dans Visual Studio (JavaScript) pour des applications du Windows Store
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

S’applique à Windows et Windows Phone] (.. /Image/windows_and_phone_content. png « windows_and_phone_content »)

 Cette rubrique explique comment démarrer une session de débogage pour les applications du Windows Store écrites en JavaScript et HTML5. Vous pouvez démarrer le débogage avec une seule séquence de touches ou configurer la session de débogage pour des scénarios spécifiques, puis choisir de quelle façon démarrer l'application.

> [!NOTE]
> Pour les applications écrites en XAML et C#visuel, C++visuel ou Visual Basic, consultez [Démarrer une session de débogage ( C#VB C++ , et XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

## <a name="BKMK_In_this_topic"></a> Dans cette rubrique
 [Dans cette rubrique](#BKMK_In_this_topic)

 [La méthode simple pour démarrer le débogage](#BKMK_The_easy_way_to_start_debugging)

 [Configurer la session de débogage](#BKMK_Configure_the_debugging_session)

- [Ouvrir la page des propriétés de débogage du projet](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Choisir les options de configuration de build](#BKMK_Choose_the_build_configuration_options)

- [Sélectionner la cible de déploiement](#BKMK_Choose_the_deployment_target)

- [Choisir le débogueur à utiliser](#BKMK_Choose_the_debugger_to_use)

- [Facultatif Retarder le démarrage de l’application dans la session de débogage](#BKMK__Optional__Delay_starting_app_in_the_debug_session)

- [Désactiver les bouclages de réseau (facultatif)](#BKMK__Optional__Disable_network_loopbacks)

  [Démarrer la session de débogage](#BKMK_Start_the_debugging_session)

- [Démarrer le débogage (F5)](#BKMK_Start_debugging__F5_)

- [Démarrer le débogage (F5), mais différer le démarrage de l'application](#BKMK_Start_debugging__F5__but_delay_the_app_start)

  [Démarrer une application installée dans le débogueur](#BKMK_Start_an_installed_app_in_the_debugger)

  [Attacher le débogueur à une application en cours de exécution](#BKMK_Attach_the_debugger_to_a_running_app_)

- [Configurer l'application pour l'exécuter en mode débogage](#BKMK_Set_the_app_to_run_in_debug_mode)

- [Attacher le débogueur](#BKMK_Attach_the_debugger)

## <a name="BKMK_The_easy_way_to_start_debugging"></a> La méthode simple pour démarrer le débogage
 ![S’applique uniquement à Windows](../debugger/media/windows-only-content.png "windows_only_content")

1. Ouvrez la solution d'application dans Visual Studio.

2. Si la solution contient des projets pour les applications du Windows Store et du Windows Phone Store, assurez-vous que le projet à déboguer est le projet de démarrage. Dans l’Explorateur de solutions, sélectionnez le projet, puis choisissez **définir comme projet de démarrage** dans le menu contextuel.

3. Appuyez sur F5.

   ![S’applique à Windows Phone uniquement](../debugger/media/phone-only-content.png "phone_only_content")

   Visual Studio génère et démarre l'application avec le débogueur attaché. L'exécution se poursuit jusqu'à ce qu'un point d'arrêt soit atteint, que vous suspendiez manuellement l'exécution, qu'une exception non gérée se produise ou que l'application se termine. Pour plus d’informations, consultez [démarrage rapide : déboguer du code HTML et CSS](../debugger/quickstart-debug-html-and-css.md).

## <a name="BKMK_Configure_the_debugging_session"></a> Configurer la session de débogage
 Comme le script n'est pas compilé, les paramètres de plateforme et de configuration de build ne s'appliquent pas. Si vous déboguez un ou C++ un composant managé, définissez la **configuration** sur **Déboguer** et choisissez votre plateforme cible dans la boîte de dialogue de **configuration** .

### <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Ouvrir la page des propriétés de débogage du projet

1. Dans l’Explorateur de solutions, sélectionnez le projet. Dans le menu contextuel, choisissez **Propriétés**.

2. Développez le nœud **Propriétés de configuration** , puis choisissez **débogage** .

### <a name="BKMK_Choose_the_build_configuration_options"></a> Choisir les options de configuration de build

1. Dans la liste **Configuration** , choisissez **Déboguer** ou **(Debug) active**.

2. Dans la liste **Plateforme** , sélectionnez la plateforme cible à générer. Dans la plupart des cas, **Any CPU** est le meilleur choix.

### <a name="BKMK_Choose_the_deployment_target"></a> Sélectionner la cible de déploiement
 Vous pouvez déployer et déboguer une application sur l'ordinateur Visual Studio, dans le simulateur Visual Studio sur l'ordinateur local ou sur un appareil distant. Vous choisissez la cible dans la liste **débogueur à lancer** de la page de propriétés **débogage** du projet.

 ![S’applique uniquement à Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Pour une application du Windows Store, choisissez l’une des options suivantes dans la liste des **appareils cibles** :

|||
|-|-|
|**Ordinateur local**|Déboguez l'application dans la session active sur votre ordinateur local. Consultez [exécuter des applications du Windows Store sur l’ordinateur local](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Simulateur**|Déboguez l'application dans le simulateur Visual Studio pour les applications [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] . Le simulateur est une fenêtre du Bureau qui permet de déboguer les fonctionnalités du périphérique, comme les mouvements tactiles et la rotation du périphérique, qui ne sont pas disponibles sur l'ordinateur local. Consultez [exécuter des applications du Windows Store dans le simulateur](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Ordinateur distant**|Déboguez l'application sur un appareil connecté à l'ordinateur local sur un intranet ou directement connecté via un câble Ethernet. Pour déboguer à distance, les outils de contrôle à distance Visual Studio doivent être installés et en cours d'exécution sur le périphérique distant. Consultez [exécuter des applications du Windows Store sur un ordinateur distant](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 Si vous choisissez **Ordinateur distant**, spécifiez le nom ou l'adresse IP de l'ordinateur distant de l'une des manières suivantes :

- Entrez le nom ou l’adresse IP de l’ordinateur distant dans la zone nom de l' **ordinateur** .

- Choisissez la flèche bas dans la zone nom de l' **ordinateur** , puis choisissez **\<localiser... >** . Choisissez ensuite la machine distante à partir de la boîte de dialogue **Sélectionner une connexion du débogueur distant** .

   ![Sélectionner une connexion du débogueur distant](../debugger/media/vsrun-pro-selectremotedebuggerdlg.png "VSRUN_PRO_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > La boîte de dialogue Sélectionner une connexion du débogueur distant affiche les ordinateurs situés sur le sous-réseau et les ordinateurs locaux qui sont directement connectés à l'ordinateur Visual Studio via un câble Ethernet. Pour spécifier un autre ordinateur, entrez le nom dans la zone **Nom de l'ordinateur** .

  ![S’applique à Windows Phone uniquement](../debugger/media/phone-only-content.png "phone_only_content")

  Pour une application de téléphone du Windows Store, choisissez **périphérique** ou l’un des émulateurs de la liste **périphérique cible** .

### <a name="BKMK_Choose_the_debugger_to_use"></a> Choisir le débogueur à utiliser
 Par défaut, le débogueur s'attache au code JavaScript de votre application. Vous pouvez choisir de déboguer le code natif C++ et le code managé des composants de votre application à la place du code JavaScript. Spécifiez le code à déboguer dans la liste **Type de débogueur** de la page des propriétés de **débogage** du projet d'application.

 Choisissez l’un de ces débogueurs dans la liste **type de débogueur** :

|||
|-|-|
|**Script uniquement**|Déboguez le code JavaScript dans votre application. Le code managé et le code natif sont ignorés.|
|**Natif uniquement**|Déboguez le code natif C/C++ dans votre application. Le code managé et le code JavaScript sont ignorés.|
|**Code natif avec script**|Déboguez le code natif C++ et le code JavaScript dans votre application.|
|**Managé uniquement**|Déboguez le code managé dans votre application. Le code JavaScript et le code natif C/C++ sont ignorés.|
|**Mixte (natif et managé)**|Déboguez le code natif et managé C/C++ dans votre application. Le code JavaScript est ignoré.|

### <a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a>Facultatif Retarder le démarrage de l’application dans la session de débogage
 Par défaut, Visual Studio démarre immédiatement l'application lorsque vous démarrez le débogage. Vous pouvez également démarrer une session de débogage et retarder le démarrage de votre application. L'application est lancée dans le débogueur quand elle est elle-même lancée depuis le menu Démarrer ou par un contrat d'activation, ou qu'elle est démarrée au moyen d'une autre procédure ou méthode. Vous pouvez aussi utiliser le démarrage différé pour déboguer les événements en arrière-plan de votre application dont vous voulez qu'ils se produisent alors que l'application n'est pas en cours d'exécution.

 Vous spécifiez s’il faut retarder le lancement de votre application dans la liste **lancer l’application** de la page de propriétés **débogage** du projet d’application. Choisissez une de ces options :

- Choisissez **non** pour différer le lancement de votre application.

- Choisissez **Oui** pour lancer l’application immédiatement.

### <a name="BKMK__Optional__Disable_network_loopbacks"></a> Désactiver les bouclages de réseau (facultatif)
 ![S’applique uniquement à Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Pour des raisons de sécurité, une application du Windows Store installée en mode standard n'est pas autorisée à effectuer des appels réseau vers l'appareil sur lequel elle est installée. Par défaut, le déploiement Visual Studio crée une exemption à cette règle pour l'application déployée. Cette exemption vous permet de tester les procédures de communication sur un seul ordinateur. Avant d'envoyer votre application au Windows Store, vous devez la tester sans l'exemption.

 Pour supprimer l’exemption de bouclage réseau, choisissez **non** dans la liste **autoriser le bouclage réseau** sur la page de propriétés **débogage** .

## <a name="BKMK_Start_the_debugging_session"></a> Démarrer la session de débogage

### <a name="BKMK_Start_debugging__F5_"></a> Démarrer le débogage (F5)
 Quand vous choisissez **Démarrer le débogage** dans le menu **Déboguer** (clavier : F5), Visual Studio lance l’application avec le débogueur attaché. L'exécution se poursuit jusqu'à ce qu'un point d'arrêt soit atteint, que vous suspendiez manuellement l'exécution, qu'une exception non gérée se produise ou que l'application se termine.

### <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Démarrer le débogage (F5), mais différer le démarrage de l'application
 Vous pouvez configurer l'application pour qu'elle s'exécute en mode débogage, mais puisse être démarrée par une autre méthode que le débogueur. Vous pouvez par exemple déboguer le lancement de votre application depuis le menu Démarrer ou déboguer un processus en arrière-plan dans l'application sans la démarrer. Pour retarder le démarrage de l'application, procédez comme suit :

1. Sur la page **Déboguer** des propriétés du projet d’application, choisissez **non** dans la liste **lancer l’application** .

2. Choisissez **Démarrer le débogage** dans le menu **Déboguer** (clavier : F5).

3. Démarrez votre application à partir du menu Démarrer, avec un contrat d'exécution ou en suivant une autre procédure.

   L'application démarre en mode débogage. L'exécution se poursuit jusqu'à ce qu'un point d'arrêt soit atteint, que vous suspendiez manuellement l'exécution, qu'une exception non gérée se produise ou que l'application se termine.

   . Pour plus d’informations sur le débogage des tâches en arrière-plan, consultez [déclencher des événements de suspension, de reprise et d’arrière-plan pour le Windows Store](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

## <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Démarrer une application installée dans le débogueur
 Quand vous lancez le débogage en appuyant sur la touche F5, Visual Studio génère et déploie l'application, la configure pour s'exécuter en mode débogage, puis la démarre. Pour démarrer une application déjà installée sur un périphérique, utilisez la boîte de dialogue Déboguer le package d'application déjà installé. Cette procédure est utile lorsque vous devez déboguer une application installée depuis Windows Store, ou lorsque vous disposez des fichiers source de l'application, mais pas de projet Visual Studio pour cette dernière. Par exemple, vous pouvez avoir un système de génération personnalisée qui n'utilise pas les projets ou les solutions Visual Studio.

 Vous pouvez installer l'application sur le périphérique local ou sur un périphérique distant.  Vous pouvez démarrer l'application immédiatement, ou bien la configurer pour s'exécuter dans le débogueur au démarrage de ce dernier par un autre processus ou une autre méthode, depuis le menu Démarrer ou par un contrat d'activation, par exemple. Vous pouvez également configurer l'application pour s'exécuter en mode débogage lorsque vous souhaitez déboguer un processus en arrière-plan sans démarrer l'application. Pour plus d’informations, consultez [déclencher des événements de suspension, de reprise et d’arrière-plan pour le Windows Store](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

 Procédez comme suit pour configurer une application installée pour s'exécuter en mode débogage :

> [!NOTE]
> L'application ne doit pas être en cours d'exécution quand vous lancez cette procédure.

1. Dans le menu **Débogage** , choisissez **Déboguer le package d'application installé**

2. Choisissez l'une des options suivantes dans la liste :

   |                    |                                                                                                                                                                                                                                                                                                                                                                                                           |
   |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Ordinateur local**  |                                                                                                                Déboguez l'application dans la session active sur votre ordinateur local. Consultez [exécuter des applications du Windows Store sur l’ordinateur local](../debugger/run-windows-store-apps-on-the-local-machine.md).                                                                                                                 |
   |   **Simulateur**    | Déboguez l'application dans le simulateur Visual Studio pour les applications [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] . Le simulateur est une fenêtre du Bureau qui permet de déboguer les fonctionnalités du périphérique, comme les mouvements tactiles et la rotation du périphérique, qui ne sont pas disponibles sur l'ordinateur local. Consultez [exécuter des applications du Windows Store dans le simulateur](../debugger/run-windows-store-apps-in-the-simulator.md). |
   | **Ordinateur distant** |                          Déboguez l'application sur un appareil connecté à l'ordinateur local sur un intranet ou directement connecté via un câble Ethernet. Pour déboguer à distance, les outils de contrôle à distance Visual Studio doivent être installés et en cours d'exécution sur le périphérique distant. Consultez [exécuter des applications du Windows Store sur un ordinateur distant](../debugger/run-windows-store-apps-on-a-remote-machine.md).                           |

3. Choisissez l'application dans la liste **Packages d'application installés** .

4. Choisissez le moteur de débogage à utiliser dans la liste **Déboguer ce type de code** .

5. (Facultatif). Choisissez **Ne pas lancer, mais déboguer mon code au démarrage** pour déboguer l'application lorsqu'elle est lancée à l'aide d'une autre méthode ou pour déboguer un processus en arrière-plan.

   Lorsque vous cliquez sur **Démarrer**, l'application démarre ou est configurée pour s'exécuter en mode débogage.

## <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Attacher le débogueur à une application en cours de exécution
 Pour attacher le débogueur à une application [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] , vous devez utiliser Debuggable Package Manager pour configurer l'application à exécuter en mode débogage. Debuggable Package Manager est installé avec les outils de contrôle à distance Visual Studio.

 Attacher le débogueur à une application est utile lorsque vous devez déboguer une application déjà installée, telle qu'une application qui a été installée à partir du Windows Store. L'attachement est requis lorsque vous possédez les fichiers sources de l'application, mais que vous n'avez pas de projet Visual Studio pour l'application. Par exemple, vous pouvez avoir un système de génération personnalisée qui n'utilise pas les projets ou les solutions Visual Studio.

 Pour attacher à une application

1. Configurez l'application pour l'exécuter en mode débogage Vous devez effectuer cette opération quand l'application n'est pas en cours d'exécution.

2. Démarrez l’application. Vous pouvez démarrer l'application à partir du menu Démarrer, d'un contrat d'exécution ou de toute autre méthode.

3. Attacher le débogueur à l'application en cours d'exécution.

### <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> Configurer l'application pour l'exécuter en mode débogage

1. Installez les outils de contrôle à distance Visual Studio sur l'appareil où l'application est installée. Consultez [installation des outils de contrôle à distance](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2. Sur le menu Démarrer, recherchez `Debuggable Package Manager`, puis démarrez-le.

     Une fenêtre PowerShell correctement configurée pour l'applet de commande AppxDebug s'affiche.

3. Pour activer le débogage d'une application, vous devez spécifier l'identificateur PackageFullName de l'application. Pour afficher une liste de toutes les applications qui incluent PackageFullName, entrez `Get-AppxPackage` à l'invite de PowerShell.

4. À l’invite PowerShell, entrez `Enable-AppxDebug` *PackageFullName* où *PackageFullName* est l’identificateur PackageFullName de l’application.

### <a name="BKMK_Attach_the_debugger"></a> Attacher le débogueur

> [!TIP]
> Les applications JavaScript s'exécutent dans une instance du processus wwahost.exe. Si d'autres applications JavaScript sont en cours d'exécution pendant l'attachement à l'application, vous devez connaître l'identifiant de processus (PID) numérique du processus wwahost.exe dans lequel l'application s'exécute.
>
> La solution la plus simple pour gérer cette situation consiste à fermer toutes les autres applications JavaScript. Sinon, vous pouvez ouvrir le Gestionnaire de tâches Windows avant de démarrer l'application et de noter les identifiants des processus wwahost.exe. Lorsque vous spécifiez le processus à attacher dans la boîte de dialogue **processus disponibles** , processus wwahost. exe de l’application aura un ID différent de ceux que vous avez notés.

 Pour attacher le débogueur

1. Dans le menu **Débogage** , sélectionnez **Attacher au processus**.

    La boîte de dialogue **Attacher au processus** s'affiche.

2. Pour attacher une application sur un périphérique distant, spécifiez le périphérique distant dans la zone **Qualificateur** . Vous pouvez :

   - Entrez le nom dans la zone **Qualificateur** .

   - Choisissez la flèche vers le bas dans la zone **qualificateur** , puis choisissez l’appareil dans la liste des appareils que vous avez attachés précédemment.

   - Choisissez **Rechercher** pour choisir l’appareil dans une liste de périphériques sur votre sous-réseau local.

3. Spécifiez le type de code à déboguer dans la zone **Attacher à** .

    Choisissez **Sélectionner** , puis effectuez l'une des opérations suivantes :

   - Choisissez **Déterminer automatiquement le type de code à déboguer**

   - Choisissez **Déboguer ces types de codes** , puis sélectionnez un ou plusieurs types dans la liste.

4. Dans la liste **processus disponibles** , choisissez le processus **processus wwahost. exe** approprié. Utilisez la colonne **titre** pour identifier votre application.

5. Choisissez **Attacher**.

   Visual Studio attache le débogueur au processus. L'exécution se poursuit jusqu'à ce qu'un point d'arrêt soit atteint, que vous suspendiez manuellement l'exécution, qu'une exception non gérée se produise ou que l'application se termine.

## <a name="see-also"></a>Voir aussi
 [Contrôle de l’exécution dans un guide de démarrage rapide de session de débogage (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) [: déboguer](../debugger/quickstart-debug-html-and-css.md) des [événements de fermeture, de reprise et d’arrière-plan de déclencheur html et CSS pour les](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [applications de débogage Windows Store dans Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
