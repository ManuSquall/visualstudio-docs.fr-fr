---
title: Déboguer un package d’application UWP installé | Microsoft Docs
description: Déboguez un package d’application plateforme Windows universelle (UWP) installé dans Visual Studio sur les ordinateurs, les Xbox et les appareils Internet des objets (IoT) Windows 10.
ms.custom: SEO-VS-2020
ms.date: 11/07/2018
ms.topic: how-to
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
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: e77d74e0d7d0094918ecbd4e86cdfe5d15e511bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857517"
---
# <a name="debug-an-installed-uwp-app-package-in-visual-studio"></a>Déboguer un package d’application UWP installé dans Visual Studio

Visual Studio peut déboguer des packages d’application plateforme Windows universelle (UWP) installés sur des ordinateurs Windows 10 et des appareils Xbox, HoloLens et IoT.

>[!NOTE]
>Le débogage Visual Studio pour les applications UWP installées n’est pas pris en charge sur les téléphones.

Pour plus d’informations sur le débogage des applications UWP, consultez les billets de blog sur le [débogage des packages d’application installés](https://devblogs.microsoft.com/devops/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) et la [création d’applications Windows universelles (UWP)](https://devblogs.microsoft.com/visualstudio/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-uwp-app-on-a-local-machine"></a>Déboguer une application UWP installée sur un ordinateur local

1. Dans Visual Studio, sélectionnez **Déboguer**  >  **autres cibles de débogage**  >  **déboguer le package d’application installé**.

1. Dans la boîte de dialogue **déboguer le package d’application installé** , sous **type de connexion**, sélectionnez **ordinateur local**.

1. Sous **packages d’applications installés**, sélectionnez l’application que vous souhaitez déboguer, ou tapez son nom dans la zone de recherche. Les packages d’applications qui ne sont pas exécutés s’affichent sous **non exécuté**, et les applications en cours d’exécution sont **en cours d’exécution**.

   ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

1. Si nécessaire, modifiez le type de code sous **déboguer ce type de code**, puis sélectionnez d’autres options.
   - Sélectionnez **ne pas lancer, mais déboguer mon code lorsqu’il commence** à démarrer le débogage au démarrage de l’application. Le démarrage du débogage lorsque l’application démarre est un moyen efficace de déboguer des chemins de contrôle à partir de [différentes méthodes de lancement](/windows/uwp/xbox-apps/automate-launching-uwp-apps), telles que l’activation de protocole avec des paramètres personnalisés.

1. Sélectionnez **Démarrer**, ou si l’application est en cours d’exécution, sélectionnez **attacher**.

> [!NOTE]
> Vous pouvez également effectuer l’attachement à n’importe quel processus d’application UWP ou autre en sélectionnant **Déboguer**  >  **attacher au processus** dans Visual Studio. Vous n’avez pas besoin du projet Visual Studio d’origine à attacher à un processus en cours d’exécution, mais le chargement des symboles de l’application peut être utile lors du débogage d’un processus pour lequel vous n’avez pas le code d’origine. Consultez [spécifier les fichiers de symboles et sources dans le débogueur](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="debug-an-installed-uwp-app-on-a-remote-computer-or-device"></a><a name="remote"></a> Déboguer une application UWP installée sur un ordinateur ou un appareil distant

La première fois que Visual Studio débogue une application UWP installée sur un appareil Windows 10 ou un ordinateur Windows 10 mis à jour à distance, il installe les outils de débogage à distance sur l’appareil cible.

1. [Activez le mode développeur](/windows/uwp/get-started/enable-your-device-for-development) sur l’ordinateur Visual Studio, ainsi que l’appareil ou l’ordinateur distant.

1. Si vous vous connectez à un ordinateur distant qui exécute la mise à jour Windows 10 du pré-créateur, [Installez et démarrez manuellement le débogueur distant](../debugger/remote-debugging.md) sur l’ordinateur distant.

1. Sur l’ordinateur Visual Studio, sélectionnez **Déboguer**  >  **autres cibles de débogage**  >  **déboguer le package d’application installé**.

1. Dans la boîte de dialogue **déboguer le package d’application installé** , sous **type de connexion**, sélectionnez ordinateur ou **périphérique** **distant** .

   Si vous sélectionnez **appareil**, votre ordinateur doit être connecté physiquement à un appareil Windows 10.

   Pour un ordinateur distant, si l’adresse de l’ordinateur n’apparaît pas en regard de **adresse**, sélectionnez **modifier**.

   1. Dans la boîte de dialogue **connexion à distance** , en regard de **adresse**, tapez le nom ou l’adresse IP de l’ordinateur auquel vous souhaitez vous connecter.

      ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

      Si le débogueur ne peut pas se connecter à un ordinateur distant à l’aide du nom de l’ordinateur, utilisez l’adresse IP à la place. Utilisez l’adresse IP pour les appareils Xbox, HoloLens ou IoT.
   1. Sélectionnez une option d’authentification en regard de **mode d’authentification**.

      Pour la plupart des applications, conservez la valeur par défaut, **Universal (protocole non chiffré)**.
   1. Sélectionnez **Sélectionner**.

1. Sous **packages d’applications installés**, sélectionnez l’application que vous souhaitez déboguer, ou tapez son nom dans la zone de recherche. Les packages d’applications qui ne sont pas exécutés s’affichent sous **non exécuté**, et les applications en cours d’exécution sont **en cours d’exécution**.

1. Si nécessaire, modifiez le type de code sous **déboguer ce type de code**, puis sélectionnez d’autres options.
   - Sélectionnez **ne pas lancer, mais déboguer mon code lorsqu’il commence** à démarrer le débogage au démarrage de l’application. Le démarrage du débogage lorsque l’application démarre est un moyen efficace de déboguer des chemins de contrôle à partir de [différentes méthodes de lancement](/windows/uwp/xbox-apps/automate-launching-uwp-apps), telles que l’activation de protocole avec des paramètres personnalisés.

1. Sélectionnez **Démarrer**, ou si l’application est en cours d’exécution, sélectionnez **attacher**.

Lorsque vous commencez à déboguer un package d’application installé sur un appareil Xbox, HoloLens ou IoT connecté pour la première fois, Visual Studio installe la version appropriée du débogueur distant pour votre appareil cible. L’installation du débogueur distant peut prendre un certain temps, et le message **démarrage du débogueur distant** s’affiche pendant qu’il se produit.

>[!NOTE]
>Actuellement, un appareil Xbox ou HoloLens redémarre l’application avec le débogueur attaché s’il était déjà en cours d’exécution.

Pour plus d’informations sur le déploiement à distance d’applications UWP, consultez [déployer et déboguer des applications UWP](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) et [Déboguer des applications UWP sur des ordinateurs distants](run-windows-store-apps-on-a-remote-machine.md).

## <a name="see-also"></a>Voir aussi

- [Débogage dans Visual Studio](../debugger/index.yml)
- [Présentation du débogueur](../debugger/debugger-feature-tour.md)
- [Débogage distant](../debugger/remote-debugging.md)
- [Configurer le pare-feu Windows pour le débogage à distance](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Attributions de ports au débogueur distant](../debugger/remote-debugger-port-assignments.md)
- [Erreurs de débogage à distance et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)