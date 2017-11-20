---
title: "Exécuter des applications UWP et Windows 8.1 dans le simulateur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
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
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
caps.latest.revision: "42"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cf4c5d1e71a4d0e0d8ac74ba02bff29ddc1c7477
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2017
---
# <a name="run-uwp-and-windows-81-apps-in-the-simulator"></a>Exécuter des applications UWP et Windows 8.1 dans le simulateur
Le simulateur de Visual Studio pour les applications UWP et Windows 8.1 est une application de bureau qui simule une application UWP ou Windows 8.1. Vous pouvez exécuter les applications choisir la taille de l’écran physique et la résolution que vous voulez émuler. Vous pouvez également simuler la rotation des événements tactiles et courantes et simuler les propriétés de connexion réseau.
  
 Le simulateur fournit un environnement dans lequel vous pouvez concevoir, développer, déboguer et tester les applications UWP. Toutefois, avant de publier votre application au Microsoft Store, vous devez tester votre application sur un appareil réel.  
  
 Le simulateur de Visual Studio pour applications UWP ne s’exécute pas dans un environnement isolé sur votre ordinateur local. Par conséquent, les erreurs qui se produisent dans un simulateur, tel qu'une erreur irrécupérable à l'échelle du système, peuvent également affecter l'ordinateur entier.  
  
 Pour plus d'informations sur le Windows Phone, voir [Run Windows Phone apps in the emulator](../debugger/run-windows-phone-apps-in-the-emulator.md) .  
  
> [!IMPORTANT]
>  Le simulateur Visual Studio 2015 n’inclut pas le bouton de géolocalisation. En effet, le simulateur Windows 10 n’inclut pas la simulation de géolocalisation. Si vous devez effectuer ce type de simulation, vous pouvez utiliser le simulateur Visual Studio 2013 sur des systèmes d’exploitation Windows 8.1 ou antérieurs.  
  
##  <a name="BKMK_Set_the_simulator_as_the_target"></a> Définir un simulateur comme cible  
 Pour exécuter votre application UWP dans le simulateur, sélectionnez **simulateur** à partir de la liste déroulante liste en regard du **démarrer le débogage** bouton du débogueur **Standard** barre d’outils.  
  
 ![En cours d’exécution dans le simulateur](../debugger/media/vsrun_f5_simulator.png "VSRUN_F5_Simulator")  
  
##  <a name="BKMK_Choose_an_interaction_mode"></a> Choisir un mode d'interaction  
 Vous avez le choix entre les modes d’interaction suivants  
  
-   ![Bouton de mode](../debugger/media/simulator_mousemodebtn.png "SIMULATOR_MouseModeBtn") mode de la souris : définit le mode d’interaction des mouvements de la souris. Les mouvements de souris incluent les clics, les double-clics et le déplacement d'objets par glissement.  
  
-   ![Bouton Démarrer de l’émulation tactile](../debugger/media/simulator_starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") démarrer l’émulation tactile : définit le mode d’interaction aux entrées tactiles d’un seul doigt. Les événements à un seul doigt incluent la pression simple, le déplacement et le glissement.  
  
     ![Cible à un doigt du simulateur](../debugger/media/simulator_onefinger.png "SIMULATOR_OneFinger") l’icône de cible unique indique l’emplacement des événements dans le simulateur. Utilisez la souris pour positionner le pointeur.  
  
     ![Cible de tactile à un doigt](../debugger/media/simulator_onefingerengaged.png "SIMULATOR_OneFingerEngaged") appuyez sur le bouton gauche de la souris pour activer le mode tactile. Par exemple, cliquez sur le bouton pour simuler une pression simple, ou appuyez sur la touche et maintenez-la enfoncée pendant un déplacement ou un glissement.  
  
## <a name="pinch-and-zoom"></a>Pincement de deux doigts pour zoomer  
 Définit le mode d'interaction pour utiliser le pincement de deux doigts pour zoomer.  
  
-   ![Cible de deux doigts du simulateur doigt](../debugger/media/simulator_twofinger.png "SIMULATOR_TwoFinger")  
  
     L'icône double cible indique l'emplacement des deux doigts sur l'écran du périphérique.  
  
    -   Déplacez la souris pour positionner les icônes sur l'objet de l'écran du périphérique.  
  
    -   Tournez la molette de la souris vers l'arrière ou vers l'avant pour modifier la distance simulée des deux doigts avant le pincement ou le zoom.  
  
-   -   ![Pincer, zoomer et faire pivoter les cibles](../debugger/media/simulator_twofingerengaged.png "SIMULATOR_TwoFingerEngaged")  
  
         Appuyez sur le bouton gauche et tournez la molette de la souris vers l'arrière (vers vous) pour effectuer un zoom avant (pincement).  
  
    -   Appuyez sur le bouton gauche et tournez la molette de la souris vers l'avant (en s'éloignant de vous) pour effectuer un zoom arrière (zoom).  
  
## <a name="object-rotation"></a>Rotation de l'objet  
 Le bouton **Émulation de tactile : pivoter** définit le mode d’interaction sur les mouvements de rotation à l’aide de deux doigts.  
  
-   -   Déplacez la souris pour positionner les icônes sur l'objet de l'écran du périphérique.  
  
    -   Tournez la molette de la souris vers l'arrière ou vers l'avant pour modifier l'orientation simulée des deux doigts avant de faire pivoter l'objet.  
  
-   -   Appuyez sur le bouton gauche et tournez la molette vers l'arrière (vers vous) pour faire pivoter l'objet dans le sens inverse des aiguilles d'une montre. Lorsque vous tournez la molette de la souris, l'une des deux icônes cibles pivote autour de l'autre pour indiquer la taille relative de la rotation.  
  
    -   Appuyez sur le bouton gauche et tournez la molette de la souris vers l'avant (en s'éloignant de vous) pour faire pivoter l'objet dans le sens des aiguilles d'une montre.  
  
##  <a name="BKMK_Enable_or_disable_Always_on_top_mode"></a> Activer ou désactiver le mode Toujours visible  
 Définissez la fenêtre du simulateur pour qu'elle s'affiche toujours au-dessus des autres fenêtres. Le bouton **Activer/désactiver la fenêtre au premier plan** active ou désactive le mode **Toujours visible** de la fenêtre du simulateur.  
  
##  <a name="BKMK_Change_the_device_orientation"></a> Modifier l'orientation de l'appareil  
 Vous pouvez changer l'orientation du périphérique entre le mode Portrait et Paysage en appliquant au simulateur une rotation de 90 degrés dans n'importe quelle direction.  
  
> [!NOTE]
>  Le simulateur ne respecte pas la propriété [DisplayProperties.AutoRotationPreferences](http://go.microsoft.com/fwlink/?LinkId=249460) d’un projet. Par exemple, si votre projet définit l'orientation sur `Landscape`, et que vous appliquez au simulateur une rotation vers une orientation Portrait, l'image d'affichage du simulateur sera également pivotée et redimensionnée. Testez ces paramètres sur un périphérique réel.  
  
> [!NOTE]
>  Si vous faites pivoter un simulateur et qu'un bord du simulateur est plus grand que l'écran sur lequel il s'affiche, le simulateur est automatiquement redimensionné à la taille de l'écran. Le simulateur n'est pas redimensionné dans sa taille d'origine si vous lui appliquez une nouvelle rotation.  
  
##  <a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a> Modifier la taille et la résolution simulées de l'écran  
 Pour modifier la taille et la résolution simulées de l’écran, sélectionnez le bouton **Modifier la résolution** dans la palette et choisissez une nouvelle taille et résolution dans la liste.  
  
 La taille et la résolution de l'écran sont indiquées en *Largeur écran pouces, largeur pixel X hauteur pixel*. Notez que la taille et la résolution de l'écran sont simulées. Les coordonnées de l'emplacement sur le simulateur sont traduites en coordonnées de la taille et de la résolution du périphérique sélectionnées.  
  
> [!NOTE]
>  Enregistrez les versions mises à l'échelle d'images bitmap dans votre application et Windows chargera l'image appropriée à l'échelle actuelle. Pour plus d’informations, consultez [introduction de conception et de l’interface utilisateur](/windows/uwp/layout/design-and-ui-intro). Toutefois, si vous modifiez la résolution du simulateur pour que Windows sélectionne une image différente en fonction de la résolution, vous devez arrêter et redémarrer la session de débogage pour afficher la nouvelle image.  
  
##  <a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a>Effectuer une capture d’écran de votre application à envoyer au Microsoft Store  
 Quand vous envoyez une application dans Microsoft Store, vous devez inclure des captures d’écran de l’application.  
  
> [!NOTE]
>  La capture d'écran est enregistrée dans la résolution en cours du simulateur. Pour modifier la résolution, cliquez sur le bouton **Modifier la résolution** .  
  
-   Pour créer des captures de votre application à partir du simulateur, cliquez sur le bouton **Copier la capture d'écran** .  
  
-   Pour définir l’emplacement où se trouve les captures d’écran, sélectionnez le bouton **Paramètres de capture d’écran** et sélectionnez l’emplacement dans le menu contextuel.  
  
     ![Menu contextuel des paramètres d’écran](../debugger/media/simulator_screenshotsettingscntxmnu.png "SIMULATOR_ScreenShotSettingsCntxMnu")  
  
##  <a name="BKMK_Simulate_network_connection_properties"></a> Simuler des propriétés de connexion réseau  
 Vous pouvez aider les utilisateurs de votre application gérer le coût des connexions réseau limitées en faisant bien comprendre de connexion données ou Coût plan état modifications de réseau et permettant à votre application d’utiliser ces informations pour éviter de subir des frais supplémentaires pour l’itinérance ou supérieure à un limite de transfert de données spécifié. Le [Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity) API vous permet de répondre aux [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) et [TriggerType](/uwp/api/windows.applicationmodel.background.systemtrigger) les événements qui assurent la connexion. Consultez [Comment gérer les contraintes liées au coût des connexions réseau limitées (HTML)](http://msdn.microsoft.com/library/windows/apps/Hh750310.aspx).  
  
 Pour déboguer ou tester votre code prenant en charge les coûts de réseau, le simulateur peut simuler les propriétés d’un réseau qui sont exposées par le [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) objet retourné par [GetInternetConnectionProfile](/uwp/api/windows.networking.connectivity.networkinformation).
  
 Pour simuler les propriétés d'un réseau :  
  
1.  Dans la barre d’outils du simulateur, choisissez **Modifier les propriétés du réseau** .  
  
2.  Dans la boîte de dialogue **Définir les propriétés du réseau** , sélectionnez **Utiliser les propriétés du réseau simulé**.  
  
     Désactivez la case à cocher pour supprimer la simulation et pour revenir aux propriétés du réseau de l'interface actuellement connectée.  
  
3.  Entrez un nom dans **Nom du profil** pour le réseau simulé. Nous vous recommandons d’utiliser un nom unique que vous pouvez utiliser pour identifier la simulation dans la [ProfileName](/uwp/api/windows.networking.connectivity.connectionprofile) propriété de la [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) objet.  
  
4.  Sélectionnez le [NetworkCostType](/uwp/api/windows.networking.connectivity.networkcosttype) valeur pour le profil à partir de la **Type de coût réseau** liste.  
  
5.  À partir de la **indicateur d’état de limite de données** la liste, vous pouvez définir le [ApproachingDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) propriété ou le [OverDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) sur true, ou vous pouvez choisir  **Sous la limite de données** pour affecter la valeur False.  
  
6.  À partir de la **état d’itinérance** liste, définissez la [itinérance](/uwp/api/windows.networking.connectivity.connectioncost) propriété.  
  
7.  Choisissez **définir les propriétés** pour simuler les propriétés réseau en déclenchant un premier plan [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) événement et un arrière-plan [SystemTrigger](/uwp/api/windows.applicationmodel.background.systemtrigger) de type  **NetworkStateChange**.  
  
 **Pour plus d'informations sur la gestion des connexions réseau**  
  
 [Comment gérer les contraintes liées au coût des connexions réseau limitées (HTML)](http://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)  
  
 [Exemple d’informations réseau](http://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)  
  
 [Analyser l’utilisation de l’énergie](../profiling/analyze-energy-use-in-store-apps.md)  
  
 [Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity)  
  
 [Comment répondre aux événements système avec des tâches en arrière-plan](http://msdn.microsoft.com/en-us/f7c86e86-a7ae-4abb-a923-76b03337a80a)  
  
 [Comment déclencher suspendre, reprendre, événements et d’arrière-plan dans les applications UWP](http://msdn.microsoft.com/library/windows/apps/hh974425.aspx)  
  
##  <a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> Naviguez dans le simulateur à l'aide du clavier  
 Vous pouvez parcourir la barre d’outils du simulateur en appuyant sur **CTRL + ALT + flèche haut** pour déplacer le focus à partir de la fenêtre du simulateur vers la barre d’outils du simulateur. Utilisez **Flèche haut** et **Flèche bas** pour basculer entre les boutons de la barre d'outils.  
  
 Vous pouvez arrêter le simulateur en appuyant sur **CTRL + ALT + F4**.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécuter des applications à partir de Visual Studio](../debugger/run-store-apps-from-visual-studio.md)