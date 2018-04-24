---
title: Exécuter les applications UWP sur un ordinateur distant | Documents Microsoft
ms.custom: ''
ms.date: 01/05/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 2c09d29340584f3f6187175342fd1171dd59ba37
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="run-uwp-apps-on-a-remote-machine-in-visual-studio"></a>Exécuter les applications UWP sur un ordinateur distant dans Visual Studio
  
Pour exécuter une application UWP sur un ordinateur distant, vous devez joindre à l’aide des outils à distance pour Visual Studio. Les outils à distance permettent d’exécuter, déboguer, Profiler et tester une application UWP qui s’exécute sur un périphérique à partir d’un deuxième ordinateur exécutant Visual Studio. En cours d’exécution sur un périphérique distant peut être particulièrement efficace lorsque l’ordinateur Visual Studio ne prend pas en charge les fonctionnalités spécifiques aux applications UWP, telles que la fonction tactile, emplacement géographique et l’orientation physique. Cette rubrique décrit les procédures de configuration et de démarrage d'une session distante.

Dans certains scénarios, les outils à distance sont installés automatiquement lorsque vous déployez sur un périphérique distant.

- Pour les PC Windows 10 en cours d’exécution mise à jour de créateurs et versions ultérieures, les outils à distance seront installés automatiquement.
- Pour les appareils Windows 10 Xbox, IOT et HoloLens, les outils à distance seront installés automatiquement.
- Pour Windows Mobile 10, vous devez être connecté physiquement au numéro de téléphone, vous devez activer [mode développeur](/windows/uwp/get-started/enable-your-device-for-development) et vous devez sélectionner **périphérique** en tant que la cible de débogage. Les outils à distance ne sont pas requises ou pris en charge.

Pour les PC Windows 10 version de mise à jour d’un créateur versions antérieures de Windows en cours d’exécution, vous devez installer les outils à distance sur l’ordinateur distant manuellement avant de pouvoir déboguer. Suivez les instructions de cette rubrique. 
  
##  <a name="BKMK_Prerequisites"></a> Conditions préalables  
 Pour déboguer sur un appareil distant :  
  
- L’appareil distant et l’ordinateur Visual Studio doivent être connectés via un réseau ou directement à l’aide d’un câble USB ou Ethernet. Le débogage sur Internet n'est pas pris en charge.  

- Vous devez activer [mode développeur](/windows/uwp/get-started/enable-your-device-for-development). 
  
- Pour les PC Windows 10 exécutant une version de Windows 10 antérieure à la mise à jour du créateur de Windows 10, vous devez [installer et exécuter les composants de débogage à distance](#BKMK_download).
  
##  <a name="BKMK_Security"></a> Sécurité  
Par défaut, **universel (protocole non chiffré)** est utilisé sur Windows 10. Ths protocole doit uniquement être utilisé sur des réseaux approuvés. La connexion de débogage est vulnérable aux utilisateurs malveillants qui pourrait intercepter et modifier les données transmises entre le développement et l’ordinateur distant.
  
> [!WARNING]
>  Il n’existe aucune sécurité de réseau lorsque vous définissez le mode d’authentification **universel (protocole non chiffré)** ou **aucun**. Choisissez ces modes uniquement si vous êtes sûr que le réseau n’est pas exposé à des programmes malveillants ou dangereux.  
  
##  <a name="BKMK_DirectConnect"></a> Comment se connecter directement à l’aide d’un câble USB 

Sur Windows 10, vous pouvez déployer sur un périphérique USB connecté en choisissant **périphérique** au lieu de **ordinateur distant** en tant que la cible de déploiement (vous pouvez le faire dans le **Standard** barre d’outils ou dans la page de propriétés de débogage).

##  <a name="BKMK_ConnectVS"></a> Configurer le projet Visual Studio pour le débogage distant  
 Vous spécifiez le périphérique distant auquel se connecter dans les propriétés du projet. La procédure varie en fonction du langage de programmation. Vous pouvez taper le nom de réseau de l’appareil distant ou vous pouvez le sélectionner à partir de la **connexion à distance** boîte de dialogue.  
  
 ![Boîte de dialogue de connexion du débogueur distant sélectionnez](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
 La boîte de dialogue répertorie uniquement les appareils qui se trouvent sur le sous-réseau local de l'ordinateur Visual Studio et qui exécutent le débogueur distant.  
  
> [!TIP]
>  Si vous avez des problèmes pour vous connecter à un périphérique distant, entrez son adresse IP. Pour connaître l'adresse IP d'un périphérique, ouvrez une fenêtre de commande, puis tapez **ipconfig**. L'adresse IP s'affiche comme **IPv4 Address**.  
  
###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Choisissez le périphérique distant pour les projets c# et Visual Basic  
  
1.  Sélectionnez le nom du projet dans l'Explorateur de solutions, puis choisissez **Propriétés** dans le menu contextuel.  
  
2.  Sélectionnez **Déboguer**.  
  
3.  Choisissez **Ordinateur distant** dans la liste **Périphérique cible** .  
  
4.  Entrez le nom réseau du périphérique distant dans la zone **Ordinateur distant** ou choisissez **Rechercher** pour sélectionner le périphérique dans la boîte de dialogue **Sélectionner une connexion au débogueur distant** . 

    ![Propriétés du projet pour le débogage distant managé](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")  
  
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Choisissez le périphérique distant pour les projets JavaScript et C++  
  
1.  Sélectionnez le nom du projet dans l'Explorateur de solutions, puis choisissez **Propriétés** dans le menu contextuel.  
  
2.  Développez le nœud **Propriétés de configuration** , puis sélectionnez **Débogage**.  
  
3.  Choisissez **Remote Debugger** dans la liste **Débogueur à lancer** .  
  
4.  Entrez le nom réseau du périphérique distant dans la zone **Nom de l'ordinateur** ou choisissez la flèche Bas de la zone pour sélectionner le périphérique dans la boîte de dialogue **Sélectionner une connexion au débogueur distant** .  

    ![C&#43; &#43; propriétés pour le débogage distant de projet](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")
  
## <a name="BKMK_download"></a> Téléchargez et installez les outils à distance (créateurs avant mise à jour)

Si vous utilisez des versions de mise à jour d’un créateur versions antérieures de Windows 10, suivez ces instructions. Sinon, vous pouvez ignorer cette section.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> Configurer le débogueur distant

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]  
  
##  <a name="BKMK_RunRemoteDebug"></a> Démarrer une session de débogage à distance  
 Le démarrage, la désactivation et l'exploration d'une session de débogage distant s'effectuent de la même façon que pour une session locale. Dans les versions de mise à jour du pre-créateur de Windows 10, assurez-vous que Remote Debugging Monitor s’exécute sur le périphérique distant.  
  
 Choisissez ensuite **Démarrer le débogage** dans le menu **Déboguer** (clavier : F5). Le projet est recompilé, puis déployé et démarré sur le périphérique distant. Le débogueur interrompt l'exécution aux points d'arrêt et vous pouvez effectuer un pas à pas détaillé, principal et sortant de votre code. Choisissez **Arrêter le débogage** pour terminer la session de débogage et fermer l'application distante.
  
## <a name="see-also"></a>Voir aussi  
 [Les options de déploiement à distance avancées](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)  
 [Test d’applications UWP avec Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Déboguer des applications dans Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)