---
title: "Configuration, installation et vérifications pour les utilisateurs Mac | Microsoft Docs"
ms.custom: 
ms.date: 04/13/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22725520-59ba-4f6f-80e4-097b1287a34b
caps.latest.revision: 10
author: ghogen
ms.author: ghogen
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: b3c999f9b960e6d220fcf9e4715393dd27e5fe73
ms.contentlocale: fr-fr
ms.lasthandoff: 05/13/2017

---
# <a name="setup-install-and-verifications-for-mac-users"></a>Configuration, installation et vérifications pour les utilisateurs Mac
Cette rubrique est destinée aux développeurs qui travaillent principalement sur Mac et qui utilisent éventuellement Visual Studio sur une machine virtuelle Windows sur le Mac. Si vous êtes un développeur qui travaille principalement sur un ordinateur Windows et que vous devez configurer un Mac secondaire pour cibler iOS, consultez la rubrique principale [Configurer et installer](../cross-platform/setup-and-install.md).

 Pour utiliser Xamarin sur un Mac, vous devez disposer des éléments suivants :

-   Un Mac avec macOS Sierra 10.12 ou ultérieur, avec Xcode et Xamarin installés.

-   Une des configurations suivantes :

    -   **Pour l’exécution de Xamarin Studio directement sur le Mac :** Xamarin Studio est l’environnement de développement de Xamarin qui prend en charge la création d’applications Android, iOS et Windows à l’aide de C#.  Pour obtenir un aperçu rapide de Xamarin Studio, reportez-vous à la [vue d’ensemble de Xamarin Studio](https://xamarin.com/studio) (xamarin.com).

    -   **Si Parallels ou VMWare est déjà configuré sur votre Mac :** exécutez Windows avec Visual Studio 2017 et Xamarin dans Parallels ou VMWare.  Avec cette configuration, Xamarin est une extension installée avec Visual Studio qui offre la possibilité d’utiliser Visual Studio comme environnement de développement pour la création d’applications Android, iOS et Windows en C#.  Notez que vous pouvez obtenir un abonnement gratuit de 3 mois à Parallels dans le cadre du programme Visual Studio Developer Essentials. Consultez [Microsoft Visual Studio Dev Essentials Will Include Parallels Desktop Pro and Parallels Access](http://blog.parallels.com/blog/2015/11/18/visual-studio-dev-essentials/) (blog Parallels).

 Cette rubrique fournit des instructions pour cette configuration requise.  Pendant le processus d’installation, vous pouvez passer en revue la rubrique [En savoir plus sur le développement mobile avec Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) pour vous familiariser avec les informations nécessaires.

##  <a name="mac"></a> Configuration pour Mac (identifiant Apple, Xcode et Xamarin)

1.  Créez un ID Apple gratuit sur [Identifiant Apple](https://appleid.apple.com/) si vous n’en avez pas encore. Cette opération est nécessaire pour l’installation et la connexion à Xcode.

2.  Téléchargez et installez Xcode depuis [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/).

3.  Téléchargez et installez Xamarin en suivant les instructions de [Installing and Configuring Xamarin.iOS](http://developer.xamarin.com/guides/ios/getting_started/installation/mac/) (xamarin.com).

4.  Une fois que vous avez fini d’installer Xamarin sur les ordinateurs Windows et Mac, suivez les instructions de la page [Connecting to the Mac using XMA](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Connecting_to_the_Mac_Using_XMA) (xamarin.com) pour pouvoir utiliser iOS et le Mac à partir de Visual Studio sur l’ordinateur Windows.

##  <a name="windows"></a> Configuration de Windows dans Parallels (Visual Studio et Xamarin)

1.  En utilisant le Bureau Windows que vous avez configuré dans Parallels/VMWare, [téléchargez et lancez le programme d’installation de l’édition Visual Studio 2017 de votre choix](https://www.visualstudio.com/downloads/) (Community, Professional ou Enterprise). Visual Studio 2017 Community est une version gratuite, tandis que les éditions Professional et Enterprise peuvent être utilisées dans le cadre d’une évaluation de 30 jours.

2.  Dans le programme d’installation, cliquez sur le bouton **Choix supplémentaires** (icône à trois barres) _à côté de_ **Lancer**, puis choisissez **Modifier** :  
  
     ![Choisir l’option Modifier dans le programme d’installation de Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-1a.png "Configuration multiplateforme de Xamarin 1")  
  
3.  Cochez les cases suivantes :

    1.  **Mobile et jeux > Développement mobile en .NET**. Différents outils Android sont aussi automatiquement sélectionnés sous Kits de développement logiciel (SDK) et outils courants. Cette option permet également de mettre à jour les installations Xamarin existantes.  
  
         ![Sélectionner l’option Développement mobile sous Jeux et Développement mobile](../cross-platform/media/cross-plat-xamarin-setup-2a.png "Configuration multiplateforme de Xamarin 2")  
  
    2. (Facultatif) **Windows > Développement pour la plateforme Windows universelle**. Des options y sont proposées pour l’installation d’images d’émulateurs dont le chargement prend davantage de temps : vous pouvez toujours revenir au programme d’installation de Visual Studio pour les ajouter ultérieurement.  

4.  Cliquez sur le bouton **Modifier** et laissez le processus s’exécuter. Là encore, cette opération va prendre un certain temps. Vous pouvez en profiter pour poursuivre la lecture des instructions de configuration du Mac, puis consulter [En savoir plus sur le développement mobile avec Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).

5.  Une fois l’installation terminée, lancez Visual Studio et connectez-vous avec votre compte Microsoft si vous y êtes invité (il s’agit du même compte que celui que vous utilisez avec Windows).

6.  Une fois que vous avez fini d’installer Xamarin sur les ordinateurs Windows et Mac, suivez les instructions de la page [Connecting to the Mac using XMA](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Connecting_to_the_Mac_Using_XMA) (xamarin.com) pour pouvoir utiliser iOS à partir de Visual Studio.

##  <a name="verify"></a> Vérifier votre environnement
 Une fois les programmes d’installation terminés, passez quelques minutes à vérifier que tout est prêt pour expérimenter le développement Xamarin.

### <a name="xamarin-studio"></a>Xamarin Studio
 Vérifiez d’abord que, quand vous accédez aux liens fournis, **Xamarin Studio** est sélectionné en haut à droite, afin d’afficher la version correcte de la documentation de Xamarin :

 ![Sélection de Xamarin Studio pour afficher la documentation appropriée sur Xamarin.com](../cross-platform/media/crossplat-xamarin-mac-1.png "CrossPlat Xamarin Mac 1")

**Android**

1.  Vérifiez la création d’un projet Android en suivant les instructions de [Create an Android Project](http://developer.xamarin.com/recipes/android/general/projects/create_an_android_project/) (xamarin.com).

2.  Vérifiez le débogage dans l’émulateur Android en sélectionnant [Android Player > Integration with Xamarin Studio documentation](https://developer.xamarin.com/guides/android/getting_started/installation/android-player/#Integration_with_Xamarin_Studio) (xamarin.com).

**iOS**

1.  Vérifiez la création d’un projet iOS en suivant les instructions de [Create an iOS Project](http://developer.xamarin.com/recipes/ios/general/projects/create_an_ios_project/) (xamarin.com).

2.  Validez le débogage dans le simulateur iOS via la [documentation du débogage dans le simulateur](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) (xamarin.com).

### <a name="visual-studio"></a>Visual Studio
 Vérifiez d’abord que, quand vous accédez aux liens fournis, **Visual Studio** est sélectionné en haut à droite, afin d’afficher la version correcte de la documentation de Xamarin :

 ![Sélection de Visual Studio pour afficher la documentation appropriée sur Xamarin.com](../cross-platform/media/crossplat-xamarin-mac-2.png "CrossPlat Xamarin Mac 2")

**Android**

1.  Vérifiez la création d’un projet Android en suivant les instructions de [Create an Android Project](http://developer.xamarin.com/recipes/android/general/projects/create_an_android_project/) (xamarin.com).

2.  Vérifiez Android Designer : dans le projet Android, dans l’Explorateur de solutions, ouvrez le fichier **Ressources > Disposition > Main.axml**.

    -   Si vous recevez une erreur indiquant que « Le Kit de développement logiciel Android est trop ancien », cliquez sur **Ouvrir Android SDK Manager** dans ce message, puis sélectionnez la dernière version du SDK disponible. Notez que vous devez exécuter Visual Studio en tant qu’administrateur pour mettre à jour le Kit de développement logiciel.

3.  Vérifiez que vous pouvez vous connecter depuis Visual Studio à l’émulateur qui est installé sur votre Mac.  Vous devriez voir Xamarin Player dans la liste des émulateurs que vous pouvez sélectionner à partir de Visual Studio pour le débogage.  Pour ce faire, suivez les instructions dans [Connecting Visual Studio to the Xamarin Android Player](http://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/android-player-with-visual-studio-in-vm/) (xamarin.com).

**iOS**

1.  Vérifiez que votre Mac est disponible sur le réseau et apparié à Visual Studio, comme décrit dans [Connecting to the Mac](https://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Connecting_to_the_Mac) (xamarin.com).

2.  Vérifiez la création d’un projet iOS en suivant les instructions de [Create an iOS Project](http://developer.xamarin.com/recipes/ios/general/projects/create_an_ios_project/) (xamarin.com).

3.  Vérifiez le concepteur de plan conceptuel : dans le projet iOS, dans l’Explorateur de solutions, ouvrez le fichier **MainStoryboard.storyboard** . Ici, Visual Studio héberge le concepteur qui s’exécute à distance sur le Mac.

4.  Vérifiez la génération et le débogage :

    1.  Cliquez avec le bouton droit sur le projet iOS dans l’Explorateur de solutions et sélectionnez **Définir comme projet de démarrage**.

    2.  Sélectionnez la cible **iPhoneSimulator** dans la liste déroulante des builds de Visual Studio, comme indiqué ci-dessous. Si aucun simulateur ne figure dans la liste, lancez Xcode sur votre Mac, sélectionnez **Xcode->Préférences**, puis cliquez sur **Télécharger**. Sous **Components** , vous devez voir les versions de simulateur qui sont disponibles en téléchargement. Vous trouverez des instructions supplémentaires pour le débogage dans la page [Debugging](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) de Xamarin (xamarin.com).

         ![Sélection de la cible de génération iPhoneSimulator](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin Verify 5")

    3.  Sélectionnez une cible iPhone dans le menu déroulant du débogage de Visual Studio comme illustré ci-dessous, puis démarrez le débogueur en appuyant sur F5. Ceci lance le simulateur sur le Mac, où vous allez interagir avec l’application, alors que le débogage se fait dans Visual Studio.

         ![Sélection d’une cible de débogage iPhone](../cross-platform/media/crossplat-xamarin-verify-6.png "CrossPlat Xamarin Verify 6")
