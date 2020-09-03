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
ms.openlocfilehash: 1e90a1d9e03892cf81bd2257d3dcc6e25ab36246
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89324426"
---
Sur le périphérique ou le serveur distant sur lequel vous souhaitez effectuer le débogage, plutôt que sur l’ordinateur Visual Studio, téléchargez et installez la version appropriée des outils de contrôle à distance à partir des liens figurant dans le tableau suivant.

- Téléchargez les outils de contrôle à distance les plus récents pour votre version de Visual Studio. La dernière version des outils de contrôle à distance est compatible avec les versions antérieures de Visual Studio, mais les anciennes versions des outils de contrôle à distance ne sont pas compatibles avec les versions ultérieures de Visual Studio. (Par exemple, si vous utilisez Visual Studio 2017, téléchargez la dernière mise à jour des outils de contrôle à distance pour Visual Studio 2017. Dans ce scénario, ne téléchargez pas les outils de contrôle à distance de Visual Studio 2019.)
- Téléchargez les outils de contrôle à distance avec la même architecture que l’ordinateur sur lequel vous les installez. Par exemple, si vous souhaitez déboguer une application 32 bits sur un ordinateur distant exécutant un système d’exploitation 64 bits, installez les outils de contrôle à distance 64 bits.

::: moniker range=">=vs-2019"

|Version|Lien|Remarques|
|-|-|-|
|Visual Studio 2019|[outils de contrôle à distance.](https://visualstudio.microsoft.com/downloads#remote-tools-for-visual-studio-2019)|Compatible avec toutes les versions de Visual Studio 2019. Téléchargez la version correspondant à votre système d’exploitation d’appareil (x86, x64 ou ARM64). Sur Windows Server, consultez [débloquer le téléchargement de fichiers](../../debugger/remote-debugging-unblock-file-download.md) pour obtenir de l’aide sur le téléchargement des outils de contrôle à distance.|
|Visual Studio 2017|[outils de contrôle à distance.](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Compatible avec toutes les versions de Visual Studio 2017. Téléchargez la version correspondant à votre système d’exploitation d’appareil (x86, x64 ou ARM64). Sur Windows Server, consultez [débloquer le téléchargement de fichiers](../../debugger/remote-debugging-unblock-file-download.md) pour obtenir de l’aide sur le téléchargement des outils de contrôle à distance.|
|Visual Studio 2015|[outils de contrôle à distance.](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Les outils de contrôle à distance de Visual Studio 2015 sont disponibles à partir de My.VisualStudio.com. Si vous y êtes invité, joignez le programme [Visual Studio dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) gratuit ou connectez-vous avec votre ID d’abonnement Visual Studio. Sur Windows Server, consultez [débloquer le téléchargement de fichiers](../../debugger/remote-debugging-unblock-file-download.md) pour obtenir de l’aide sur le téléchargement des outils de contrôle à distance.|
|Visual Studio 2013|[outils de contrôle à distance.](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Page de téléchargement dans Visual Studio 2013 documentation|
|Visual Studio 2012|[outils de contrôle à distance.](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Page de téléchargement dans la documentation de Visual Studio 2012|

::: moniker-end

::: moniker range="vs-2017"

|Version|Lien|Remarques|
|-|-|-|
|Visual Studio 2017|[outils de contrôle à distance.](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Compatible avec toutes les versions de Visual Studio 2017. Téléchargez la version correspondant à votre système d’exploitation d’appareil (x86, x64 ou ARM64). Sur Windows Server, consultez [débloquer le téléchargement de fichiers](../../debugger/remote-debugging-unblock-file-download.md) pour obtenir de l’aide sur le téléchargement des outils de contrôle à distance. Pour obtenir la version la plus récente des outils de contrôle à distance, ouvrez le [document Visual Studio 2019](../../debugger/remote-debugging.md?view=vs-2019).|
|Visual Studio 2015|[outils de contrôle à distance.](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Les outils de contrôle à distance de Visual Studio 2015 sont disponibles à partir de My.VisualStudio.com. Si vous y êtes invité, joignez le programme [Visual Studio dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) gratuit ou connectez-vous avec votre ID d’abonnement Visual Studio. Sur Windows Server, consultez [débloquer le téléchargement de fichiers](../../debugger/remote-debugging-unblock-file-download.md) pour obtenir de l’aide sur le téléchargement des outils de contrôle à distance.|
|Visual Studio 2013|[outils de contrôle à distance.](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Page de téléchargement dans Visual Studio 2013 documentation|
|Visual Studio 2012|[outils de contrôle à distance.](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Page de téléchargement dans la documentation de Visual Studio 2012|

::: moniker-end

Vous pouvez exécuter le débogueur distant en copiant *msvsmon.exe* sur l’ordinateur distant, plutôt que d’installer les outils de contrôle à distance. Toutefois, l’Assistant Configuration du débogueur distant (*rdbgwiz.exe*) est disponible uniquement lorsque vous installez les outils de contrôle à distance. Vous devrez peut-être utiliser l’Assistant pour la configuration si vous souhaitez exécuter le débogueur distant en tant que service. Pour plus d’informations, consultez [(facultatif) configurer le débogueur distant en tant que service](../../debugger/remote-debugging.md#bkmk_configureService).

>[!NOTE]
>- Pour déboguer des applications Windows 10 sur des appareils ARM, utilisez ARM64, qui est disponible avec la dernière version des outils de contrôle à distance.
>- Pour déboguer des applications Windows 10 sur des appareils Windows RT, utilisez ARM, qui est uniquement disponible dans le téléchargement des outils de contrôle à distance de Visual Studio 2015.
