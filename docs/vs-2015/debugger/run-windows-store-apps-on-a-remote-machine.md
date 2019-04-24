---
title: Applications d’exécution Windows Store sur un ordinateur à distance | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa0fac38c79e4c54cb461ef51e016508d043f202
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60039793"
---
# <a name="run-windows-store-apps-on-a-remote-machine"></a>Exécuter des applications du Windows Store sur un ordinateur distant
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

S’applique uniquement à Windows] (.. /Image/windows_only_content.png « windows_only_content »)  
  
 Les outils de contrôle à distance de Visual Studio permettent d'exécuter, de déboguer, de profiler et de tester une application Windows Store en cours d'exécution sur un périphérique à partir d'un deuxième ordinateur exécutant Visual Studio. L'exécution sur un périphérique distant peut être particulièrement efficace lorsque l'ordinateur Visual Studio ne prend pas en charge une fonctionnalité spécifique aux applications Windows Store, telle que la fonction tactile, la géo-localisation et l'orientation physique. Cette rubrique décrit les procédures de configuration et de démarrage d'une session distante.  
  
## <a name="BKMK_In_this_topic"></a> Dans cette rubrique  
 Vous pouvez apprendre :  
  
 [Conditions préalables](#BKMK_Prerequisites)  
  
 [Sécurité](#BKMK_Security)  
  
 [Comment se connecter directement à un périphérique distant](#BKMK_DirectConnect)  
  
 [Installation des outils de contrôle à distance](#BKMK_Installing_the_Remote_Tools)  
  
 [Démarrage de Remote Debugging Monitor](#BKMK_Starting_the_Remote_Debugger_Monitor)  
  
 [Configuration du débogueur à distance](#BKMK_ConfigureRemoteDebugger)  
  
 [Configuration du projet Visual Studio pour le débogage distant](#BKMK_ConnectVS)  
  
- [Choix de l'appareil distant pour les projets C# et Visual Basic](#BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects)  
  
- [Choix de l'appareil distant pour les projets JavaScript et C++](#BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects)  
  
  [Exécution d'une session de débogage distant](#BKMK_RunRemoteDebug)  
  
## <a name="BKMK_Prerequisites"></a> Conditions préalables  
 Pour déboguer sur un appareil distant :  
  
- L'appareil distant et l'ordinateur Visual Studio doivent être connectés sur un réseau ou directement à l'aide d'un câble Ethernet. Le débogage sur Internet n'est pas pris en charge.  
  
- Une licence de développeur doit être installée sur le périphérique distant.  
  
- L'appareil distant doit exécuter les composants de débogage distant.  
  
- Vous devez être administrateur sur le périphérique distant pour configurer le pare-feu pendant l'installation. Vous devez disposer d'un accès utilisateur au périphérique distant pour exécuter le débogueur distant ou vous y connecter.  
  
## <a name="BKMK_Security"></a> Sécurité  
 Par défaut, le débogueur distant utilise l'authentification Windows.  
  
> [!WARNING]
>  Vous pouvez également choisir d'exécuter le débogueur distant en mode Aucune authentification, mais ce mode est fortement déconseillé. Il n'existe aucune sécurité du réseau lorsque vous lancez l'exécution dans ce mode. Sélectionnez le mode Aucune authentification uniquement si vous êtes sûr que le réseau n'est pas exposé à un problème de sécurité lié à des programmes malveillants ou dangereux.  
  
## <a name="BKMK_DirectConnect"></a> Comment se connecter directement à un périphérique distant  
 Pour vous connecter directement à un périphérique distant, connectez l'ordinateur Visual Studio au périphérique à l'aide d'un câble Ethernet standard. Si le périphérique n'est pas équipé de port Ethernet, utilisez un adaptateur USB à Ethernet pour brancher le câble.  
  
## <a name="BKMK_Installing_the_Remote_Tools"></a> Installation des outils de contrôle à distance  
  
> [!NOTE]
>  **Versions et mises à jour**  
>   
>  Les **Outils de contrôle à distance de Visual Studio 2015** ne sont pas pris en charge pour les versions antérieures de Visual Studio.  
>   
>  Nous vous recommandons d'installer la version de mise à jour des Outils de contrôle à distance de Visual Studio 2015 qui correspond à la version de mise à jour de votre installation de Visual Studio.  
>   
>  Le débogueur VS est compatible avec toute combinaison de versions de VS 2015 et des outils de contrôle à distance pour Visual Studio 2015. Toutefois, les dernières fonctionnalités de Visual Studio nécessitent la version la plus récente de Visual Studio et des outils de contrôle à distance.  
>   
>  D'autres outils de diagnostic peuvent exiger les mêmes versions des outils de contrôle à distance et de Visual Studio.  
  
 **Installation des composants de débogage distant sur un appareil distant**  
  
 Pour exécuter ou enregistrer le programme d’installation pour les outils à distance, choisissez un des liens dans le tableau qui correspond à votre version de Visual Studio :  
  
|Version|Lien|Notes|
|-|-|-|
|Visual Studio 2015 Update 3|[Outils à distance](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Si vous y êtes invité, rejoindre le groupe de Visual Studio Dev Essentials gratuit, ou vous pouvez simplement vous connecter avec un abonnement Visual Studio valide. Puis ouvrez à nouveau le lien si nécessaire. Toujours télécharger la version correspondant à votre système d’exploitation (x 86, x64 ou ARM version)|
|Visual Studio 2015 (plus ancienne)|[Outils à distance](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Si vous y êtes invité, rejoindre le groupe de Visual Studio Dev Essentials gratuit, ou vous pouvez simplement vous connecter avec un abonnement Visual Studio valide. Puis ouvrez à nouveau le lien si nécessaire. Toujours télécharger la version correspondant à votre système d’exploitation (x 86, x64 ou ARM version)|
|Visual Studio 2013|[Outils à distance](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Télécharger la page dans la documentation de Visual Studio 2013|
  
 Vous pouvez choisir de télécharger le programme d'installation ou l'exécuter immédiatement. Lorsque vous exécutez le programme d'installation, acceptez le contrat utilisateur, puis choisissez **Installer**.  
  
 Par défaut, les composants de débogage à distance sont installés dans le dossier **C:\Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger** .  
  
## <a name="BKMK_Starting_the_Remote_Debugger_Monitor"></a> Démarrage de Remote Debugging Monitor  
  
> [!NOTE]
>  Comme le débogueur distant configure le pare-feu pour autoriser la communication avec l'hôte Visual Studio, vous devez être administrateur sur le périphérique distant lorsque vous démarrez le débogueur distant pour la première fois.  
  
 Après avoir installé les outils de contrôle à distance, choisissez **Remote Debugger** dans l'écran **Démarrer** . La boîte de dialogue **Configuration du débogage distant** apparaît lorsque vous démarrez le débogueur distant pour la première fois.  
  
 Dans la boîte de dialogue **Configuration du débogage distant** :  
  
1. Si l'API des services Web Windows n'est pas installée, choisissez **Installer**  
  
2. Dans le groupe **Configurer le Pare-feu Windows** , choisissez les réseaux pour lesquels vous souhaitez autoriser des connexions. Seuls les réseaux auxquels le périphérique est connecté actuellement sont activés. Vous devez sélectionner au moins un réseau.  
  
3. Sélectionnez **Configurer le débogage distant** pour définir les options du pare-feu et démarrez Remote Debugging Monitor.  Ouvrez la boîte de dialogue **Visual Studio Remote Debugging Monitor** pour accorder aux utilisateurs des autorisations d'accès aux outils de contrôle à distance et pour définir d'autres options avancées.  
  
4. La boîte de dialogue **Visual Studio Remote Debugging Monitor** s'affiche. Elle vous permet d'accorder aux utilisateurs des droits d'accès aux outils de contrôle à distance et de définir d'autres options avancées.  
  
## <a name="BKMK_ConfigureRemoteDebugger"></a> Configuration du débogueur à distance  
 Deux outils vous permettent de modifier la configuration du débogueur distant.  
  
1. Dans le menu **Outils** de **Visual Studio Remote Debugging Monitor**:  
  
   1. Choisissez **Options** pour modifier le numéro de port, le mode d'authentification ou l'intervalle de délai d'attente du débogueur distant.  
  
   2. Choisissez **Autorisations** pour ajouter ou supprimer des utilisateurs disposant d'une autorisation de débogage distant.  
  
       > [!NOTE]
       >  Les autorisations doivent être accordées à chaque compte d'utilisateur qui effectue un débogage distant.  
  
   Utilisez l' **Assistant Configuration Remote Debugger** pour définir des options avancées pour le débogueur distant. Pour ouvrir l'assistant, choisissez **Assistant Configuration Remote Debugger** dans l'écran de démarrage.  
  
2. Dans la page **Configurer le service Visual Studio Remote Debugger** , vous pouvez choisir d'exécuter le débogueur distant en tant que service. Dans la plupart des cas, l'exécution en tant que service n'est pas obligatoire.  
  
3. Dans la page **Configurer le Pare-feu Windows pour le débogage** , ajoutez ou supprimez les types de réseaux auxquels vous souhaitez que le débogueur distant se connecte. Seuls les réseaux auxquels le périphérique est connecté actuellement sont activés. Vous devez sélectionner au moins un réseau.  
  
## <a name="BKMK_ConnectVS"></a> Configuration du projet Visual Studio pour le débogage distant  
 Vous spécifiez le périphérique distant auquel se connecter dans les propriétés du projet. La procédure varie en fonction du langage de programmation. Entrez le nom de réseau de l'appareil distant ou sélectionnez-le dans la boîte de dialogue Sélectionner une connexion du débogueur distant.  
  
 ![Boîte de dialogue de connexion du débogueur distant sélectionnez](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
 La boîte de dialogue répertorie uniquement les appareils qui se trouvent sur le sous-réseau local de l'ordinateur Visual Studio et qui exécutent le débogueur distant.  
  
> [!TIP]
>  Si vous avez des problèmes pour vous connecter à un périphérique distant, entrez son adresse IP. Pour connaître l'adresse IP d'un périphérique, ouvrez une fenêtre de commande, puis tapez **ipconfig**. L'adresse IP s'affiche comme **IPv4 Address**.  
  
### <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Choix de l'appareil distant pour les projets C# et Visual Basic  
 ![Propriétés du projet pour le débogage distant managé](../debugger/media/vsrun-managed-projprop-remote.png "VSRUN_Managed_ProjProp_Remote")  
  
1. Sélectionnez le nom du projet dans l'Explorateur de solutions, puis choisissez **Propriétés** dans le menu contextuel.  
  
2. Sélectionnez **Déboguer**.  
  
3. Choisissez **Ordinateur distant** dans la liste **Périphérique cible** .  
  
4. Entrez le nom réseau du périphérique distant dans la zone **Ordinateur distant** ou choisissez **Rechercher** pour sélectionner le périphérique dans la boîte de dialogue **Sélectionner une connexion au débogueur distant** .  
  
### <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Choix de l'appareil distant pour les projets JavaScript et C++  
 ![C&#43; &#43; projeter des propriétés pour le débogage distant](../debugger/media/vsrun-cpp-projprop-remote.png "VSRUN_CPP_ProjProp_Remote")  
  
1. Sélectionnez le nom du projet dans l'Explorateur de solutions, puis choisissez **Propriétés** dans le menu contextuel.  
  
2. Développez le nœud **Propriétés de configuration** , puis sélectionnez **Débogage**.  
  
3. Choisissez **Remote Debugger** dans la liste **Débogueur à lancer** .  
  
4. Entrez le nom réseau du périphérique distant dans la zone **Nom de l'ordinateur** ou choisissez la flèche Bas de la zone pour sélectionner le périphérique dans la boîte de dialogue **Sélectionner une connexion au débogueur distant** .  
  
## <a name="BKMK_RunRemoteDebug"></a> Exécution d'une session de débogage distant  
 Le démarrage, la désactivation et l'exploration d'une session de débogage distant s'effectuent de la même façon que pour une session locale. Avant de démarrer le débogage, vérifiez que Remote Debugging Monitor est en cours d'exécution sur le périphérique distant.  
  
 Puis choisissez **démarrer le débogage** sur le **déboguer** menu (clavier : F5). Le projet est recompilé, puis déployé et démarré sur le périphérique distant. Le débogueur interrompt l'exécution aux points d'arrêt et vous pouvez effectuer un pas à pas détaillé, principal et sortant de votre code. Choisissez **Arrêter le débogage** pour terminer la session de débogage et fermer l'application distante. Pour plus d’informations, consultez [déboguer des applications dans Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Test des applications du Windows Store avec Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Déboguer des applications dans Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
