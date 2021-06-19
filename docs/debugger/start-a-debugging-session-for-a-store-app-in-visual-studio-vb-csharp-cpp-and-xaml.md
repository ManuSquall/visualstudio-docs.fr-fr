---
title: Démarrer une session de débogage pour une application UWP | Microsoft Docs
description: Démarrez une session de débogage Visual Studio pour une application plateforme Windows universelle (UWP). Configurez la session de débogage et choisissez le mode de démarrage de l’application.
ms.custom: SEO-VS-2020
ms.date: 11/20/2018
ms.topic: how-to
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
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: d0669f9838073571018eb762e98aa6d907456f12
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386460"
---
# <a name="start-a-debugging-session-for-a-uwp-app"></a>Commencer une session de débogage pour une application UWP

Cet article explique comment démarrer une session de débogage Visual Studio pour une application plateforme Windows universelle (UWP). Les applications UWP peuvent être écrites en XAML et C++, XAML et C#/Visual Basic. Pour démarrer le débogage d’une application UWP, configurez la session de débogage et choisissez le mode de démarrage de l’application.

::: moniker range=">=vs-2019"
> [!NOTE]
> À compter de Visual Studio 2019, les applications UWP pour HTML et JavaScript ne sont plus prises en charge.
::: moniker-end
::: moniker range="vs-2017"
Dans Visual Studio 2017, la plupart des commandes et options présentées dans cet article s’appliquent également aux applications UWP pour HTML et JavaScript. Lorsque les commandes sont différentes entre les applications managées et C++, les applications JavaScript sont généralement les mêmes que les commandes pour les applications UWP C++.
::: moniker-end

## <a name="start-debugging-from-the-visual-studio-toolbar"></a><a name="BKMK_The_easy_way_to_start_debugging"></a>Démarrer le débogage à partir de la barre d’outils de Visual Studio

Le moyen le plus simple de configurer et de démarrer le débogage consiste à utiliser la barre d’outils standard de Visual Studio.

![Déboguer à partir de la barre d’outils](../debugger/media/vsrun_select_target_device.png)

1. Dans la liste déroulante **configuration** de la barre d’outils **standard** , sélectionnez **Déboguer**.

1. Dans la liste déroulante **plateforme** , sélectionnez la plateforme cible à générer.

1. Dans la liste déroulante en regard de la flèche verte, sélectionnez la cible de débogage. Vous pouvez choisir un ordinateur local, un appareil connecté en direct, un simulateur Visual Studio local, un appareil distant ou un émulateur.

1. Pour démarrer le débogage, sélectionnez la flèche verte **Démarrer** dans la barre d’outils, ou sélectionnez **Déboguer**  >  **Démarrer le débogage**, ou appuyez sur **F5**.

   Visual Studio génère et démarre l'application avec le débogueur attaché.

Le débogage se poursuit jusqu’à ce qu’un point d’arrêt soit atteint, que vous suspendiez manuellement l’exécution, qu’une exception non gérée se produise ou que l’application se termine.

### <a name="deployment-target-options"></a><a name="BKMK_Choose_the_deployment_target"></a> Options de la cible de déploiement

Vous pouvez définir la cible de débogage dans la barre d’outils Visual Studio ou dans la page de propriétés débogage du projet. Sélectionnez l’une des options suivantes :

|Nom|Description|
|-|-|
|**Ordinateur local**|Déboguez l'application dans la session active sur votre ordinateur local.|
|**Simulateur**|Déboguez l’application dans le simulateur Visual Studio pour les applications UWP. Le simulateur est une fenêtre de bureau qui simule les fonctions de l’appareil, telles que les gestes tactiles et la rotation du périphérique, qui peuvent ne pas exister sur l’ordinateur local. L’option de simulateur est disponible uniquement si la **version minimale de la plateforme cible** de votre application est inférieure ou égale au système d’exploitation sur l’ordinateur local. Pour plus d’informations, consultez [exécuter des applications UWP dans le simulateur](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Ordinateur distant**|Déboguez l’application sur un appareil connecté à l’ordinateur local par le biais d’un réseau ou d’un câble Ethernet. Le Outils de contrôle à distance de Visual Studio doit être installé et en cours d’exécution sur le périphérique distant. Pour plus d’informations, consultez [exécuter des applications UWP sur un ordinateur distant](../debugger/run-windows-store-apps-on-a-remote-machine.md).|
|**Appareil**|Déboguez l’application sur un appareil connecté à USB. L’appareil doit être déverrouillé par un développeur et l’écran doit être déverrouillé.|
|**Émulateur mobile**|Démarrez l’émulateur spécifié dans le nom de l’émulateur, déployez l’application et démarrez le débogage. Les émulateurs sont disponibles uniquement sur les ordinateurs activés pour Hyper-V.|

## <a name="configure-debugging-in-the-project-property-page"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Configurer le débogage dans la page de propriétés du projet

Pour configurer des options de débogage supplémentaires, utilisez la page Propriétés de débogage du projet.

**Pour ouvrir les propriétés de débogage :**

1. Dans **Explorateur de solutions**, sélectionnez le projet, puis sélectionnez l’icône **Propriétés** , ou cliquez avec le bouton droit sur le projet et sélectionnez **Propriétés**.

1. Sur le côté gauche du volet **Propriétés** :

   - Pour les applications C# et Visual Basic, sélectionnez **Déboguer**.

     ![Page de propriétés de débogage du projet C# et Visual Basic](../debugger/media/dbg_csvb_debugpropertypage.png)

   - Pour les applications C++, sélectionnez **Configuration Propriétés**  >  **débogage**.

     ![Page de propriétés débogage de l’application UWP C++](../debugger/media/dbg_cpp_debugpropertypage.png)

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a> Choisir le débogueur à utiliser

Pour les applications C# et Visual Basic, Visual Studio débogue le code managé par défaut. Vous pouvez choisir de déboguer d’autres types de code ou d’autres. Vous pouvez également définir des valeurs de **type de débogueur** pour toutes les tâches en arrière-plan qui font partie du projet.

Dans les applications C++, Visual Studio débogue le code natif par défaut. Vous pouvez choisir de déboguer des types de code spécifiques au lieu de ou en plus du code natif.

**Pour spécifier les types de code à déboguer :**

- Pour les applications C# et Visual Basic, sélectionnez l’un des débogueurs suivants dans les listes déroulantes type d' **application** et **type de processus en arrière-plan** sous **type de débogueur** dans la page de propriétés **Déboguer** .

- Pour les applications C++, sélectionnez l’un des débogueurs suivants dans la liste déroulante **type** de débogueur de la page de propriétés **débogage** .

|Nom|Description|
|-|-|
|**Managé uniquement**|Déboguez le code managé dans votre application. Le code JavaScript et le code natif C/C++ sont ignorés.|
|**Natif uniquement**|Déboguez le code natif C/C++ dans votre application. Le code managé et le code JavaScript sont ignorés.|
|**Mixte (natif et managé)**|Déboguez le code natif et managé C/C++ dans votre application. Le code JavaScript est ignoré. Dans les projets C++, cette option est appelée **managé et natif**.|
|**Script**|Déboguez le code JavaScript dans votre application. Le code managé et le code natif sont ignorés.|
|**Code natif avec script**|Déboguez le code natif C/C++ et le code JavaScript dans votre application. Le code managé est ignoré. Disponible uniquement dans les projets C++ ou les tâches en arrière-plan.|
|**GPU uniquement (C++ AMP)**|Déboguez le code C++ natif qui s'exécute sur une unité de traitement graphique (GPU). Disponible uniquement dans les projets C++.|

### <a name="disable-network-loopbacks-optional"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a> Désactiver les bouclages de réseau (facultatif)

 Pour des raisons de sécurité, une application UWP installée de manière standard ne peut pas effectuer d’appels réseau vers l’appareil sur lequel elle est installée. Par défaut, Visual Studio exempte les applications déployées de cette règle, ce qui vous permet de tester les procédures de communication sur un seul ordinateur. Avant de libérer votre application, vous devez la tester sans l’exemption.

**Pour supprimer l'exemption du bouclage de réseau :**

- Pour les applications C# et Visual Basic, désactivez la case à cocher **autoriser le bouclage de réseau local** sous **options de démarrage** dans la page de propriétés **Déboguer** .

- Pour les applications C++, sélectionnez **non** dans la liste déroulante **autoriser le bouclage de réseau local** dans la page de propriétés **débogage** .

### <a name="reinstall-the-app-when-you-start-debugging-optional"></a><a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> Réinstaller l’application lorsque vous démarrez le débogage (facultatif)
 Pour diagnostiquer les problèmes d’installation avec une application C# ou Visual Basic, sélectionnez **désinstaller, puis réinstallez mon package** sur la page de propriétés **Déboguer**  . Cette option recrée l’installation d’origine lorsque vous démarrez le débogage. Cette option n’est pas disponible pour les projets C++.

### <a name="set-authentication-options-for-remote-debugging"></a><a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> Définir les options d’authentification pour le débogage distant

Par défaut, vous devez fournir les informations d’identification Windows pour exécuter le débogueur distant lorsque vous sélectionnez **ordinateur distant** comme cible de déploiement. Vous pouvez modifier l’exigence d’authentification.

Le mode d’authentification **universel (protocole non chiffré)** est destiné aux appareils IOT, Xbox et HoloLens, ainsi qu’à la mise à jour ou aux PC Windows 10 ultérieurs du créateur.

**Pour modifier la méthode d’authentification :**

- Pour les applications C# et Visual Basic, dans la page de propriétés **Déboguer** , sélectionnez **ordinateur distant** comme **appareil cible**. Ensuite, sélectionnez **aucun** ou **protocole universel (protocole non chiffré)** pour le **mode d’authentification**.

- Pour les applications C++, sélectionnez **ordinateur distant** sous **débogueur à lancer** dans la page de propriétés **débogage** . Ensuite, sélectionnez **aucune authentification** ou **protocole universel (non chiffré)** pour le **type d’authentification**.

> [!CAUTION]
> Il n’existe pas de sécurité réseau lorsque vous exécutez le débogueur distant en mode **aucun** ou en mode **universel (protocole non chiffré)** . Choisissez ces modes uniquement sur les réseaux approuvés dont vous êtes sûr qu’ils ne sont pas exposés à un code malveillant ou à un trafic hostile.

## <a name="debugging-start-options"></a><a name="BKMK_Start_the_debugging_session"></a> Options de démarrage du débogage

Lorsque vous sélectionnez **Déboguer**  >  **Démarrer le débogage** ou appuyez sur **F5**, Visual Studio lance l’application avec le débogueur attaché. L'exécution se poursuit jusqu'à ce qu'un point d'arrêt soit atteint, que vous suspendiez manuellement l'exécution, qu'une exception non gérée se produise ou que l'application se termine.

### <a name="start-debugging-but-delay-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Démarrer le débogage mais retarder le démarrage de l’application

Par défaut, Visual Studio démarre immédiatement l’application lorsque vous démarrez le débogage. Vous pouvez également configurer l’application pour qu’elle s’exécute en mode débogage, mais démarrer l’application en dehors du débogueur. Par exemple, vous pouvez déboguer le lancement de l’application à partir du menu **Démarrer** de Windows, ou déboguer un processus en arrière-plan dans l’application. Si vous choisissez cette option, l’application démarre dans le débogueur au lancement.

**Pour désactiver le démarrage automatique de l’application :**

- Pour les applications C# et Visual Basic, sélectionnez **ne pas lancer, mais déboguer mon code au démarrage** sous **options de démarrage** dans la page de propriétés **Déboguer** .

- Pour les applications C++, sélectionnez **non** dans la liste déroulante **lancer l’application** sur la page de propriétés **débogage** .

Pour plus d’informations sur le débogage des tâches en arrière-plan, consultez [déclencher des événements de suspension, de reprise et d’arrière-plan pour les applications UWP](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

### <a name="debug-an-installed-or-running-uwp-app"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Déboguer une application UWP installée ou en cours d’exécution

Vous pouvez utiliser le **package d’application de débogage** pour déboguer une application UWP déjà installée ou en cours d’exécution sur un appareil local ou distant. L’application a peut-être été installée à partir du Microsoft Store ou il ne s’agit peut-être pas d’un projet Visual Studio. Par exemple, l’application peut avoir un système de génération personnalisé qui n’utilise pas Visual Studio.

Vous pouvez démarrer l’application installée immédiatement, ou vous pouvez la configurer pour qu’elle s’exécute dans le débogueur quand elle est démarrée avec une autre méthode. Pour plus d’informations, consultez [déclencher des événements de suspension, de reprise et d’arrière-plan pour les applications UWP](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

Pour démarrer une application UWP installée ou en cours d’exécution dans le débogueur, sélectionnez **Déboguer**  >  **autres cibles de débogage**  >  **déboguer le package d’application installé**. Pour plus d’instructions, consultez [Déboguer un package d’application installé](../debugger/debug-installed-app-package.md).

### <a name="attach-the-debugger-to-a-running-windows-8x-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Attacher le débogueur à une application Windows 8. x en cours d’exécution

Pour attacher le débogueur à une application [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] , vous devez utiliser Debuggable Package Manager pour configurer l'application à exécuter en mode débogage. Le gestionnaire de package pouvant être débogué est installé avec le Outils de contrôle à distance de Visual Studio.

1. Installez le Outils de contrôle à distance de Visual Studio sur l’appareil où l’application est installée. Pour plus d’informations, consultez [installation des outils de contrôle à distance](../debugger/remote-debugging.md).

1. Dans l’écran d' **Accueil** de Windows, recherchez et démarrez le gestionnaire de package pouvant être **débogué**.

   Une fenêtre PowerShell correctement configurée pour l'applet de commande AppxDebug s'affiche.

1. Spécifiez l’identificateur PackageFullName de l’application.

   1. Pour afficher une liste incluant le PackageFullName de toutes les applications, tapez `Get-AppxPackage` à l’invite de PowerShell.

   1. À l’invite PowerShell, entrez `Enable-AppxDebug <PackageFullName>` , où \<PackageFullName> est l’identificateur PackageFullName de l’application.

1. Sélectionnez **Déboguer**  >  **attacher au processus**.

1. Dans la boîte de dialogue **attacher au processus** , spécifiez le périphérique distant dans la zone cible de la **connexion** .

   Vous pouvez entrer le nom de l’appareil, le sélectionner dans la liste déroulante de la zone cible de la **connexion** ou sélectionner **Rechercher** pour trouver l’appareil dans la boîte de dialogue **connexions à distance** .

1. Pour spécifier le type de code que vous souhaitez déboguer, en regard de la zone **attacher à** , sélectionnez **Sélectionner**.

1. Dans la boîte de dialogue **Sélectionner le type de code** , sélectionnez l’une des deux opérations suivantes :
   - **Déterminer automatiquement le type de code à déboguer**, ou
   - **Déboguez ces types de code**, puis sélectionnez un ou plusieurs types de code dans la liste.

1. Dans la liste **processus disponibles**  , sélectionnez le processus d’application à déboguer.

1. Sélectionnez **Attacher**.

 Visual Studio attache le débogueur au processus. L'exécution se poursuit jusqu'à ce qu'un point d'arrêt soit atteint, que vous suspendiez manuellement l'exécution, qu'une exception non gérée se produise ou que l'application se termine.

::: moniker range="vs-2017"
> [!NOTE]
> Les applications JavaScript s’exécutent dans une instance du processus de *wwahost.exe* . Si plusieurs applications JavaScript sont en cours d’exécution, vous devez connaître l’ID de processus numérique (PID) du processus de *wwahost.exe* de votre application pour l’attacher.
>
> Le moyen le plus simple de s’attacher à votre application JavaScript consiste à fermer toutes les autres applications JavaScript. Ou bien, vous pouvez noter les PID de l’exécution des processus *wwahost.exe* dans le gestionnaire des tâches de Windows avant de démarrer votre application. Quand vous démarrez votre application, son *wwahost.exe* PID est celle qui est différente de celle que vous avez notée précédemment.
::: moniker-end

## <a name="see-also"></a>Voir aussi

- [Déboguer des applications dans Visual Studio](../debugger/debugging-windows-store-and-windows-universal-apps.md)