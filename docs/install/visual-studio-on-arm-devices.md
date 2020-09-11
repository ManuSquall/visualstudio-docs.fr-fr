---
title: Appareils Powered Visual Studio sur ARM
description: Recommandations relatives à l’utilisation de Visual Studio sur des appareils avec des processeurs ARM.
ms.date: 09/10/2020
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 6aacd4639e440998a5123dae8c38a64c84ebb948
ms.sourcegitcommit: d9dd86c421532cfca6c0c5761d160f35829419c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90026290"
---
# <a name="visual-studio-on-arm-powered-devices"></a>Visual Studio sur des appareils fonctionnant sur ARM

> [!IMPORTANT]
> Visual Studio est uniquement pris en charge sur les appareils utilisant un processeur x86 ou AMD64/x64.

Visual Studio est conçu pour cibler des processeurs basés sur l’architecture x86, et il n’existe aucune version de Visual Studio pour les processeurs ARM. Toutefois, Windows fournit une [émulation x86 sur ARM](https://www.docs.microsoft.com/windows/uwp/porting/apps-on-arm-x86-emulation), que Visual Studio peut exécuter. L’exécution de Visual Studio sur un processeur ARM via l’émulation x86 altère gravement les performances de Visual Studio, et plusieurs fonctionnalités de Visual Studio ne sont pas conçues pour fonctionner dans ce scénario. Par conséquent, nous vous déconseillons d’exécuter Visual Studio sur des appareils qui utilisent des processeurs ARM et, à la place, recommander des appareils ARM ciblés à distance.

## <a name="remote-targeting-arm-devices"></a>Cibler à distance des appareils ARM
Pour une expérience optimale, nous vous recommandons d’utiliser Visual Studio sur un ordinateur distinct, équipé d’un processeur x86, et d’utiliser les fonctionnalités de déploiement et de débogage à distance dans Visual Studio pour cibler l’appareil ARM. Pour déboguer des applications Windows universelles déjà installées sur l’appareil, consultez la documentation [déboguer le package d’application installé](../debugger/debug-installed-app-package.md) . Pour déployer une nouvelle application, consultez [exécution d’une application du Windows Store remotley](../debugger/run-windows-store-apps-on-a-remote-machine.md). Pour tous les autres types d’applications, consultez la documentation sur le [débogage à distance](../debugger/remote-debugging.md) .

## <a name="tips-for-running-visual-studio-on-arm-devices"></a>Conseils pour l’exécution de Visual Studio sur des appareils ARM

### <a name="use-only-when-needed"></a>À utiliser uniquement lorsque cela est nécessaire
Optimisez votre temps à l’aide de Visual Studio uniquement lorsque cela est nécessaire pour un travail spécifique à ARM. Les performances sur n’importe quel périphérique ARM sont médiocres, et il est probable qu’il sera inacceptable pour une utilisation régulière.

### <a name="install-time"></a>Durée d’installation
Planifiez l’installation de Visual Studio plus longtemps et attendez qu’il s’arrête pendant des périodes de temps, ou redémarrez.
 
### <a name="remote-tools"></a>outils de contrôle à distance.
Pour déboguer une application qui s’exécute sur un appareil distant, vous devez [Télécharger et installer les outils de contrôle à distance](../debugger/remote-debugging.md#download-and-install-the-remote-tools) pour ARM.

### <a name="start-debugging-f5"></a>Démarrer le débogage (F5)
Tous les projets Visual Studio ne sont pas configurés pour lancer des projets localement quand vous démarrez le débogage (**F5**) à partir d’un appareil ARM. Vous devrez peut-être configurer Visual Studio pour le débogage distant, même si votre application s’exécute localement. Pour plus d’informations, consultez [débogage distant](../debugger/remote-debugging.md).

## <a name="we-need-your-help"></a>Nous avons besoin de votre aide !
Si vous souhaitez que Visual Studio s’exécute en mode natif sur des appareils ARM, nous aimerions connaître les scénarios et le support nécessaires. Vous pouvez nous contacter en publiant sur la [communauté des développeurs](https://developercommunity.visualstudio.com/idea/1161018/native-arm-support-for-visual-studio.html). 
