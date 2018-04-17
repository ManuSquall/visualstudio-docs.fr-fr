---
title: Déboguer un package d’application installée (UWP) | Documents Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 07/17/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.remote.connection
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- app package, debug
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 9c1406637b6d1dce312b0574cfba3c9a4f7356e8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="debug-an-installed-app-package-in-visual-studio-uwp"></a>Déboguer un package d’application installée dans Visual Studio (UWP)

Vous pouvez déboguer n’importe quel package d’application installée en cliquant sur **Déboguer > autres cibles de débogage > déboguer le Package d’application installé**. Cette méthode de débogage est disponible pour les applications Windows universelle (UWP) sur ces appareils :

* Windows 10 (non pris en charge sur les téléphones)
* XBox
* HoloLens
* IoT

Pour plus d’informations sur ces fonctionnalités, voir le blog sur les mises à jour pour [débogage installé les packages d’application](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/30/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) et la publication sur [création d’applications Windows universelle (UWP)](https://blogs.msdn.microsoft.com/visualstudio/2016/08/02/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-app-package-or-running-app-on-a-local-machine-or-device"></a>Déboguer un Package d’application installé ou l’application en cours d’exécution sur un ordinateur Local ou un périphérique

1. Votre projet UWP ouvert dans Visual Studio, cliquez sur **Déboguer > autres cibles de débogage > déboguer le Package d’application installé**.

2. Sélectionnez **ordinateur Local** ou **périphérique**.

     Si vous choisissez **périphérique**, votre ordinateur doit être connecté physiquement à un appareil Windows 10.

     ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

     En cours d’exécution installé application packages qui s’affichent sous la **en cours d’exécution** nœud. Installation des packages d’application qui ne sont pas en cours d’exécution afficher des sous **pas en cours d’exécution**.

3. Sélectionnez le nom de l’application que vous souhaitez déboguer sous **en cours d’exécution** ou **pas en cours d’exécution** et choisissez **Démarrer** ou, si l’application est déjà en cours d’exécution, choisissez **Attach**.

     Si vous sélectionnez **ne pas lancer, mais déboguer mon code au démarrage**, cela entraîne le débogueur Visual Studio attacher à votre application lorsque vous l’ouvrez à la fois personnalisé. Il s’agit d’un moyen efficace pour déboguer des chemins d’accès de contrôle à partir de [lancement différentes méthodes](/windows/uwp/xbox-apps/automate-launching-uwp-apps), par exemple, activation du protocole avec des paramètres personnalisés.

> [!NOTE]
> Visual Studio peut également joindre tout processus d’application UWP en cours d’exécution en sélectionnant **déboguer**, puis **attacher au processus**. Attachement à un processus en cours d’exécution ne nécessite pas le projet Visual Studio d’origine, mais le chargement de symboles du processus sera une aide précieuse lors du débogage d’un processus que vous n’avez pas le code d’origine.
  
## <a name="remote"></a> Déboguer une application installée ou en cours d’exécution sur un ordinateur distant 

Lorsque vous déboguez un package d’application installée sur un ordinateur distant pour la première fois, Visual Studio installe la version appropriée des outils à distance pour votre périphérique cible. Votre périphérique cible doit être un ordinateur Windows 10, le périphérique XBox, HoloLens et IoT.

1. Sur votre appareil Windows 10, activez [mode développeur](/windows/uwp/get-started/enable-your-device-for-development).

2. Si vous vous connectez à un ordinateur distant équipés pre-l’auteur de la mise à jour de Windows 10, tout d’abord manuellement [installer et démarrer le débogueur distant](../debugger/remote-debugging.md).

     Pour un appareil XBox, HoloLens et IoT, appareils et Windows en cours d’exécution mise à jour du créateur de Windows 10, vous n’avez pas besoin d’installer manuellement le débogueur distant. Les outils à distance seront automatiquement installés lorsque vous déployez l’application.

3. Cliquez sur **Déboguer > autres cibles de débogage > débogage de Package d’application installé**.

4. Dans la première liste déroulante, choisissez **ordinateur distant**.

5. Tapez le nom ou l’adresse IP de l’ordinateur que vous voulez attacher.

     ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

     Si vous ne pouvez pas attacher à l’aide du nom de l’ordinateur (une fois que vous choisissez **Démarrer**), utilisez l’adresse IP à la place. Utilisez l’adresse IP pour les appareils IoT, HoloLens ou XBox.

5. Choisissez le mode d’authentification en sélectionnant une option dans **Mode d’authentification**.

    Pour la plupart des applications, conservez la valeur par défaut, **universel (protocole non chiffré)**.

6. Sélectionnez le nom de l’application que vous souhaitez déboguer sous **en cours d’exécution** ou **pas en cours d’exécution** et choisissez **Démarrer** ou (pour les applications en cours d’exécution) **attacher**.

     Si vous sélectionnez **ne pas lancer, mais déboguer mon code au démarrage**, cela entraîne le débogueur Visual Studio attacher à votre package d’application lorsque vous l’ouvrez à la fois personnalisé. Il s’agit d’un moyen efficace pour déboguer des chemins d’accès de contrôle à partir de [lancement différentes méthodes](/windows/uwp/xbox-apps/automate-launching-uwp-apps), par exemple, activation du protocole avec des paramètres personnalisés.

     Lorsque vous déboguez un package d’application installée sur un appareil XBox, HoloLens et IoT connecté pour la première fois, Visual Studio installe la version correcte du débogueur distant pour votre périphérique cible. Cette opération peut prendre un peu de temps et vous verrez un message ``Starting remote debugger`` alors que cela se produit.

     > [!NOTE]
> À présent, une console XBox ou HoloLens appareil va redémarrer l’application avec le débogueur attaché si elle est déjà en cours d’exécution.

Pour plus d’informations sur les options avancées pour le déploiement distant des applications UWP, consultez [déploiement et débogage des applications UWP](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps.md#advanced-remote-deployment-options). 
  
## <a name="see-also"></a>Voir aussi  
 [Débogage dans Visual Studio](../debugger/index.md)  
 [Visite guidée des fonctionnalités du débogueur](../debugger/debugger-feature-tour.md)  
 [Débogage à distance](../debugger/remote-debugging.md)  
 [Configurer le Pare-feu Windows pour le débogage distant](../debugger/configure-the-windows-firewall-for-remote-debugging.md)  
 [Affectations de port du débogueur distant](../debugger/remote-debugger-port-assignments.md)  
 [Erreurs et résolution des problèmes du débogage distant](../debugger/remote-debugging-errors-and-troubleshooting.md)