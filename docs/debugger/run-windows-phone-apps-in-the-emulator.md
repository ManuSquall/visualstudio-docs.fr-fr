---
title: "Ex&#233;cuter des applications Windows Phone dans l&#39;&#233;mulateur | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
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
ms.assetid: c7590788-beb3-403c-a7dd-18472a9e585e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Ex&#233;cuter des applications Windows Phone dans l&#39;&#233;mulateur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![S'applique uniquement à Windows Phone](../debugger/media/phone_only_content.png "phone\_only\_content")  
  
 L'émulateur Windows Phone est une application de bureau servant à simuler un Windows Phone. L'émulateur fournit un environnement virtualisé dans lequel vous pouvez déboguer et tester des applications Windows Phone sur votre ordinateur, sans l'appareil physique. Vous pouvez simuler des événements tactiles et de rotation courants, et choisir la taille et la résolution de l'écran physique que vous voulez émuler. Vous pouvez également tester plusieurs fonctionnalités couramment utilisées, comme la géolocalisation, la mise en réseau, les notifications, les capteurs, l'accéléromètre et la carte SD en option.  
  
 Pour plus d'informations sur les fonctionnalités que vous pouvez tester dans l'émulateur, consultez [Tester des fonctionnalités d'application dans l'émulateur Windows Phone](http://msdn.microsoft.com/fr-fr/c1b2b0ec-b8cc-4a98-84c1-701428e45cb1).  
  
 Avec Visual Studio, l'émulateur fournit un environnement complet dans lequel vous pouvez concevoir, développer, déboguer et tester des applications Windows Phone.  
  
## Dans cette rubrique  
  
-   [Exécuter une application Windows Phone dans l'émulateur](#BKMK_run)  
  
    -   [Exécuter une application à partir de Visual Studio](#BKMK_vs)  
  
    -   [Exécuter une application avec l'outil Déploiement de l'application](#BKMK_depltool)  
  
-   [Configurer l'émulateur Windows Phone avec la barre d'outils de l'émulateur](#BKMK_toolbar)  
  
-   [Utiliser les boutons physiques simulés dans l'émulateur](#BKMK_buttons)  
  
-   [Utiliser le clavier de l'ordinateur avec l'émulateur](#BKMK_tasks_kbd)  
  
-   [Enregistrer et charger des points de vérification personnalisés](#BKMK_checkpoints)  
  
-   [Créer des captures d'écran dans l'émulateur](#BKMK_tasks_shot)  
  
##  <a name="BKMK_run"></a> Exécuter une application Windows Phone dans l'émulateur  
 Quand vous développez une application Windows Phone, vous pouvez utiliser l'émulateur Windows Phone pour déployer et tester rapidement votre application. Nous vous conseillons toutefois de tester votre application sur un appareil Windows Phone réel avant de publier votre application dans le Windows Phone Store. Vous pouvez ainsi parcourir votre application tel que le feront les utilisateurs.  
  
 Quand vous exécutez une application Windows Phone pour la première fois dans l'émulateur Windows Phone, les événements suivants se produisent :  
  
1.  L'émulateur démarre.  
  
2.  L'émulateur charge le système d'exploitation Windows Phone.  
  
3.  L'émulateur affiche l'écran d'accueil Windows Phone.  
  
4.  Votre application est déployée dans l'émulateur.  
  
5.  Votre application s'exécute dans l'émulateur.  
  
 Si l'émulateur sélectionné est déjà en cours d'exécution, votre application est déployée et démarrée dans l'émulateur en cours d'exécution. Une seule instance de chaque émulateur peut être exécutée à la fois.  
  
> [!TIP]
>  Quand vous testez votre application dans l'émulateur, laissez\-le ouvert entre les sessions de débogage pour pouvoir réexécuter votre application rapidement.  
  
###  <a name="BKMK_vs"></a> Exécuter une application à partir de Visual Studio  
  
##### Pour déployer et exécuter une application à partir de Visual Studio  
  
1.  Dans Visual Studio, ouvrez un projet Windows Phone.  
  
2.  Dans la barre d'outils **Standard**, sélectionnez l'une des options d'émulateur.  
  
     ![Liste des images de l'émulateur Windows Phone](../cross-platform/media/wp_emulator_list.png "WP\_Emulator\_list")  
  
3.  Pour déployer et exécuter votre application avec le débogage, dans le menu **Déboguer**, cliquez sur **Démarrer le débogage** ou appuyez sur F5.  
  
     Pour déployer et exécuter votre application sans débogage, dans le menu **Déboguer**, cliquez sur **Démarrer sans débogage** ou appuyez sur Ctrl\+F5.  
  
     Votre application est déployée et démarrée.  
  
     Pour déployer votre application sans l'exécuter, dans le menu **Générer**, cliquez sur **Déployer la solution**.  
  
##### Pour arrêter une application en cours d'exécution  
  
-   Pour arrêter une application en cours d'exécution, effectuez l'une des opérations suivantes :  
  
    -   Dans Visual Studio, dans le menu **Déboguer**, cliquez sur **Arrêter le débogage** ou appuyez sur Maj\+F5.  
  
    -   Dans l'émulateur, appuyez sur le bouton **Précédent** pour quitter l'application. Si la page active de l'application n'était pas la page de démarrage de l'application, vous devrez peut\-être appuyer plusieurs fois sur le bouton **Précédent**.  
  
     L'application se ferme et l'écran de démarrage apparaît. Cette étape met fin à la session de débogage active.  
  
##### Pour redémarrer une application sans débogage  
  
1.  Dans l'émulateur, dans l'écran de démarrage, balayez vers la gauche pour afficher la liste d'applications.  
  
2.  Dans la liste d'applications, appuyez sur l'icône de l'application. L'application redémarre sans débogage.  
  
##### Pour désactiver une application en cours d'exécution  
  
1.  Avant d'exécuter votre application, dans Visual Studio, cliquez avec le bouton droit sur le projet dans l'Explorateur de solutions, puis sélectionnez **Propriétés** pour ouvrir le **Concepteur de projets**.  
  
2.  Dans le **Concepteur de projets**, dans la page **Déboguer**, laissez la case **Tombstone sur désactivation lors du débogage** décochée si vous voulez que l'application bascule à l'état dormant une fois désactivée. Cochez la case si vous voulez que l'application soit complètement désactivée.  
  
3.  Dans le menu **Déboguer**, cliquez sur **Démarrer le débogage** ou appuyez sur F5 pour exécuter l'application.  
  
4.  Dans l'émulateur, appuyez sur le bouton **Démarrer**. L'écran de démarrage apparaît et l'application est désactivée. L'application passe à l'état dormant ou est désactivée, selon le paramétrage de la case à cocher **Tombstone sur désactivation lors du débogage**.  
  
##### Pour réactiver une application dormante ou désactivée  
  
-   Dans l'émulateur, appuyez sur le bouton **Précédent** pour revenir à l'application. Si vous avez navigué vers d'autres pages ou ouvert une autre application, vous devrez peut\-être appuyer plusieurs fois sur le bouton **Précédent** pour réactiver l'application.  
  
     La session de débogage reprend. Si le débogueur a été détaché de l'application, vous devrez peut\-être appuyer sur F5 pour reprendre la session de débogage.  
  
###  <a name="BKMK_depltool"></a> Exécuter une application avec l'outil Déploiement de l'application  
 Vous pouvez également utiliser l'outil Déploiement de l'application de Windows Phone \(**AppDeploy.exe**\) pour exécuter votre application dans l'émulateur. Cet outil est une application autonome installée avec les outils de développement Windows Phone.  
  
 Pour plus d'informations, consultez [Déployer des applications Windows Phone 8.1 avec l'outil de déploiement de l'application](../Topic/Deploy%20Windows%20Phone%208.1%20apps%20with%20the%20Application%20Deployment%20tool.md).  
  
##  <a name="BKMK_toolbar"></a> Configurer l'émulateur Windows Phone avec la barre d'outils de l'émulateur  
 La capture d'écran suivante montre les boutons de configuration disponibles dans la barre d'outils de l'émulateur.  
  
 f21574ab-5970-4b7a-9281-c13073bf6767  
  
|Boutons de la barre d'outils|Options de configuration|  
|----------------------------------|------------------------------|  
|![Options d'entrée dans la barre d'outils de l'émulateur Windows Phone](../debugger/media/wp_emulator_.png "WP\_Emulator\_")|**Configurer la saisie à un seul point ou multipoint**<br /><br /> Quand vous activez la saisie multipoint, vous pouvez cliquer avec le bouton droit pour déplacer les points tactiles sans toucher l'écran. Vous pouvez ensuite cliquer avec le bouton gauche pour déplacer les deux points tactiles simultanément.|  
|![Orientation dans la barre d'outils de l'émulateur Windows Phone](../debugger/media/wp_emulator_rotation.png "WP\_Emulator\_rotation")|**Configurer l'orientation de l'émulateur**<br /><br /> Vous pouvez choisir parmi trois orientations possibles pour l'émulateur Windows Phone : portrait, paysage gauche ou paysage droite. La taille de l'émulateur ne change pas quand vous modifiez l'orientation.<br /><br /> Pour modifier l'orientation, cliquez sur le bouton **Faire pivoter à gauche** ou **Faire pivoter à droite**.|  
|![Options de taille dans la barre d'outils de l'émulateur Windows Phone](../debugger/media/wp_emulator_size.png "WP\_Emulator\_size")|**Configurer la taille de l'émulateur**<br /><br /> Vous pouvez modifier la taille de l'émulateur sur l'écran de l'ordinateur hôte. La taille en points par pouce \(PPP\) de l'émulateur est basée sur celle du moniteur hôte, indépendamment de la valeur du zoom.<br /><br /> -   Pour adapter l'émulateur à la taille de l'écran, cliquez sur le bouton **Adapter à l'écran**.<br />-   Pour modifier le paramètre du zoom, cliquez sur le bouton **Zoom**. La boîte de dialogue **Zoom** s'ouvre. Dans la boîte de dialogue **Zoom**, entrez une valeur de zoom comprise entre 33 et 100.|  
  
##  <a name="BKMK_buttons"></a> Utiliser les boutons physiques simulés dans l'émulateur  
 Simulez l'utilisation des boutons physiques d'un téléphone à l'aide des boutons physiques simulés situés à droite de l'écran de l'émulateur.  
  
-   Cliquez sur le bouton **Marche\/Arrêt** pour simuler l'activation et la désactivation de l'affichage. Cliquez sur le bouton et maintenez\-le enfoncé pour simuler la désactivation du téléphone.  
  
-   Cliquez sur les boutons **Monter le volume** ou **Baisser le volume** pour simuler la modification du volume des haut\-parleurs du téléphone pour les appels et les notifications.  
  
-   Le bouton **Caméra** lance l'application Caméra. Vous pouvez simuler la prise de photo ou de vidéo à l'aide des commandes de l'application Caméra.  
  
 La capture d'écran suivante montre les boutons physiques simulés.  
  
1.  L'image de gauche affiche l'écran de démarrage sur l'émulateur.  
  
2.  L'image du milieu affiche l'émulateur après une pression sur le bouton **Marche\/Arrêt** pour éteindre l'affichage.  
  
3.  L'image de droite affiche l'écran de l'émulateur après une pression sur le bouton **Monter le volume** pour augmenter le volume.  
  
 ![Boutons de l'émulateur Windows Phone](../debugger/media/wp_emulator_buttons.png "WP\_Emulator\_buttons")  
  
##  <a name="BKMK_tasks_kbd"></a> Utiliser le clavier de l'ordinateur avec l'émulateur  
 L'émulateur prend en charge le mappage du clavier physique de votre ordinateur de développement au clavier d'un Windows Phone. Le comportement des touches est le même que sur un appareil Windows Phone.  
  
 Par défaut, le clavier physique n'est pas activé. Cette implémentation équivaut à un clavier coulissant devant être déployé avant de pouvoir être utilisé. Avant l'activation du clavier physique, l'émulateur accepte uniquement l'entrée au clavier à partir des touches de commande.  
  
 Les caractères spéciaux du clavier d'une version localisée d'un ordinateur Windows de développement ne sont pas pris en charge par l'émulateur. Pour entrer des caractères spéciaux figurant sur un clavier localisé, utilisez plutôt le panneau de saisie.  
  
#### Pour utiliser le clavier de votre ordinateur dans l'émulateur  
  
-   Appuyez sur la touche Page précédente.  
  
     \- ou \-  
  
-   Appuyez sur la touche Pause\/Attn.  
  
#### Pour arrêter d'utiliser le clavier physique de votre ordinateur dans l'émulateur  
  
-   Appuyez sur la touche Page suivante.  
  
     \- ou \-  
  
-   Appuyez sur la touche Pause\/Attn.  
  
 Le tableau suivant indique les touches du clavier physique que vous pouvez utiliser pour émuler les boutons et autres contrôles d'un appareil Windows Phone.  
  
|Touche physique de l'ordinateur|Bouton matériel Windows Phone|Remarques|  
|-------------------------------------|-----------------------------------|---------------|  
|F1|RETOUR|Les appuis longs fonctionnent comme prévu.|  
|F2|DÉMARRER|Les appuis longs fonctionnent comme prévu.|  
|F3|RECHERCHER||  
|F4|Non applicable.||  
|F5|Non applicable.||  
|F6|CAMÉRA \- MOITIÉ|Bouton dédié à la caméra qui est enfoncé à moitié.|  
|F7|CAMÉRA \- ENTIER|Bouton dédié à la caméra.|  
|F8|Non applicable.||  
|F9|MONTER LE VOLUME||  
|F10|BAISSER LE VOLUME||  
|F11|Non applicable.||  
|F12|MARCHE\/ARRÊT|Appuyez sur la touche F12 deux fois pour activer l'écran de verrouillage.<br /><br /> Les appuis longs fonctionnent comme prévu.|  
|ÉCHAP|RETOUR|Les appuis longs fonctionnent comme prévu.|  
|PAUSE\/ATTN|Activer\/désactiver le clavier|Active\/désactive le clavier physique.|  
|PAGE PRÉCÉDENTE|Clavier précédent|Active le clavier physique.|  
|PAGE SUIVANTE|Clavier suivant|Désactive le clavier physique.|  
  
##  <a name="BKMK_checkpoints"></a> Enregistrer et charger des points de vérification personnalisés  
 Enregistrez un instantané de l'état de l'émulateur à l'aide de l'onglet **Points de vérification** des **Outils supplémentaires** de l'émulateur. Cette fonctionnalité est utile si vous testez fréquemment votre application avec les mêmes données et paramètres.  
  
 Par exemple, si votre application nécessite plusieurs contacts, vous pouvez créer les enregistrements de contact une fois et enregistrer un instantané de l'émulateur. Sinon, vous devez recréer les enregistrements de contact chaque fois que vous démarrez l'émulateur.  
  
-   Cliquez sur **Nouveau point de vérification** pour capturer un nouvel instantané de l'état de l'émulateur avec les données et les paramètres nécessaires pour retester votre application plus tard. Le nouveau point de contrôle est ajouté à la liste **Points de contrôle**.  
  
     Vous ne pouvez pas capturer un point de contrôle si le débogueur est attaché à l'émulateur.  
  
-   Sélectionnez un point de contrôle dans la liste **Points de contrôle** pour afficher les informations correspondantes.  
  
-   Sélectionnez la case d'option dans la colonne **Par défaut** pour que le point de contrôle enregistré devienne l'option par défaut pour l'émulateur actif.  
  
-   Cliquez sur **Restaurer** pour redémarrer le système d'exploitation Windows Phone sur l'émulateur et charger l'instantané sélectionné.  
  
-   Cliquez sur **Supprimer** pour supprimer un instantané dont vous n'avez plus besoin.  
  
 L'image d'origine de l'émulateur apparaît toujours en premier dans la liste **Points de contrôle** et ne peut pas être modifiée ou supprimée. Toutefois, vous pouvez sélectionner un autre instantané comme image par défaut de l'émulateur.  
  
 ![Onglet Points de contrôle de l'émulateur Windows Phone](../debugger/media/wp_emulator_checkpoints.png "WP\_Emulator\_checkpoints")  
  
##  <a name="BKMK_tasks_shot"></a> Créer des captures d'écran dans l'émulateur  
 Vous pouvez créer des captures d'écran de vos applications Windows Phone à l'aide de l'outil de capture d'écran de la fenêtre Outils supplémentaires. L'outil crée des fichiers PNG dans la même résolution que celle de l'émulateur en cours d'exécution.  
  
 ![Captures d'écran de l'émulateur Windows Phone](../debugger/media/wp_emulator_screenshots.png "WP\_Emulator\_screenshots")  
  
#### Pour créer une capture d'écran d'application à l'aide de l'outil de capture d'écran intégré à l'émulateur  
  
1.  Pour optimiser la qualité de vos captures d'écran, définissez le niveau de zoom de l'émulateur sur 100 %. Plus le niveau de zoom est élevé, plus la qualité de la capture d'écran est élevée.  
  
2.  Démarrez votre application dans l'émulateur.  
  
3.  Dans la barre d'outils de l'émulateur, cliquez sur le bouton Développer pour ouvrir la fenêtre **Outils supplémentaires**.  
  
4.  Cliquez sur l'onglet **Capture d'écran**.  
  
5.  Quand votre application est prête, cliquez sur le bouton **Capturer**.  
  
     La capture d'écran apparaît dans l'espace de travail.  
  
6.  Cliquez sur le bouton **Enregistrer** pour ouvrir la boîte de dialogue **Enregistrer sous**.  
  
7.  Choisissez l'emplacement et le **Nom de fichier** souhaités, puis cliquez sur **Enregistrer**.  
  
8.  Vous pouvez aussi accéder à d'autres pages de votre application et créer d'autres captures d'écran.  
  
9. Lancez un émulateur avec une résolution d'écran différente pour créer les mêmes captures d'écran avec différentes résolutions. Si vous avez exécuté votre application avec débogage, vous devez arrêter le débogage avant de pouvoir la réexécuter sur un autre émulateur.  
  
 Désactivez les compteurs de fréquence des trames sur l'écran de l'émulateur avant de créer des captures d'écran destinées au Windows Phone Store.  
  
#### Pour désactiver les compteurs de fréquence des trames dans l'émulateur avant de créer des captures d'écran  
  
-   Spécifiez une version Release dans Visual Studio. Après avoir spécifié une version Release, lancez votre application en sélectionnant le lien **Déployer *\[nom de l'application\]*** dans le menu **Générer**.  
  
-   Vous pouvez aussi insérer un commentaire sur la ligne de code dans le fichier app.xaml.cs ou app.xaml.vb qui définit la valeur de `EnableFrameRateCounter` sur `true`.