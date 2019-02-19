---
title: Émulateur Visual Studio pour Android | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: 80f0104f-a4db-44dd-bd55-37bb67776c62
caps.latest.revision: 7
ms.author: crdun
manager: crdun
ms.openlocfilehash: ec7e6d3ee6d27c444d0904e750293a3d82c3ab4a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54789852"
---
# <a name="visual-studio-emulator-for-android"></a>Émulateur Visual Studio pour Android
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
L'Émulateur Visual Studio pour Android est une application de bureau qui émule un appareil Android. Il fournit un environnement virtualisé dans lequel vous pouvez déboguer et tester des applications Android sans appareil physique. Il fournit également un environnement isolé pour les prototypes de votre application.  
  
 L'Émulateur Visual Studio pour Android est conçu pour fournir des performances comparables à un appareil réel. Avant de publier votre application, nous vous recommandons toutefois de la tester sur un appareil physique.  
  
 Vous pouvez tester votre application sur un profil d'appareil unique pour chacune des plateformes Android, résolutions d'écran et autres propriétés matérielles prises en charge par l'Émulateur Visual Studio pour Android.  
  
 Cette rubrique contient les sections suivantes.  
  
-   [Installation et désinstallation](#Installing)  
  
-   [Configuration système requise et compatibilité descendante](#Requirements)  
  
-   [Mise en réseau dans l’Émulateur Visual Studio pour Android](#Networking)  
  
-   [Configuration de l’Émulateur Visual Studio pour Android](#Configuring)  
  
-   [Fonctionnalités que vous pouvez tester dans l’émulateur](#FeaturesTest)  
  
-   [Fonctionnalités que vous ne pouvez pas tester dans l’émulateur](#FeaturesNonTest)  
  
-   [Ressources de support technique](#Support)  
  
##  <a name="Installing"></a> Installation et désinstallation  
 Installation de  
  
 L'Émulateur Visual Studio pour Android fait partie des outils multiplateformes disponibles dans Visual Studio, que vous pouvez installer lors d'une installation personnalisée de Visual Studio. Pour ce faire, sélectionnez Développement multiplateforme pour appareils mobiles, Kits de développement logiciel (SDK) et outils courants, puis Émulateur Microsoft Visual Studio pour Android.  
  
 Désinstallation  
  
 Vous pouvez désinstaller l'émulateur Visual Studio pour Android dans Ajout/Suppression de programmes, dans le Panneau de configuration.  
  
> [!NOTE]
>  La désinstallation de Visual Studio ne désinstalle pas l'émulateur. Vous devez désinstaller l'émulateur séparément.  
  
 Quand vous désinstallez l'Émulateur Visual Studio pour Android, les cartes Ethernet virtuelles Hyper-V qui ont été créées pour l'émulateur ne sont pas supprimées automatiquement. Vous pouvez supprimer manuellement ces cartes virtuelles (si elles ne sont pas en cours d’utilisation) en ouvrant le Gestionnaire Hyper-V, en sélectionnant l’une des images VHD de l’émulateur, en choisissant l’onglet Réseau et en choisissant **Supprimer** pour chaque commutateur répertorié sous cet onglet.  
  
##  <a name="Requirements"></a> Configuration système requise et compatibilité descendante  
 Pour obtenir des informations importantes sur la configuration matérielle et logicielle requise de l’Émulateur Visual Studio pour Android, consultez la rubrique suivante.  
  
- [System Requirements for the Visual Studio Emulator for Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)  
  
  L'Émulateur Visual Studio pour Android nécessite Visual Studio 2015. Il n'est pas compatible avec les versions antérieures de Visual Studio.  
  
  Les nouvelles versions de l'émulateur sont installées sur les anciennes versions (et peuvent, dans certains cas, remplacer les anciennes images et supprimer les paramètres, applications et fichiers installés sur ces images).  
  
##  <a name="Networking"></a> Mise en réseau dans l’Émulateur Visual Studio pour Android  
 La connexion réseau de l'Émulateur Visual Studio pour Android se comporte comme la connexion d'un ordinateur de bureau avec ces caractéristiques :  
  
- L'émulateur apparaît sur le réseau comme une unité distincte avec sa propre adresse IP.  
  
- Il ne nécessite aucun logiciel de mise en réseau supplémentaire en plus de ceux déjà installés.  
  
- Il n'est pas joint à un domaine Windows.  
  
  Pour comprendre les fonctions de la connexion réseau de l'émulateur, imaginez qu'il s'agit d'une connexion Wi-Fi entre votre téléphone Android et le même réseau. Si une application en cours d'exécution sur votre téléphone peut accéder à une ressource réseau via sa connexion Wi-Fi, une application en cours d'exécution sur l'émulateur peut aussi accéder à la même ressource réseau.  
  
  Pour plus d’informations sur la configuration réseau requise, consultez [Configuration système requise pour l’Émulateur Visual Studio pour Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md).  
  
  Pour plus d’informations sur la résolution des problèmes de réseau, consultez [Résolution des problèmes liés à l’émulateur Visual Studio pour Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md).  
  
##  <a name="Configuring"></a> Configuration de l’Émulateur Visual Studio pour Android  
 Tester la compatibilité de votre application Android sur toute la gamme de matériel Android peut constituer un vrai défi. Les téléphones et tablettes Android disponibles sur le marché existent en de nombreuses versions, tailles d'écran et configurations matérielles (mémoire RAM, UC, architecture, etc.). L'Émulateur Visual Studio pour Android simplifie cette démarche grâce aux profils d'appareils. Notre ensemble de profils d'appareils inclut le matériel le plus populaire sur le marché, y compris les appareils Samsung, Motorola, Sony, LG et bien plus encore.  
  
 Dans Visual Studio 2015, vous pouvez installer, désinstaller et démarrer les profils d'appareils à l'aide du Gestionnaire d'émulateur. Vous pouvez accéder au Gestionnaire d’émulateur en choisissant **Outils**, puis **Émulateur Microsoft Visual Studio pour Android**.  
  
 ![Émulateur Visual Studio pour Android Manager](../cross-platform/media/android-emu-manager.png "Android_Emu_Manager")  
  
 Par défaut, il existe quatre profils d'appareils préinstallés (configurations KitKat et Lollipop phone/5" et tablet/7" ), comme indiqué par les icônes et le texte blanc. Les autres profils de la liste restent grisés tant que vous n’avez pas choisi le bouton **Installer un profil** et que l’installation n’est pas terminée. Vous pouvez filtrer la liste par niveau d'API et cliquer sur la flèche de détails en bas à droite d'un profil pour afficher l'ensemble de ses détails de configuration.  
  
 Une fois que vous avez installé l’ensemble de profils que vous souhaitez cibler, vous pouvez démarrer ces nouveaux profils directement à partir du gestionnaire en appuyant sur le bouton vert **Lecture**. Les profils apparaissent également dans le menu déroulant de la cible de débogage dans n’importe quel type de projet mobile multiplateforme Visual Studio.  
  
##  <a name="FeaturesTest"></a> Fonctionnalités que vous pouvez tester dans l’émulateur  
 Pour plus d’informations sur les fonctionnalités que vous pouvez tester dans l’émulateur, consultez cette [documentation](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx).  
  
##  <a name="FeaturesNonTest"></a>Fonctionnalités que vous ne pouvez pas tester dans l’émulateur  
 La liste suivante décrit les fonctionnalités de la plateforme Android que vous **ne pouvez pas** tester dans l’émulateur. Vous devez tester ces fonctionnalités sur un appareil physique.  
  
-   Boussole  
  
-   Gyroscope  
  
-   Contrôleur de vibration  
  
-   Luminosité. La modification du niveau de luminosité de l'émulateur n'affecte pas visuellement la façon dont l'appareil apparaît sur votre écran.  
  
##  <a name="Support"></a> Ressources de support technique  
 Si votre ordinateur hôte satisfait à la configuration système requise et que vous rencontrez un problème non couvert dans ce guide de dépannage :  
  
-   Posez une question sur StackOverflow en utilisant les balises [android-emulator](http://stackoverflow.com/questions/tagged/android-emulator) et visual-studio.  
  
-   Signalez un problème en utilisant l'outil Envoyer un sourire dans Visual Studio ou dans le gestionnaire de l'émulateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration requise pour l’émulateur Visual Studio pour Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)   
 [Troubleshooting the Visual Studio Emulator for Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)
