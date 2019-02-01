---
title: Déboguer des applications UWP sur des ordinateurs distants | Microsoft Docs
ms.date: 10/05/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 9125887789cdeee3152f9ebf3e2c82cf523cc468
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932764"
---
# <a name="debug-uwp-apps-on-remote-machines-from-visual-studio"></a>Déboguer des applications UWP sur des ordinateurs distants à partir de Visual Studio
  
Vous pouvez utiliser Visual Studio pour exécuter, déboguer, Profiler et tester une application Universal Windows Platform (UWP) sur un autre ordinateur ou périphérique. L’application UWP en cours d’exécution sur un ordinateur distant est particulièrement utile lorsque l’ordinateur Visual Studio ne prend pas en charge la fonctionnalité spécifique à UWP comme tactile, emplacement géographique ou l’orientation physique. 

##  <a name="BKMK_Prerequisites"></a> Conditions préalables  

Pour déboguer une application UWP sur un appareil distant à partir de Visual Studio :  
  
- Le projet Visual Studio doit être configuré pour le débogage distant.
- L’ordinateur distant et l’ordinateur Visual Studio doivent être connectés via un réseau, ou directement par le biais d’un câble USB ou Ethernet. Le débogage sur Internet n'est pas pris en charge.  
- Vous devez [activer le mode développeur](/windows/uwp/get-started/enable-your-device-for-development) sur l’ordinateur Visual Studio et l’ordinateur distant. 
- Les ordinateurs à distance doivent exécuter les outils à distance pour Visual Studio. 
  - Certaines versions de Windows 10 démarrez et exécutez les outils à distance automatiquement. Sinon, [installer et exécuter les outils à distance pour Visual Studio](#BKMK_download).
  - Périphériques Windows Mobile 10 ne requièrent ou prennent en charge les outils à distance. 

##  <a name="BKMK_ConnectVS"></a> Configurer un projet Visual Studio pour le débogage distant
<a name="BKMK_DirectConnect"></a> Vous utilisez le projet **propriétés** pour spécifier le périphérique à distance pour se connecter à. Les paramètres diffèrent selon le langage de programmation. 

> [!CAUTION]
> Par défaut, la page de propriétés définit **universel (protocole non chiffré)** en tant que le **Type d’authentification** pour les connexions à distance de Windows 10. Vous devrez peut-être définir **aucune authentification** pour se connecter au débogueur distant. **Universel (protocole non chiffré)** et **aucune authentification** protocoles n’ont aucune sécurité du réseau, par conséquent, les données transmises entre le développement et les ordinateurs distants sont vulnérables. Choisissez ces types d’authentification uniquement pour des réseaux approuvés que vous êtes sûr ne sont pas exposés à des programmes malveillants ou dangereux. 
>
>Si vous choisissez **l’authentification Windows** pour le **Type d’authentification**, vous devez vous connecter à l’ordinateur distant lors du débogage. Le débogueur distant doit également être en cours d’exécution sous **l’authentification Windows** mode, avec le même compte d’utilisateur que sur l’ordinateur Visual Studio.

###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Configurer un C# ou un projet Visual Basic pour le débogage distant  

1. Sélectionnez le C# ou un projet Visual Basic dans Visual Studio **l’Explorateur de solutions** et sélectionnez le **propriétés** icône, appuyez sur **Alt** +  **Entrez**, ou avec le bouton droit et choisissez **propriétés**.
  
1.  Sélectionnez l’onglet **Débogage**.  
  
1.  Sous **appareil cible**, sélectionnez **Machine distante** pour un ordinateur distant, ou **appareil** pour un appareil Mobile Windows 10 directement connectés.  
  
1.  Pour un ordinateur distant, entrez le nom de réseau ou l’adresse IP dans le **machine distante** champ ou sélectionnez **trouver** pour rechercher l’appareil dans le [boîte de dialogue connexions à distance](#remote-connections). 
    
    ![Propriétés du projet pour le débogage distant managé](../debugger/media/vsrun_managed_projprop_remote.png "Managed Debug des propriétés de projet")  
    
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Configurer un projet JavaScript ou C++ pour le débogage distant   
  
1.  Sélectionnez le projet C++ ou JavaScript dans Visual Studio **l’Explorateur de solutions** et sélectionnez le **propriétés** icône, appuyez sur **Alt**+**entrée** , ou avec le bouton droit et choisissez **propriétés**.
  
1.  Sélectionnez le **débogage** onglet.  
  
3.  Sous **débogueur à lancer**, sélectionnez **Machine distante** pour un ordinateur distant, ou **appareil** pour un appareil Mobile Windows 10 directement connectés. 
  
1.  Pour un ordinateur distant, entrez ou sélectionnez le nom de réseau ou l’adresse IP dans le **nom_machine** champ ou la liste déroulante et sélectionnez **localiser** pour rechercher l’appareil dans le [boîte de dialogue connexions à distance ](#remote-connections). 

    ![Propriétés du projet C++ pour le débogage distant](../debugger/media/vsrun_cpp_projprop_remote.png "propriétés du projet de débogage C++")
    
### <a name="remote-connections"></a> Utilisez la boîte de dialogue connexions à distance

Dans le **connexions à distance** boîte de dialogue, vous pouvez rechercher une adresse IP ou le nom de l’ordinateur distant spécifique, ou détecter automatiquement les connexions en sélectionnant l’icône d’actualisation de la direction d’arrondi. La boîte de dialogue recherche uniquement les appareils sur le sous-réseau local qui sont en cours d’exécution du débogueur distant. Pas tous les appareils peuvent être détectés dans le **connexions à distance** boîte de dialogue. 

 ![Boîte de dialogue de connexion à distance](../debugger/media/vsrun_selectremotedebuggerdlg.png "boîte de dialogue connexions à distance")  

>[!TIP]
>Si vous ne peut pas se connecter à un périphérique distant par nom, essayez d’utiliser son adresse IP. Pour déterminer l’adresse IP, sur le périphérique distant, entrez **ipconfig** dans une fenêtre de commande. L’adresse IP apparaît sous la forme **adresse IPv4**.  
    
## <a name="BKMK_download"></a> Télécharger et installer les outils de contrôle à distance de Visual Studio

Pour Visual Studio déboguer des applications sur un ordinateur distant, l’ordinateur distant doit exécuter les outils à distance pour Visual Studio. 

- Périphériques Windows Mobile 10 ne requièrent pas ou ne prennent en charge les outils à distance. 
- Mettre à jour les PC Windows 10 exécutant Creators (version 1703) et une version ultérieure, les appareils Windows 10 Xbox, IoT et HoloLens installer les outils à distance automatiquement quand vous déployez l’application. 
- Sur les PC de pre-l’auteur de la mise à jour Windows 10, vous devez manuellement télécharger, installer et exécuter les outils à distance sur l’ordinateur distant avant de commencer le débogage.

**Pour télécharger et installer les outils à distance :**

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> Configurer les outils à distance

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]  
  
##  <a name="BKMK_RunRemoteDebug"></a> Déboguer des applications UWP à distance 

Le débogage distant fonctionne comme le débogage local. 

1. Dans les versions de mise à jour du pre-créateur de Windows 10, assurez-vous que Remote Debugging Monitor (*msvsmon.exe*) est en cours d’exécution sur le périphérique distant.  
   
1. Sur l’ordinateur Visual Studio, assurez-vous que la cible de débogage correct (**Machine distante** ou **appareil**) s’affiche en regard de la flèche verte dans la barre d’outils. 
   
1. Démarrer le débogage en sélectionnant **déboguer** > **démarrer le débogage**, en cliquant sur **F5**, ou en sélectionnant la flèche verte dans la barre d’outils. 
   
   RECOMPILE le projet, puis déploie et démarre sur le périphérique distant. Le débogueur interrompt l’exécution aux points d’arrêt, et vous pouvez effectuer un détaillé, principal et en dehors du code. 
   
1. Si nécessaire, sélectionnez **déboguer** > **arrêter le débogage** ou appuyez sur **MAJ**+**F5** pour arrêter le débogage et Fermez l’application distante.
  
## <a name="see-also"></a>Voir aussi  
 [Options avancées de déploiement à distance](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)  
 [Test d’applications UWP avec Visual Studio](/visualstudio/test/create-and-run-unit-tests-for-a-store-app-in-visual-studio/)   
 [Déployer des applications UWP dans Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
