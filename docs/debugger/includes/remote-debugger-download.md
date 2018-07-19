---
title: Téléchargement du débogueur distant
description: Liens de téléchargement pour le débogueur distant
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 987193cb7f78947087c6d387e16261d83a20e7c2
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809244"
---
1.  Sur l’appareil ou serveur machine que vous souhaitez déboguer (plutôt que l’ordinateur qui exécute Visual Studio), obtenir la version des outils à distance.

    |Version|Lien|Notes|
    |-|-|-|
    |Visual Studio 2017 (version la plus récente)|[Outils à distance](https://visualstudio.microsoft.com/downloads/?q=remote+tools#remote-tools-for-visual-studio-2017)|Téléchargez toujours la version correspondant à votre système d’exploitation (x 86, x64 ou ARM64). Sur Windows Server, consultez [débloquer le téléchargement du fichier](../../debugger/remote-debugging.md#unblock_msvsmon) pour l’aide pour télécharger les outils à distance.|
    |Visual Studio 2017 (plus ancienne)|[Outils à distance](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Les outils à distance pour les versions antérieures de Visual Studio 2017 sont disponibles à partir de My.VisualStudio.com. Si vous y êtes invité, jointure du groupe Visual Studio Dev Essentials gratuit, ou connectez-vous avec votre abonnement Visual Studio code. Sur Windows Server, consultez [débloquer le téléchargement du fichier](../../debugger/remote-debugging.md#unblock_msvsmon) pour l’aide pour télécharger les outils à distance.|
    |Visual Studio 2015 (plus ancienne)|[Outils à distance](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Si vous y êtes invité, jointure du groupe Visual Studio Dev Essentials gratuit, ou connectez-vous avec votre abonnement Visual Studio code. Sur Windows Server, consultez [débloquer le téléchargement du fichier](../../debugger/remote-debugging.md#unblock_msvsmon) pour l’aide pour télécharger les outils à distance.|
    |Visual Studio 2013|[Outils à distance](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Télécharger la page dans la documentation de Visual Studio 2013|
    |Visual Studio 2012|[Outils à distance](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Télécharger la page dans la documentation de Visual Studio 2012|

2.  Sur la page de téléchargement, choisissez la version des outils qui correspond à votre système d’exploitation (x86, x64, ARM ou ARM64) et téléchargez les outils à distance.

    > [!IMPORTANT]
    >  Nous vous recommandons de qu'installer la version la plus récente des outils à distance qui correspond à votre version de Visual Studio. Versions incompatibles ne sont pas recommandées. En outre, vous devez installer les outils à distance qui ont la même architecture que le système d’exploitation sur lequel vous souhaitez l’installer. En d’autres termes, si vous souhaitez déboguer une application 32 bits sur un ordinateur distant exécutant un système d’exploitation de 64 bits, vous devez installer la version 64 bits des outils à distance sur l’ordinateur distant.
    >
    >  Pour le débogage sur Windows 10 sur les appareils ARM, cliquez sur Télécharger ARM64 disponible avec la dernière version des outils à distance.  Pour les appareils Windows RT, choisissez la version ARM, qui est uniquement disponible dans le téléchargement de Visual Studio 2015 RTW.

3.  Lorsque vous avez terminé de télécharger le fichier exécutable, accédez à la section suivante et suivez les instructions d’installation.

Si vous tentez de copier le débogueur distant (msvsmon.exe) sur l’ordinateur distant et l’exécuter, n’oubliez pas que le **Assistant Configuration Remote Debugger** (**rdbgwiz.exe**) est installé uniquement lorsque vous téléchargez le outils. Vous devrez peut-être utiliser l’Assistant de configuration plus tard, en particulier si vous souhaitez que le débogueur distant s’exécute en tant que service. Pour plus d’informations, consultez [(facultatif) configurer le débogueur distant en tant que service](../../debugger/remote-debugging.md#bkmk_configureService).
