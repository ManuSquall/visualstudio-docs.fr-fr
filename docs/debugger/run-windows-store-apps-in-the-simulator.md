---
title: "Ex&#233;cuter des applications du Windows&#160;Store dans le simulateur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
caps.latest.revision: 42
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 42
---
# Ex&#233;cuter des applications du Windows&#160;Store dans le simulateur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le simulateur Visual Studio pour les applications Windows Store est une application de bureau qui simule une application Windows Store. Vous pouvez exécuter des applications et simuler les événements tactiles et de rotation courants sur votre ordinateur de développement. Vous pouvez également choisir la taille d’écran et la résolution physiques que vous souhaitez émuler et simuler les propriétés de connexion réseau.  
  
 Le simulateur fournit un environnement dans lequel vous pouvez concevoir, développer, déboguer et tester des applications du Windows Store. Toutefois, avant de publier votre application sur le Windows Store, vous devez la tester sur un appareil réel.  
  
 Le simulateur Visual Studio pour les applications Windows Store ne fonctionne pas dans un environnement isolé sur votre ordinateur local. Par conséquent, les erreurs qui se produisent dans un simulateur, tel qu'une erreur irrécupérable à l'échelle du système, peuvent également affecter l'ordinateur entier.  
  
 Pour plus d'informations sur le Windows Phone, voir [Exécuter des applications Windows Phone dans l'émulateur](../debugger/run-windows-phone-apps-in-the-emulator.md).  
  
> [!IMPORTANT]
>  Le simulateur Visual Studio 2015 n’inclut pas le bouton de géolocalisation. En effet, le simulateur Windows 10 n’inclut pas la simulation de géolocalisation. Si vous devez effectuer ce type de simulation, vous pouvez utiliser le simulateur Visual Studio 2013 sur des systèmes d’exploitation Windows 8.1 ou antérieurs.  
  
##  <a name="BKMK_Set_the_simulator_as_the_target"></a> Définir un simulateur comme cible  
 Pour exécuter votre application Windows Store dans le simulateur, sélectionnez **Simulateur** dans la liste déroulante située en regard du bouton **Démarrer le débogage** de la barre d'outils **Standard** du débogueur.  
  
 ![Exécution dans le simulateur](../debugger/media/vsrun_f5_simulator.png "VSRUN\_F5\_Simulator")  
  
##  <a name="BKMK_Choose_an_interaction_mode"></a> Choisir un mode d'interaction  
 Vous avez le choix entre les modes d’interaction suivants  
  
-   ![Bouton de mode de la souris](~/docs/debugger/media/simulator_mousemodebtn.png "SIMULATOR\_MouseModeBtn") Mode de la souris : définit le mode d’interaction sur les mouvements de la souris. Les mouvements de souris incluent les clics, les double\-clics et le déplacement d'objets par glissement.  
  
-   ![Bouton de démarrage de l'émulation tactile](~/docs/debugger/media/simulator_starttouchemulationbtn.png "SIMULATOR\_StartTouchEmulationBtn") Démarrer l’émulation tactile : définit le mode d’interaction sur les mouvements tactiles à l’aide d’un seul doigt. Les événements à un seul doigt incluent la pression simple, le déplacement et le glissement.  
  
     ![Simulator one finger target](../debugger/media/simulator_onefinger.png "SIMULATOR\_OneFinger") L’icône de cible unique indique l’emplacement des événements dans le simulateur. Utilisez la souris pour positionner le pointeur.  
  
     ![One finger touch target](../debugger/media/simulator_onefingerengaged.png "SIMULATOR\_OneFingerEngaged") Appuyez sur le bouton gauche de la souris pour activer le mode tactile. Par exemple, cliquez sur le bouton pour simuler une pression simple, ou appuyez sur la touche et maintenez\-la enfoncée pendant un déplacement ou un glissement.  
  
## Pincement de deux doigts pour zoomer  
 Définit le mode d'interaction pour utiliser le pincement de deux doigts pour zoomer.  
  
-   ![Siimulator two finger target](~/docs/debugger/media/simulator_twofinger.png "SIMULATOR\_TwoFinger")  
  
     L'icône double cible indique l'emplacement des deux doigts sur l'écran du périphérique.  
  
    -   Déplacez la souris pour positionner les icônes sur l'objet de l'écran du périphérique.  
  
    -   Tournez la molette de la souris vers l'arrière ou vers l'avant pour modifier la distance simulée des deux doigts avant le pincement ou le zoom.  
  
-   -   ![Pinch, zoom, and rotate targets](../debugger/media/simulator_twofingerengaged.png "SIMULATOR\_TwoFingerEngaged")  
  
         Appuyez sur le bouton gauche et tournez la molette de la souris vers l'arrière \(vers vous\) pour effectuer un zoom avant \(pincement\).  
  
    -   Appuyez sur le bouton gauche et tournez la molette de la souris vers l'avant \(en s'éloignant de vous\) pour effectuer un zoom arrière \(zoom\).  
  
## Rotation de l'objet  
 Le bouton **Émulation de tactile : pivoter** définit le mode d’interaction sur les mouvements de rotation à l’aide de deux doigts.  
  
-   -   Déplacez la souris pour positionner les icônes sur l'objet de l'écran du périphérique.  
  
    -   Tournez la molette de la souris vers l'arrière ou vers l'avant pour modifier l'orientation simulée des deux doigts avant de faire pivoter l'objet.  
  
-   -   Appuyez sur le bouton gauche et tournez la molette vers l'arrière \(vers vous\) pour faire pivoter l'objet dans le sens inverse des aiguilles d'une montre. Lorsque vous tournez la molette de la souris, l'une des deux icônes cibles pivote autour de l'autre pour indiquer la taille relative de la rotation.  
  
    -   Appuyez sur le bouton gauche et tournez la molette de la souris vers l'avant \(en s'éloignant de vous\) pour faire pivoter l'objet dans le sens des aiguilles d'une montre.  
  
##  <a name="BKMK_Enable_or_disable_Always_on_top_mode"></a> Activer ou désactiver le mode Toujours visible  
 Définissez la fenêtre du simulateur pour qu'elle s'affiche toujours au\-dessus des autres fenêtres. Le bouton **Activer\/désactiver la fenêtre au premier plan** active ou désactive le mode **Toujours visible** de la fenêtre du simulateur.  
  
##  <a name="BKMK_Change_the_device_orientation"></a> Modifier l'orientation de l'appareil  
 Vous pouvez changer l'orientation du périphérique entre le mode Portrait et Paysage en appliquant au simulateur une rotation de 90 degrés dans n'importe quelle direction.  
  
> [!NOTE]
>  Le simulateur ne respecte pas la propriété [DisplayProperties.AutoRotationPreferences](http://go.microsoft.com/fwlink/?LinkId=249460) d’un projet. Par exemple, si votre projet définit l'orientation sur `Landscape`, et que vous appliquez au simulateur une rotation vers une orientation Portrait, l'image d'affichage du simulateur sera également pivotée et redimensionnée. Testez ces paramètres sur un périphérique réel.  
  
> [!NOTE]
>  Si vous faites pivoter un simulateur et qu'un bord du simulateur est plus grand que l'écran sur lequel il s'affiche, le simulateur est automatiquement redimensionné à la taille de l'écran. Le simulateur n'est pas redimensionné dans sa taille d'origine si vous lui appliquez une nouvelle rotation.  
  
##  <a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a> Modifier la taille et la résolution simulées de l'écran  
 Pour modifier la taille et la résolution simulées de l’écran, sélectionnez le bouton **Modifier la résolution** dans la palette et choisissez une nouvelle taille et résolution dans la liste.  
  
 La taille et la résolution de l'écran sont indiquées en *Largeur écran pouces, largeur pixel X hauteur pixel*. Notez que la taille et la résolution de l'écran sont simulées. Les coordonnées de l'emplacement sur le simulateur sont traduites en coordonnées de la taille et de la résolution du périphérique sélectionnées.  
  
> [!NOTE]
>  Enregistrez les versions mises à l'échelle d'images bitmap dans votre application et Windows chargera l'image appropriée à l'échelle actuelle. Pour plus d’informations, consultez [Conception dynamique \(101\) des applications de plateforme Windows universelle \(UWP\)](https://msdn.microsoft.com/en-us/library/windows/apps/dn958435.aspx). Toutefois, si vous modifiez la résolution du simulateur pour que Windows sélectionne une image différente en fonction de la résolution, vous devez arrêter et redémarrer la session de débogage pour afficher la nouvelle image.  
  
##  <a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a> Capturer un écran de votre application à envoyer au Windows Store  
 Quand vous envoyez une application au Windows Store, vous devez inclure des captures d’écran de l’application.  
  
> [!NOTE]
>  La capture d'écran est enregistrée dans la résolution en cours du simulateur. Pour modifier la résolution, cliquez sur le bouton **Modifier la résolution**.  
  
-   Pour créer des captures de votre application à partir du simulateur, cliquez sur le bouton **Copier la capture d'écran**.  
  
-   Pour définir l’emplacement où se trouve les captures d’écran, sélectionnez le bouton **Paramètres de capture d’écran** et sélectionnez l’emplacement dans le menu contextuel.  
  
     ![Menu contextuel des paramètres de capture d’écran](~/docs/debugger/media/simulator_screenshotsettingscntxmnu.png "SIMULATOR\_ScreenShotSettingsCntxMnu")  
  
##  <a name="BKMK_Simulate_network_connection_properties"></a> Simuler des propriétés de connexion réseau  
 Vous pouvez aider les utilisateurs de votre application à gérer le coût des connexions réseau limitées en faisant bien comprendre le coût des connexions réseau ou les modifications de l'état du forfait données et en permettant à votre application d'utiliser ces informations pour éviter de subir des frais d'itinérance supplémentaires ou de dépasser la limite de transfert de données spécifiée. Les API [Windows.Networking.Connectivity](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.aspx) vous permettent de répondre aux événements [NetworkStatusChanged](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx) et [TriggerType](https://msdn.microsoft.com/en-us/library/windows/apps/windows.applicationmodel.background.systemtrigger.triggertype.aspx) qui assurent la connexion. Consultez [Comment gérer les contraintes liées au coût des connexions réseau limitées \(HTML\)](http://msdn.microsoft.com/library/windows/apps/Hh750310.aspx).  
  
 Pour déboguer ou tester votre code réseau sensible au coût, le simulateur peut simuler les propriétés d’un réseau qui sont exposées par l’objet [ConnectionProfile](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx) retourné par [GetInternetConnectionProfile](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.networkinformation.getinternetconnectionprofile.aspx).  
  
 Pour simuler les propriétés d'un réseau :  
  
1.  Dans la barre d’outils du simulateur, choisissez **Modifier les propriétés du réseau**.  
  
2.  Dans la boîte de dialogue **Définir les propriétés du réseau**, sélectionnez **Utiliser les propriétés du réseau simulé**.  
  
     Désactivez la case à cocher pour supprimer la simulation et pour revenir aux propriétés du réseau de l'interface actuellement connectée.  
  
3.  Entrez un nom dans **Nom du profil** pour le réseau simulé. Nous vous recommandons d’utiliser un nom unique que vous pouvez utiliser pour identifier la simulation dans la propriété [ProfileName](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.connectionprofile.profilename.aspx) de l’objet [ConnectionProfile](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx).  
  
4.  Sélectionnez la valeur [NetworkCostType](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.networkcosttype.aspx) du profil dans la liste **Type de coût réseau**.  
  
5.  Dans la liste **Indicateur d’état de limite de données**, vous pouvez affectez la valeur true à la propriété [ApproachingDataLimit](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.connectioncost.approachingdatalimit.aspx) ou [OverDataLimit](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.connectioncost.overdatalimit.aspx) ou choisir **En deçà de la limite de données** pour affecter la valeur false aux deux propriétés.  
  
6.  Dans la liste **État d’itinérance**, définissez la propriété [Roaming](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.connectioncost.roaming.aspx).  
  
7.  Choisissez **Définir les propriétés** pour simuler les propriétés réseau en déclenchant un événement [NetworkStatusChanged](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx) de premier plan et un événement [SystemTrigger](https://msdn.microsoft.com/en-us/library/windows/apps/windows.applicationmodel.background.systemtrigger.aspx) d’arrière\-plan de type **NetworkStateChange**.  
  
 **Pour plus d'informations sur la gestion des connexions réseau**  
  
 [Comment gérer les contraintes liées au coût des connexions réseau limitées \(HTML\)](http://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)  
  
 [Exemple d’informations réseau](http://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)  
  
 [Analyser l'utilisation de l'énergie](../profiling/analyze-energy-use-in-store-apps.md)  
  
 [Windows.Networking.Connectivity](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.aspx)  
  
 [Comment répondre aux événements système avec des tâches en arrière\-plan](http://msdn.microsoft.com/fr-fr/f7c86e86-a7ae-4abb-a923-76b03337a80a)  
  
 [Comment déclencher des événements d’interruption, de reprise et d’arrière\-plan dans les applications du Windows Store.](http://msdn.microsoft.com/library/windows/apps/hh974425.aspx)  
  
##  <a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> Naviguez dans le simulateur à l'aide du clavier  
 Vous pouvez parcourir la barre d’outils du simulateur en appuyant sur **Ctrl\+Alt\+Flèche haut** pour déplacer le focus de la fenêtre du simulateur sur la barre d’outils du simulateur. Utilisez **Flèche haut** et **Flèche bas** pour basculer entre les boutons de la barre d'outils.  
  
 Vous pouvez arrêter le simulateur en appuyant sur **Ctrl\+Alt\+F4**.  
  
## Voir aussi  
 [Exécuter des applications à partir de Visual Studio](../debugger/run-store-apps-from-visual-studio.md)