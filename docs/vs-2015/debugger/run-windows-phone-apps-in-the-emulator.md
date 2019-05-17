---
title: Exécuter des applications de Windows Phone dans l’émulateur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c7590788-beb3-403c-a7dd-18472a9e585e
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5673ebf28cc652e3bcd973808db87b5bb058659c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65683524"
---
# <a name="run-windows-phone-apps-in-the-emulator"></a>Exécuter des applications Windows Phone dans l'émulateur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'émulateur Windows Phone fournit un environnement virtualisé dans lequel vous pouvez déboguer et tester des applications Windows Phone sur votre ordinateur, sans appareil physique. Vous pouvez simuler des événements tactiles et de rotation courants, et choisir la taille et la résolution de l'écran physique que vous voulez émuler. Vous pouvez également tester plusieurs fonctionnalités couramment utilisées, comme la géolocalisation, la mise en réseau, les notifications, les capteurs, l’accéléromètre et la carte SD en option.  
  
 Pour plus d’informations sur les fonctionnalités que vous pouvez tester dans l’émulateur, consultez [tester les fonctionnalités de l’application dans l’émulateur de Windows Phone](https://msdn.microsoft.com/c1b2b0ec-b8cc-4a98-84c1-701428e45cb1).  
  
 Avec Visual Studio, l'émulateur fournit un environnement complet dans lequel vous pouvez concevoir, développer, déboguer et tester des applications Windows Phone.  
  
## <a name="BKMK_run"></a> Exécuter une application Windows Phone dans l’émulateur  
 Quand vous développez une application Windows Phone, vous pouvez utiliser l'émulateur Windows Phone pour déployer et tester rapidement votre application. Nous vous conseillons toutefois de tester votre application sur un appareil Windows Phone réel avant de publier votre application dans le Windows Phone Store. Vous pouvez ainsi parcourir votre application tel que le feront les utilisateurs.  
  
 Quand vous exécutez une application Windows Phone pour la première fois dans l'émulateur Windows Phone, les événements suivants se produisent :  
  
1. L’émulateur démarre.  
  
2. L'émulateur charge le système d'exploitation Windows Phone.  
  
3. L'émulateur affiche l'écran d'accueil Windows Phone.  
  
4. Votre application est déployée dans l'émulateur.  
  
5. Votre application s'exécute dans l'émulateur.  
  
   Si l'émulateur sélectionné est déjà en cours d'exécution, votre application est déployée et démarrée dans l'émulateur en exécution. Une seule instance de chaque émulateur peut être exécutée à la fois.  
  
> [!TIP]
> Quand vous testez votre application dans l'émulateur, laissez l'émulateur ouvert entre les sessions de débogage pour pouvoir réexécuter votre application rapidement.  
  
### <a name="BKMK_vs"></a> Exécuter une application à partir de Visual Studio  
  
##### <a name="to-deploy-and-run-an-app-from-visual-studio"></a>Pour déployer et exécuter une application à partir de Visual Studio  
  
1. Dans Visual Studio, ouvrez un projet Windows Phone.  
  
2. Sur le **Standard** barre d’outils, sélectionnez une des options d’émulateur.  
  
     ![Liste d’images d’émulateur de Windows Phone](../debugger/media/wp-emulator-list.png "WP_Emulator_list")  
  
3. Pour déployer et exécuter votre application avec débogage, dans le **déboguer** menu, cliquez sur **démarrer le débogage**, ou appuyez sur F5.  
  
     Pour déployer et exécuter votre application sans débogage, dans le **déboguer** menu, cliquez sur **démarrer sans débogage**, ou appuyez sur Ctrl + F5.  
  
     Votre application est déployée et démarrée.  
  
     Pour déployer votre application sans l’exécuter, dans le **Build** menu, cliquez sur **déployer la Solution**.  
  
##### <a name="to-stop-a-running-app"></a>Pour arrêter une application en cours d'exécution  
  
- Pour arrêter une application en cours d'exécution, effectuez l'une des opérations suivantes :  
  
  - Dans Visual Studio, sur le **déboguer** menu, cliquez sur **arrêter le débogage**, ou appuyez sur MAJ + F5.  
  
  - Dans l’émulateur, appuyez sur la **retour** bouton pour quitter l’application. Si la page active de l’application n’était pas page de démarrage de l’application, vous devrez peut-être appuyer sur le **retour** bouton plusieurs fois.  
  
    L'application se ferme et l'écran de démarrage s'ouvre. Cette étape termine la session active de débogage.  
  
##### <a name="to-restart-an-app-without-debugging"></a>Pour redémarrer une application sans débogage  
  
1. Dans l'émulateur, dans l'écran de démarrage, balayez vers la gauche pour afficher la liste d'applications.  
  
2. Dans la liste d'applications, appuyez sur l'icône de l'application. L'application redémarre sans débogage.  
  
##### <a name="to-deactivate-a-running-app"></a>Pour désactiver une application en cours d'exécution  
  
1. Avant d’exécuter votre application, dans Visual Studio, cliquez sur le projet dans l’Explorateur de solutions, puis sélectionnez **propriétés** pour ouvrir **Concepteur de projet**.  
  
2. Dans **Concepteur de projets**, dans le **déboguer** page, laissez le **Tombstone sur désactivation lors du débogage** case décochée si vous voulez que l’application dans un état dormant état lorsque désactivé. Cochez la case si vous voulez que l'application soit complètement désactivée.  
  
3. Sur le **déboguer** menu, cliquez sur **démarrer le débogage**, ou appuyez sur F5 pour exécuter l’application.  
  
4. Dans l’émulateur, appuyez sur la **Démarrer** bouton. L'écran de démarrage apparaît et l'application est désactivée. L’application passe à l’état dormant ou est désactivée, selon le paramètre de la **Tombstone sur désactivation lors du débogage** case à cocher.  
  
##### <a name="to-reactivate-a-dormant-or-tombstoned-app"></a>Pour réactiver une application dormante ou désactivée  
  
- Dans l’émulateur, appuyez sur la **retour** bouton pour revenir à l’application. Si vous navigué vers d’autres pages ou ouvert une autre application, vous devrez peut-être appuyer sur le **retour** bouton plusieurs fois pour réactiver l’application.  
  
     La session de débogage reprend. Si le débogueur a été détaché de l'application, vous devrez peut-être appuyer sur F5 pour reprendre la session de débogage.  
  
### <a name="BKMK_depltool"></a> Exécuter une application avec l’outil de déploiement d’Application  
 Vous pouvez également utiliser l’outil de déploiement d’applications Windows Phone (**AppDeploy.exe**) pour exécuter votre application dans l’émulateur. Cet outil est une application autonome installée avec les outils de développement Windows Phone.  
  
 Pour plus d’informations, consultez [des applications de déployer Windows Phone 8.1 avec l’outil de déploiement d’applications](https://msdn.microsoft.com/library/23700f82-1399-44d9-bc0c-714be4a48ee6).  
  
## <a name="BKMK_toolbar"></a> Configurer l’émulateur Windows Phone avec la barre d’outils de l’émulateur  
 Ce tableau montre les boutons de configuration disponibles dans la barre d'outils de l'émulateur.  
  
|Boutons de la barre d'outils|Options de configuration|  
|---------------------|---------------------------|  
|![Options de barre d’outils de l’émulateur de Windows Phone d’entrée](../debugger/media/wp-emulator.png "WP_Emulator_")|**Configurer l’entrée seul point ou multipoint**<br /><br /> Quand vous activez la saisie multipoint, vous pouvez cliquer avec le bouton droit pour déplacer les points tactiles sans toucher l'écran. Vous pouvez ensuite cliquer avec le bouton gauche pour déplacer les deux points tactiles simultanément.|  
|![Orientation dans la barre d’outils de l’émulateur de Windows Phone](../debugger/media/wp-emulator-rotation.png "WP_Emulator_rotation")|**Configurer l’orientation de l’émulateur**<br /><br /> Vous pouvez choisir parmi trois orientations possibles pour l'émulateur Windows Phone : portrait, paysage gauche ou paysage droite. La taille de l'émulateur n'est pas modifiée quand vous changez l'orientation.<br /><br /> Pour modifier l’orientation, cliquez sur le **faire pivoter à gauche** bouton ou le **faire pivoter à droite** bouton.|  
|![Taille des options de barre d’outils de l’émulateur de Windows Phone](../debugger/media/wp-emulator-size.png "WP_Emulator_size")|**Configurer la taille de l’émulateur**<br /><br /> Vous pouvez modifier la taille de l'émulateur sur l'écran de l'ordinateur hôte. La taille en points par pouce (PPP) de l'émulateur est basée sur celle du moniteur hôte, indépendamment de la valeur du zoom.<br /><br /> -Pour adapter l’émulateur taille à l’écran, cliquez sur le **ajuster à l’écran** bouton.<br />-Pour modifier le paramètre du zoom, cliquez sur le **Zoom** bouton. Le **Zoom** boîte de dialogue s’ouvre. Dans le **Zoom** boîte de dialogue, entrez une valeur de zoom entre 33 et 100.|  
  
## <a name="BKMK_buttons"></a> Utiliser les boutons physiques simulés dans l’émulateur  
 Simulez l'utilisation des boutons physiques d'un téléphone à l'aide des boutons physiques simulés situés à droite de l'écran de l'émulateur.  
  
- Cliquez sur le **Power** bouton pour simuler la désactivant et l’affichage. Cliquez et maintenez le bouton enfoncé pour simuler la désactivation du téléphone.  
  
- Cliquez sur le **monter le Volume** ou **baisser le Volume** bouton pour simuler la modification du volume des haut-parleurs du téléphone pour les appels téléphoniques et les notifications.  
  
- Le **caméra** bouton lance l’application caméra. Vous pouvez simuler la prise de photo ou de vidéo à l'aide des commandes de l'application Caméra.  
  
  La capture d'écran suivante montre les boutons physiques simulés.  
  
1. L'image de gauche affiche l'écran d'accueil sur l'émulateur.  
  
2. L’image du milieu affiche l’émulateur après avoir appuyé sur le **Power** bouton pour désactiver l’affichage.  
  
3. L’image de droite affiche l’écran de l’émulateur après avoir appuyé sur le **monter le Volume** bouton pour augmenter le volume.  
  
   ![Boutons sur l’émulateur Windows Phone](../debugger/media/wp-emulator-buttons.png "WP_Emulator_buttons")  
  
## <a name="BKMK_tasks_kbd"></a> Utiliser le clavier de l’ordinateur avec l’émulateur  
 L'émulateur prend en charge le mappage du clavier physique de votre ordinateur de développement au clavier d'un Windows Phone. Le comportement des touches est le même que sur un appareil Windows Phone.  
  
 Par défaut, le clavier physique n'est pas activé. Cette implémentation équivaut à un clavier coulissant devant être déployé avant de pouvoir être utilisé. Avant l'activation du clavier physique, l'émulateur accepte la saisie au clavier des touches de contrôle.  
  
 Les caractères spéciaux du clavier d'une version localisée d'un ordinateur Windows de développement ne sont pas pris en charge par l'émulateur. Pour entrer des caractères spéciaux figurant sur un clavier localisé, utilisez plutôt le panneau de saisie.  
  
 Pour utiliser le clavier de votre ordinateur dans l'émulateur, appuyez sur la touche Pg préc ou Pause/Attn (émulateur Windows 8/8.1) ou sur la touche F4 (émulateur Windows 10).  
  
 Pour cesser d'utiliser le clavier de votre ordinateur dans l'émulateur, appuyez sur la touche Pg suiv ou Pause/Attn (émulateur Windows 8/8.1) ou sur la touche F4 (émulateur Windows 10).  
  
 Le tableau suivant indique les touches du clavier physique que vous pouvez utiliser pour émuler les boutons et autres contrôles d'un appareil Windows Phone.  
  
|Touche physique de l'ordinateur|Bouton matériel Windows Phone|Notes|  
|---------------------------|-----------------------------------|-----------|  
|F1|Retour|Les appuis longs fonctionnent comme il se doit.|  
|F2|Écran d'accueil|Les appuis longs fonctionnent comme il se doit.|  
|F3|Rechercher||  
|F4|Dans l'émulateur Windows 10, active/désactive l'utilisation du clavier de l'ordinateur local.|Non applicable dans l'émulateur Windows 8/8.1.|  
|F5|Non applicable.||  
|F6|CAMÉRA - MOITIÉ|Bouton dédié à la caméra qui est enfoncé à moitié.|  
|F7|CAMÉRA - ENTIER|Bouton dédié à la caméra.|  
|F8|Non applicable.||  
|F9|MONTER LE VOLUME||  
|F10|BAISSER LE VOLUME||  
|F11|Non applicable.||  
|F12|MARCHE/ARRÊT|Appuyez sur la touche F12 deux fois pour activer l'écran de verrouillage.<br /><br /> Les appuis longs fonctionnent comme il se doit.|  
|Échap|Retour|Les appuis longs fonctionnent comme il se doit.|  
|Pause/Attn|Activer/désactiver le clavier (émulateur Windows 8/8.1 uniquement).|Non applicable dans l'émulateur Windows 10.|  
|PG.PRÉC|Active le clavier matériel (émulateur Windows 8/8.1 uniquement).|Non applicable dans l'émulateur Windows 10.|  
|PG.SUIV|Désactive le clavier matériel (émulateur Windows 8/8.1 uniquement).|Non applicable dans l'émulateur Windows 10.|  
  
## <a name="BKMK_checkpoints"></a> Enregistrer et charger des points de contrôle personnalisés  
 Enregistrer un instantané de l’état de l’émulateur à l’aide de la **points de contrôle** onglet de l’émulateur **des outils supplémentaires**. Cette fonctionnalité est utile si vous testez fréquemment votre application avec les mêmes données et paramètres.  
  
 Par exemple, si votre application requiert plusieurs contacts, vous pouvez créer les enregistrements de contact une fois et enregistrer un instantané de l'émulateur. Sinon, vous devez recréer les enregistrements de contact chaque fois que vous démarrez l'émulateur.  
  
- Cliquez sur **nouveau point de contrôle** pour capturer un nouvel instantané de l’état de l’émulateur avec les données et les paramètres requis pour tester votre application plus tard. Le nouveau point de contrôle est ajouté à la **points de contrôle** liste.  
  
   Vous ne pouvez pas capturer un point de vérification si le débogueur est attaché à l'émulateur.  
  
- Sélectionnez un point de contrôle dans le **points de contrôle** liste pour afficher les informations sur le point de contrôle.  
  
- Sélectionnez la case dans la **par défaut** colonne afin qu’un point de contrôle enregistré le point de contrôle par défaut pour l’émulateur actif.  
  
- Cliquez sur **restaurer** pour redémarrer le système d’exploitation Windows Phone sur l’émulateur et charger l’instantané sélectionné.  
  
- Cliquez sur **supprimer** pour supprimer un instantané dont vous n’avez plus besoin.  
  
  L’image d’origine de l’émulateur apparaît toujours comme premier élément dans le **points de contrôle** liste et ne peut pas être modifiées ou supprimées. Toutefois, vous pouvez sélectionner un autre instantané que l'image par défaut de l'émulateur.  
  
  ![Onglet points de contrôle de l’émulateur Windows Phone](../debugger/media/wp-emulator-checkpoints.png "WP_Emulator_checkpoints")  
  
## <a name="BKMK_tasks_shot"></a> Captures d’écran dans l’émulateur  
 Vous pouvez créer des captures d'écran de vos applications Windows Phone à l'aide de l'outil de capture d'écran de la fenêtre Outils supplémentaires. L’outil crée des fichiers PNG dans la même résolution que celle de l’émulateur en cours d’exécution.  
  
 ![Captures d’écran à partir du Windows Phone Emulator](../debugger/media/wp-emulator-screenshots.png "WP_Emulator_screenshots")  
  
#### <a name="to-create-an-app-screenshot-by-using-the-built-in-emulator-screenshot-tool"></a>Pour créer une capture d'écran d'application à l'aide de l'outil de capture d'écran intégré à l'émulateur  
  
1. Pour optimiser la qualité de vos captures d'écran, définissez le niveau de zoom de l'émulateur sur 100 %. Plus le niveau de zoom est élevé, plus la qualité de la capture d'écran est élevée.  
  
2. Démarrez votre application dans l'émulateur.  
  
3. Dans la barre d’outils de l’émulateur, cliquez sur le bouton développer pour ouvrir le **des outils supplémentaires** fenêtre.  
  
4. Cliquez sur le **capture d’écran** onglet.  
  
5. Lorsque votre application est prête, cliquez sur le **capturer** bouton.  
  
    La capture d'écran apparaît dans l'espace de travail.  
  
6. Cliquez sur le **enregistrer** bouton pour ouvrir la **Enregistrer sous** boîte de dialogue.  
  
7. Choisissez l’emplacement et **nom de fichier** que vous souhaitez, puis cliquez sur **enregistrer**.  
  
8. Vous pouvez aussi accéder à d'autres pages de votre application et créer d'autres captures d'écran.  
  
9. Lancez un émulateur avec une résolution d’écran différente pour créer les mêmes captures d’écran avec différentes résolutions. Si vous avez exécuté votre application avec débogage, vous devez arrêter le débogage avant de pouvoir la réexécuter sur un autre émulateur.  
  
   Désactivez les compteurs de fréquence des trames sur l'écran de l'émulateur avant de créer des captures d'écran destinées au Windows Phone Store.  
  
#### <a name="to-disable-frame-rate-counters-in-the-emulator-before-capturing-screenshots"></a>Pour désactiver les compteurs de fréquence des trames dans l'émulateur avant de créer des captures d'écran  
  
- Spécifiez une version Release dans Visual Studio. Après avoir spécifié une version Release, lancez votre application en sélectionnant le **déployer _[nom_application]_**  lien sur le **Build** menu.  
  
- Vous pouvez aussi insérer un commentaire sur la ligne de code dans le fichier app.xaml.cs ou app.xaml.vb qui définit la valeur de `EnableFrameRateCounter` sur `true`.
