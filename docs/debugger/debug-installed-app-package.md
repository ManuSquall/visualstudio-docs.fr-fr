---
title: Déboguer un package d’application UWP installé | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 11/07/2018
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
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 7fc90c6ecb17a8c794561b975fb8e0be9f6501af
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936214"
---
# <a name="debug-an-installed-uwp-app-package-in-visual-studio"></a>Déboguer un package d’application UWP installé dans Visual Studio

Visual Studio peut déboguer des packages d’application Universal Windows Platform (UWP) installés sur les ordinateurs Windows 10 et appareils Xbox, HoloLens et IoT. 

>[!NOTE]
>Pour les applications UWP installées de débogage Visual Studio n’est pas pris en charge sur les téléphones.
   
Pour plus d’informations sur le débogage des applications UWP, consultez les billets de blog sur [débogage installé des packages d’application](https://blogs.msdn.microsoft.com/devops/2016/03/30/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) et [création d’applications de Windows universelle (UWP)](https://blogs.msdn.microsoft.com/visualstudio/2016/08/02/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-uwp-app-on-a-local-machine"></a>Déboguer une application UWP installée sur un ordinateur local

1. Dans Visual Studio, sélectionnez **déboguer** > **autres cibles de débogage** > **déboguer le Package d’application installé**.
   
1. Dans le **déboguer le Package d’application installé** boîte de dialogue, sous **Type de connexion**, sélectionnez **ordinateur Local**.
   
1. Sous **Packages d’application installés**, sélectionnez l’application que vous souhaitez déboguer, ou tapez son nom dans la zone de recherche. Packages d’applications installés non-en cours d’exécution s’affichent sous **ne pas en cours d’exécution**, et les applications en cours d’exécution sont sous **en cours d’exécution**. 
   
   ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")
   
1. Si nécessaire, modifiez le type de code sous **déboguer ce type de code**, puis sélectionnez les autres options. 
   - Sélectionnez **ne pas lancer, mais déboguer mon code au démarrage** pour démarrer le débogage lorsque l’application démarre. Démarrage du débogage lorsque l’application démarre est un moyen efficace pour déboguer les chemins d’accès de contrôle à partir de [lancement différentes méthodes](/windows/uwp/xbox-apps/automate-launching-uwp-apps), telles que l’activation du protocole avec des paramètres personnalisés.
   
1. Sélectionnez **Démarrer**, ou si l’application est en cours d’exécution, sélectionnez **attacher**.

> [!NOTE]
> Vous pouvez également attacher à n’importe quel UWP en cours d’exécution ou d’autres processus de l’application en sélectionnant **déboguer** > **attacher au processus** dans Visual Studio. Vous n’avez pas besoin du projet d’origine de Visual Studio pour attacher à un processus en cours d’exécution, mais le chargement de symboles de l’application sera d’une aide précieuse lors du débogage d’un processus que vous n’avez pas le code d’origine. Consultez [spécifier les symboles et les fichiers sources dans le débogueur](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  
## <a name="remote"></a> Déboguer une application UWP installée sur un ordinateur distant ou un appareil

La première fois que Visual Studio débogue une application UWP installée sur un appareil Windows 10 ou d’un à distance-créateur de la publication mise à jour Windows 10, il installe les outils de débogage à distance sur l’appareil cible. 

1. [Activer le mode développeur](/windows/uwp/get-started/enable-your-device-for-development) sur l’ordinateur Visual Studio et l’appareil distant ou l’ordinateur.
   
1. Si vous vous connectez à un ordinateur distant exécutant mise à jour Windows 10 pre-l’auteur de la, [manuellement installer et démarrer le débogueur distant](../debugger/remote-debugging.md) sur l’ordinateur distant.
   
1. Sur l’ordinateur Visual Studio, sélectionnez **déboguer** > **autres cibles de débogage** > **déboguer le Package d’application installé**.
   
1. Dans le **déboguer le Package d’application installé** boîte de dialogue, sous **Type de connexion**, sélectionnez **Machine distante** ou **appareil**.
   
   Si vous sélectionnez **appareil**, votre ordinateur doit être connecté physiquement à un appareil Windows 10.
   
   Pour un ordinateur distant, si l’adresse de l’ordinateur ne s’affiche à côté **adresse**, sélectionnez **modification**. 
      
   1. Dans le **connexion à distance** boîte de dialogue, ensuite **adresse**, tapez le nom ou l’adresse IP de l’ordinateur que vous souhaitez vous connecter.
      
      ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")
      
      Si le débogueur ne peut pas se connecter à un ordinateur distant en utilisant le nom de l’ordinateur, utilisez l’adresse IP à la place. Utilisez l’adresse IP pour les appareils Xbox, HoloLens ou IoT.
   1. Sélectionnez une option d’authentification **Mode d’authentification**.
      
      Pour la plupart des applications, conservez la valeur par défaut, **universel (protocole non chiffré)**.
   1. Sélectionnez **sélectionnez**. 

1. Sous **Packages d’application installés**, sélectionnez l’application que vous souhaitez déboguer, ou tapez son nom dans la zone de recherche. Packages d’applications installés non-en cours d’exécution s’affichent sous **ne pas en cours d’exécution**, et les applications en cours d’exécution sont sous **en cours d’exécution**. 
   
1. Si nécessaire, modifiez le type de code sous **déboguer ce type de code**, puis sélectionnez les autres options. 
   - Sélectionnez **ne pas lancer, mais déboguer mon code au démarrage** pour démarrer le débogage lorsque l’application démarre. Démarrage du débogage lorsque l’application démarre est un moyen efficace pour déboguer les chemins d’accès de contrôle à partir de [lancement différentes méthodes](/windows/uwp/xbox-apps/automate-launching-uwp-apps), telles que l’activation du protocole avec des paramètres personnalisés.
   
1. Sélectionnez **Démarrer**, ou si l’application est en cours d’exécution, sélectionnez **attacher**.

Lorsque vous commencez à déboguer un package d’application installée sur un appareil connecté Xbox, HoloLens ou IoT pour la première fois, Visual Studio installe la version correcte du débogueur distant pour votre appareil cible. Installation du débogueur distant peut prendre du temps et le message **démarrage du débogueur distant** affiche pendant qu’il se passe.

>[!NOTE]
>Actuellement, un appareil Xbox ou HoloLens redémarre l’application avec le débogueur attaché si elle était déjà en cours d’exécution.

Pour plus d’informations sur le déploiement distant des applications UWP, consultez [déployer et déboguer les applications UWP](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) et [UWP de déboguer des applications sur des ordinateurs distants](run-windows-store-apps-on-a-remote-machine.md). 
  
## <a name="see-also"></a>Voir aussi  
 [Débogage dans Visual Studio](../debugger/index.md)  
 [Visite guidée des fonctionnalités du débogueur](../debugger/debugger-feature-tour.md)  
 [Débogage distant](../debugger/remote-debugging.md)  
 [Configurer le pare-feu Windows pour le débogage distant](../debugger/configure-the-windows-firewall-for-remote-debugging.md)  
 [Attributions de ports au débogueur distant](../debugger/remote-debugger-port-assignments.md)  
 [Erreurs de débogage distant et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)