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
ms.openlocfilehash: 6c429614a094ceefc4f9a1e358ebc8ee26c40773
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50915156"
---
Sur l’appareil distant ou serveur que vous souhaitez déboguer sur, plutôt que l’ordinateur Visual Studio, téléchargez et installez la version correcte des outils distants parmi les liens dans le tableau suivant.

- Téléchargez les outils à distance la plus récentes pour votre version de Visual Studio. La dernière version des outils à distance est compatible avec les versions antérieures de Visual Studio, mais les versions antérieures des outils à distance ne sont pas compatibles avec les versions ultérieures de Visual Studio. 
- Téléchargez les outils à distance avec la même architecture que l’ordinateur que vous les installez sur. Par exemple, si vous souhaitez déboguer une application 32 bits sur un ordinateur distant exécutant un système d’exploitation de 64 bits, installez les outils à distance de 64 bits. 

|Version|Lien|Notes|
|-|-|-|
|Visual Studio 2017 (version la plus récente)|[Outils à distance](https://visualstudio.microsoft.com/downloads/?q=remote+tools#remote-tools-for-visual-studio-2017)|Compatible avec toutes les versions de Visual Studio 2017. Téléchargez la version correspondant à votre système d’exploitation (x 86, x64 ou ARM64). Sur Windows Server, consultez [débloquer le téléchargement du fichier](../../debugger/remote-debugging-unblock-file-download.md) pour télécharger les outils à distance de l’aide.|
|Visual Studio 2015|[Outils à distance](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Les outils à distance pour Visual Studio 2015 sont disponibles à partir de My.VisualStudio.com. Si vous y êtes invité, participez à la version gratuite [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) programme, ou connectez-vous avec votre ID d’abonnement Visual Studio. Sur Windows Server, consultez [débloquer le téléchargement du fichier](../../debugger/remote-debugging-unblock-file-download.md) pour télécharger les outils à distance de l’aide.|
|Visual Studio 2013|[Outils à distance](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#Installing_the_Remote_Tools)|Télécharger la page dans la documentation de Visual Studio 2013|
|Visual Studio 2012|[Outils à distance](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#BKMK_Installing_the_Remote_Tools)|Télécharger la page dans la documentation de Visual Studio 2012|

Vous pouvez exécuter le débogueur distant en copiant *msvsmon.exe* à l’ordinateur distant, plutôt que de l’installation des outils à distance. Toutefois, l’Assistant Configuration Remote Debugger (*rdbgwiz.exe*) est disponible uniquement lorsque vous installez les outils à distance. Vous devrez peut-être utiliser l’Assistant de configuration si vous souhaitez exécuter le débogueur distant en tant que service. Pour plus d’informations, consultez [(facultatif) configurer le débogueur distant en tant que service](../../debugger/remote-debugging.md#bkmk_configureService).

>[!NOTE]
>- Pour déboguer des applications Windows 10 sur les appareils ARM, utilisez ARM64, qui est disponible avec la dernière version des outils à distance.  
>- Pour déboguer des applications Windows 10 sur les appareils Windows RT, utilisez ARM, qui est disponible uniquement dans Visual Studio 2015 de téléchargement des outils à distance.

