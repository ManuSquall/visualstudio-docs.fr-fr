---
title: 'Procédure : Utiliser Graphics Diagnostics avec un appareil ARM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 346fd3c0-9e92-4ab8-bb3b-1aa9000a2483
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5bbe12449849b656af2658c5bab667b0e611515e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685874"
---
# <a name="how-to-use-graphics-diagnostics-with-an-arm-device"></a>Procédure : Utiliser Graphics Diagnostics avec un appareil ARM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Graphics Diagnostics prend en charge le débogage distant des applications Direct3D sur les appareils ARM qui exécutent Windows RT 8.1 ou Windows Phone 8.1. Vous pouvez capturer les informations graphiques de votre application Direct3D pendant qu'elle s'exécute sur l'appareil ou utiliser ce dernier comme ordinateur de lecture pour des informations graphiques capturées antérieurement.  
  
## <a name="using-graphics-diagnostics-with-an-arm-based-device"></a>Utilisation de Graphics Diagnostics avec un appareil ARM  
 Sachant que Visual Studio ne s'exécute pas sur les appareils ARM, vous devez utiliser le débogueur distant pour analyser une application qui s'exécute sur ces appareils. En prenant en charge la capture et la lecture des informations graphiques, le débogueur distant vous permet de diagnostiquer les erreurs de rendu et d'évaluer les performances graphiques de ces appareils avec autant de facilité que pour déboguer votre application sur ces mêmes appareils.  
  
 Pour utiliser les fonctionnalités de Graphics Diagnostics, commencez par activer le débogage distant sur votre appareil.  
  
#### <a name="to-enable-remote-debugging-on-your-arm-based-device"></a>Pour activer le débogage distant sur votre appareil ARM  
  
1. Installer le [stratégie de Kits ARM](https://msdn.microsoft.com/windows/desktop/dn469188) sur votre appareil ARM.  
  
2. Installer le [les outils de débogage à distance](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015) sur votre appareil ARM.  
  
> [!IMPORTANT]
> Pour les appareils Windows Phone 8.1, vous serez peut-être amené à inscrire votre téléphone pour le développement. Pour cela, vous devez être inscrit en tant que développeur. Pour plus d’informations, consultez [comment déployer et exécuter une application pour Windows Phone 8](https://msdn.microsoft.com/library/windowsphone/develop/ff402565.aspx).  
  
 Une fois le débogage distant activé sur votre appareil, faites-en votre cible de débogage et démarrez Graphics Diagnostics.  
  
#### <a name="to-configure-and-start-graphics-diagnostics-on-your-device"></a>Pour configurer et démarrer Graphics Diagnostics sur votre appareil  
  
1. Sur le **plateformes Solution** liste déroulante, sélectionnez **ARM** afin que votre appareil ARM seront disponible en tant que cible de débogage distant.  
  
2. Sur le **cible de débogage** liste déroulante, sélectionnez votre appareil ARM.  
  
3. Dans le menu, choisissez **déboguer**, **Graphics**, **démarrer les Diagnostics**. (Clavier : Alt+F5)  
  
## <a name="see-also"></a>Voir aussi  
 [Exécuter des applications de Store de Windows sur un ordinateur distant](../debugger/run-windows-store-apps-on-a-remote-machine.md)   
 [Guide pratique pour modifier l’ordinateur de lecture de Graphics Diagnostics](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md)
