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
ms.openlocfilehash: 358dc0b457381bb56532e6cae1156aac9ea2dba2
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2018
---
1.  Sur l’appareil ou serveur ordinateur que vous souhaitez déboguer (plutôt que l’ordinateur exécutant Visual Studio), obtenir la version des outils à distance.

    |Version|Lien|Notes|
    |-|-|-|
    |Visual Studio 2017 (dernière version)|[Outils à distance](https://www.visualstudio.com/downloads/?q=remote+tools#remote-tools-for-visual-studio-2017)|Toujours télécharger la version correspondant à votre système d’exploitation de périphérique (x86 ou x64). Sur Windows Server, consultez [débloquer le téléchargement du fichier](../../debugger/remote-debugging.md#unblock_msvsmon) de l’aide télécharger les outils à distance.|
    |2017 de Visual Studio (plus ancienne)|[Outils à distance](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Les outils à distance pour les versions antérieures de Visual Studio 2017 sont disponibles à partir de My.VisualStudio.com. Si vous y êtes invité, jointure du groupe Visual Studio Dev Essentials libre, ou connectez-vous avec votre abonnement Visual Studio code. Sur Windows Server, consultez [débloquer le téléchargement du fichier](../../debugger/remote-debugging.md#unblock_msvsmon) de l’aide télécharger les outils à distance.|
    |Visual Studio 2015 (plus ancienne)|[Outils à distance](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Si vous y êtes invité, jointure du groupe Visual Studio Dev Essentials libre, ou connectez-vous avec votre abonnement Visual Studio code. Sur Windows Server, consultez [débloquer le téléchargement du fichier](../../debugger/remote-debugging.md#unblock_msvsmon) de l’aide télécharger les outils à distance.|
    |Visual Studio 2013|[Outils à distance](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Télécharger la page dans la documentation de Visual Studio 2013|
    |Visual Studio 2012|[Outils à distance](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Télécharger la page dans la documentation de Visual Studio 2012|
  
2.  Sur la page de téléchargement, choisissez la version des outils qui correspond à votre système d’exploitation (x 86, x64 ou ARM) et télécharger les outils à distance.
  
    > [!IMPORTANT]
    >  Nous vous recommandons de qu'installer la version la plus récente des outils à distance qui correspond à votre version de Visual Studio. Versions incompatibles ne sont pas recommandées. En outre, vous devez installer les outils à distance qui ont la même architecture que le système d’exploitation sur lequel vous souhaitez l’installer. En d’autres termes, si vous souhaitez déboguer une application 32 bits sur un ordinateur distant exécutant un système d’exploitation de 64 bits, vous devez installer la version 64 bits des outils à distance sur l’ordinateur distant. 
    >   
    >  Surface 3 basculée ARM vers x64 architecture. Une version ARM des outils à distance n’est pas disponible pour Visual Studio 2017. Pour Visual Studio 2015, recherchez la version ARM dans le téléchargement de la version RTW de Visual Studio 2015.
  
3.  Lorsque vous avez terminé de télécharger le fichier exécutable, accédez à la section suivante et suivez les instructions d’installation.

Si vous essayez de copier le débogueur distant (msvsmon.exe) à l’ordinateur distant et l’exécuter, n’oubliez pas que le **Assistant Configuration Débogueur distant** (**rdbgwiz.exe**) est installé uniquement lorsque vous téléchargez le outils. Vous devrez peut-être utiliser l’Assistant de configuration plus tard, en particulier si vous souhaitez que le débogueur distant s’exécute en tant que service. Pour plus d’informations, consultez [(facultatif) configurer le débogueur distant en tant que service](../../debugger/remote-debugging.md#bkmk_configureService).
