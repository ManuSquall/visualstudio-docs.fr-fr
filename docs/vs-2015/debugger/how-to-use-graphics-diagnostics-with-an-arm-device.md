---
title: 'Comment : utiliser Graphics Diagnostics avec un appareil ARM | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 346fd3c0-9e92-4ab8-bb3b-1aa9000a2483
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24067412f875001185a0709c41f930ce3cdc8f3c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504618"
---
# <a name="how-to-use-graphics-diagnostics-with-an-arm-device"></a>Comment : utiliser Graphics Diagnostics avec un appareil ARM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : utiliser Graphics Diagnostics avec un appareil ARM](https://docs.microsoft.com/visualstudio/debugger/graphics/how-to-use-graphics-diagnostics-with-an-arm-device).  
  
Graphics Diagnostics prend en charge le débogage distant des applications Direct3D sur les appareils ARM qui exécutent Windows RT 8.1 ou Windows Phone 8.1. Vous pouvez capturer les informations graphiques de votre application Direct3D pendant qu'elle s'exécute sur l'appareil ou utiliser ce dernier comme ordinateur de lecture pour des informations graphiques capturées antérieurement.  
  
## <a name="using-graphics-diagnostics-with-an-arm-based-device"></a>Utilisation de Graphics Diagnostics avec un appareil ARM  
 Sachant que Visual Studio ne s'exécute pas sur les appareils ARM, vous devez utiliser le débogueur distant pour analyser une application qui s'exécute sur ces appareils. En prenant en charge la capture et la lecture des informations graphiques, le débogueur distant vous permet de diagnostiquer les erreurs de rendu et d'évaluer les performances graphiques de ces appareils avec autant de facilité que pour déboguer votre application sur ces mêmes appareils.  
  
 Pour utiliser les fonctionnalités de Graphics Diagnostics, commencez par activer le débogage distant sur votre appareil.  
  
#### <a name="to-enable-remote-debugging-on-your-arm-based-device"></a>Pour activer le débogage distant sur votre appareil ARM  
  
1.  Installer le [stratégie de Kits ARM](http://msdn.microsoft.com/windows/desktop/dn469188) sur votre appareil ARM.  
  
2.  Installer le [les outils de débogage à distance](http://go.microsoft.com/fwlink/?LinkId=393086) sur votre appareil ARM.  
  
> [!IMPORTANT]
>  Pour les appareils Windows Phone 8.1, vous serez peut-être amené à inscrire votre téléphone pour le développement. Pour cela, vous devez être inscrit en tant que développeur. Pour plus d’informations, consultez [comment déployer et exécuter une application pour Windows Phone 8](http://msdn.microsoft.com/library/windowsphone/develop/ff402565.aspx).  
  
 Une fois le débogage distant activé sur votre appareil, faites-en votre cible de débogage et démarrez Graphics Diagnostics.  
  
#### <a name="to-configure-and-start-graphics-diagnostics-on-your-device"></a>Pour configurer et démarrer Graphics Diagnostics sur votre appareil  
  
1.  Sur le **plateformes Solution** liste déroulante, sélectionnez **ARM** afin que votre appareil ARM seront disponible en tant que cible de débogage distant.  
  
2.  Sur le **cible de débogage** liste déroulante, sélectionnez votre appareil ARM.  
  
3.  Dans le menu, choisissez **déboguer**, **Graphics**, **démarrer les Diagnostics**. (clavier : Alt+F5)  
  
## <a name="see-also"></a>Voir aussi  
 [Exécuter des applications de Store de Windows sur un ordinateur distant](../debugger/run-windows-store-apps-on-a-remote-machine.md)   
 [Guide pratique pour modifier l’ordinateur de réexécution de Graphics Diagnostics](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md)



