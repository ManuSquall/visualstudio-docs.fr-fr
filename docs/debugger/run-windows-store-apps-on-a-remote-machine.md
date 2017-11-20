---
title: "Exécuter les applications UWP sur un ordinateur distant | Documents Microsoft"
ms.custom: 
ms.date: 07/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
caps.latest.revision: "43"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e1b298f8088adf05992f7ebf8b5afbb743ec995
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2017
---
# <a name="run-uwp-apps-on-a-remote-machine"></a>Exécuter les applications UWP sur un ordinateur distant
![S’applique uniquement à Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
Pour exécuter une application UWP sur un ordinateur distant, vous devez joindre à l’aide des outils distants Visual Studio. Les outils à distance permettent d’exécuter, déboguer, Profiler et tester une application UWP qui s’exécute sur un périphérique à partir d’un deuxième ordinateur exécutant Visual Studio. En cours d’exécution sur un périphérique distant peut être particulièrement efficace lorsque l’ordinateur Visual Studio ne prend pas en charge les fonctionnalités spécifiques aux applications UWP, telles que la fonction tactile, emplacement géographique et l’orientation physique. Cette rubrique décrit les procédures de configuration et de démarrage d'une session distante.

Dans certains scénarios, les outils à distance sont installés automatiquement lorsque vous déployez sur un périphérique distant.

- Pour les PC Windows 10 en cours d’exécution mise à jour de créateurs et versions ultérieures, consultez [déboguer un Package d’application installé](debug-installed-app-package.md#remote). Les outils à distance seront installés automatiquement.
- Pour les appareils Windows 10 Xbox, IOT et HoloLens, consultez [déboguer un Package d’application installé](debug-installed-app-package.md#remote). Les outils à distance seront installés automatiquement.
- Pour Windows Phone, vous devez être connecté physiquement au numéro de téléphone, vous devez installer un [licence de développeur](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh974578.aspx) (Windows Phone 8 et 8.1) ou activer [mode développeur](/windows/uwp/get-started/enable-your-device-for-development) (Windows Mobile 10), et vous devez Sélectionnez **périphérique** en tant que la cible de débogage. Les outils à distance ne sont pas requises ou pris en charge.

Pour les PC Windows 8.1 et des PC Windows 10 version de mise à jour d’un créateur versions antérieures de Windows en cours d’exécution, vous devez installer les outils à distance sur l’ordinateur distant manuellement avant de pouvoir déboguer. Suivez les instructions de cette rubrique.
  
##  <a name="BKMK_Prerequisites"></a> Composants requis  
 Pour déboguer sur un appareil distant :  
  
-   L'appareil distant et l'ordinateur Visual Studio doivent être connectés sur un réseau ou directement à l'aide d'un câble Ethernet. Le débogage sur Internet n'est pas pris en charge.  

- Le périphérique distant doit être activé pour le développement.

    - Pour les appareils Windows 8 et Windows 8.1, un [licence de développeur](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh974578.aspx) doit être installé sur le périphérique distant.
    - Pour les appareils Windows 10, vous devez activer [mode développeur](/windows/uwp/get-started/enable-your-device-for-development). 
  
-   Pour les PC Windows 10 exécutant une version de Windows 10 antérieure à la mise à jour du créateur de Windows 10, vous devez installer et exécuter les composants de débogage distant.
  
-   Vous devez être administrateur sur le périphérique distant pour configurer le pare-feu pendant l'installation. Vous devez disposer d'un accès utilisateur au périphérique distant pour exécuter le débogueur distant ou vous y connecter.  
  
##  <a name="BKMK_Security"></a> Sécurité  
 Par défaut, le débogueur distant utilise l'authentification Windows.  
  
> [!WARNING]
>  Vous pouvez également choisir d'exécuter le débogueur distant en mode Aucune authentification, mais ce mode est fortement déconseillé. Il n'existe aucune sécurité du réseau lorsque vous lancez l'exécution dans ce mode. Sélectionnez le mode Aucune authentification uniquement si vous êtes sûr que le réseau n'est pas exposé à un problème de sécurité lié à des programmes malveillants ou dangereux.  
  
##  <a name="BKMK_DirectConnect"></a> Comment se connecter directement à un périphérique distant  
 Pour vous connecter directement à un périphérique distant, connectez l'ordinateur Visual Studio au périphérique à l'aide d'un câble Ethernet standard. Si le périphérique n'est pas équipé de port Ethernet, utilisez un adaptateur USB à Ethernet pour brancher le câble.  
  
## <a name="BKMK_download"></a>Téléchargez et installez les outils à distance

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
## <a name="BKMK_setup"></a>Configurer le débogueur distant

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]
  
##  <a name="BKMK_ConnectVS"></a> Configuration du projet Visual Studio pour le débogage distant  
 Vous spécifiez le périphérique distant auquel se connecter dans les propriétés du projet. La procédure varie en fonction du langage de programmation. Entrez le nom de réseau de l'appareil distant ou sélectionnez-le dans la boîte de dialogue Sélectionner une connexion du débogueur distant.  
  
 ![Boîte de dialogue de connexion du débogueur distant sélectionnez](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
 La boîte de dialogue répertorie uniquement les appareils qui se trouvent sur le sous-réseau local de l'ordinateur Visual Studio et qui exécutent le débogueur distant.  
  
> [!TIP]
>  Si vous avez des problèmes pour vous connecter à un périphérique distant, entrez son adresse IP. Pour connaître l'adresse IP d'un périphérique, ouvrez une fenêtre de commande, puis tapez **ipconfig**. L'adresse IP s'affiche comme **IPv4 Address**.  
  
###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Choix de l'appareil distant pour les projets C# et Visual Basic  
 ![Propriétés du projet pour le débogage distant managé](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")  
  
1.  Sélectionnez le nom du projet dans l'Explorateur de solutions, puis choisissez **Propriétés** dans le menu contextuel.  
  
2.  Sélectionnez **Déboguer**.  
  
3.  Choisissez **Ordinateur distant** dans la liste **Périphérique cible** .  
  
4.  Entrez le nom réseau du périphérique distant dans la zone **Ordinateur distant** ou choisissez **Rechercher** pour sélectionner le périphérique dans la boîte de dialogue **Sélectionner une connexion au débogueur distant** .  
  
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Choix de l'appareil distant pour les projets JavaScript et C++  
 ![C &#43; &#43; propriétés pour le débogage distant de projet](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")  
  
1.  Sélectionnez le nom du projet dans l'Explorateur de solutions, puis choisissez **Propriétés** dans le menu contextuel.  
  
2.  Développez le nœud **Propriétés de configuration** , puis sélectionnez **Débogage**.  
  
3.  Choisissez **Remote Debugger** dans la liste **Débogueur à lancer** .  
  
4.  Entrez le nom réseau du périphérique distant dans la zone **Nom de l'ordinateur** ou choisissez la flèche Bas de la zone pour sélectionner le périphérique dans la boîte de dialogue **Sélectionner une connexion au débogueur distant** .  
  
##  <a name="BKMK_RunRemoteDebug"></a> Exécution d'une session de débogage distant  
 Le démarrage, la désactivation et l'exploration d'une session de débogage distant s'effectuent de la même façon que pour une session locale. Avant de démarrer le débogage, vérifiez que Remote Debugging Monitor est en cours d'exécution sur le périphérique distant.  
  
 Choisissez ensuite **Démarrer le débogage** dans le menu **Déboguer** (clavier : F5). Le projet est recompilé, puis déployé et démarré sur le périphérique distant. Le débogueur interrompt l'exécution aux points d'arrêt et vous pouvez effectuer un pas à pas détaillé, principal et sortant de votre code. Choisissez **Arrêter le débogage** pour terminer la session de débogage et fermer l'application distante. Pour plus d’informations, consultez [déboguer des applications dans Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Test des applications UWP avec Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Déboguer des applications dans Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)