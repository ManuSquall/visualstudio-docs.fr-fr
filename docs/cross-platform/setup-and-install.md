---
title: Configuration et installation | Microsoft Docs
ms.custom: 
ms.date: 04/13/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
caps.latest.revision: 16
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
ms.openlocfilehash: d353d8a0a41ad487191b79aa68f26585cf9902b4
ms.contentlocale: fr-fr
ms.lasthandoff: 05/13/2017

---
# <a name="setup-and-install"></a>Configurer et installer
Pour générer des applications natives iOS, Android et Windows à partir d’une base de code C#/.NET commune en utilisant Xamarin, vous avez besoin des éléments suivants :  
  
-   Pour travailler avec des applications Windows et Android : un ordinateur de développement Windows équipé de Visual Studio 2017 ou 2015 avec Xamarin. Vous pouvez également utiliser Visual Studio 2013 en suivant les instructions relatives à l’[installation directe de Xamarin](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com). 
  
-   Pour travailler avec des applications iOS : un Mac avec macOS Sierra 10.12 ou ultérieur, avec Xcode et Xamarin installés.  
  
 Vous pouvez configurer les ordinateurs Windows et Mac en même temps. Pendant l’exécution de ces programmes d’installation, vous pouvez parcourir la rubrique [En savoir plus sur le développement mobile avec Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) pour vous familiariser avec les informations nécessaires.  
 
Si vous rencontrez des problèmes d’utilisation de Xamarin après les phases d’installation et de configuration, publiez votre question sur [forums.xamarin.com](http://forums.xamarin.com/).
  
> [!NOTE]
>  À partir du 31 mars 2016, Xamarin est inclus dans toutes les éditions de Visual Studio, sans coût supplémentaire et sans nécessiter de licence distincte. Xamarin Studio Community pour Mac est également gratuit pour les étudiants, les développeurs de logiciels open source et les petites équipes. Notez que pour les installations existantes de Visual Studio configurées avec des licences antérieures de Xamarin, vous devez mettre à jour Xamarin vers la version 4.0.3.214 ou une version ultérieure. Pour ce faire, accédez à **Outils > Options > Xamarin > Autre**, cliquez sur le lien **Vérifier maintenant**, puis téléchargez la mise à jour 4.0.3.214. Après avoir redémarré Visual Studio, accédez à **Outils > Compte Xamarin** pour voir la mise à jour de l’état de la licence.  
  
##  <a name="prereq"></a> Conditions préalables  
  
###  <a name="for-targeting-windows-and-android"></a>Pour cibler Windows et Android 
  
1.  Recommandé : Ordinateur Windows physique (pas une machine virtuelle) exécutant Windows 8 ou ultérieur pour optimiser les performances de l’émulateur Android. (Avons-nous bien précisé que vous avez besoin d’un ordinateur physique et non d’une machine virtuelle ?)  
  
2.  Si vous disposez d’un ordinateur Windows 7 (ou version antérieure), utilisez Xamarin Player pour Android en tant qu’émulateur. 
    
3. Pour chaque configuration, vous pouvez toujours exécuter les applications directement sur les appareils physiques connectés.  
  
### <a name="for-targeting-ios"></a>Pour cibler iOS  
  
1.  Mac ou Mac mini en réseau avec macOS Sierra exécutant macOS 10.12 ou ultérieur (obligatoire pour Xcode 8.3).  
  
2.  Quand vous utilisez Visual Studio sur un ordinateur Windows 7 (ou version ultérieure) comme environnement de développement principal, un Mac en réseau est nécessaire uniquement pour compiler et déboguer les applications iOS, se connecter au simulateur iOS ou aux appareils attachés, et utiliser le concepteur de storyboards de Visual Studio pour concevoir l’interface utilisateur. Les modèles de Mac plus anciens sont tout à fait suffisants pour ce rôle secondaire.  
  
##  <a name="windows"></a> Configuration de Windows (Visual Studio et Xamarin)  
  
> [!TIP]
>  Ces instructions s’appliquent à Visual Studio 2017. Pour Visual Studio 2015, consultez [MSDN](https://msdn.microsoft.com/en-us/library/mt613162.aspx). Pour utiliser Xamarin avec Visual Studio 2013 (Update 2 obligatoire), suivez les instructions d’[installation directe de Xamarin](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com).  
  
1.  [Téléchargez et lancez le programme d’installation de n’importe quelle édition de Visual Studio 2017](https://www.visualstudio.com/downloads/) (Community, Professional ou Enterprise). Visual Studio 2017 Community est une version gratuite, tandis que les éditions Professional et Enterprise peuvent être utilisées dans le cadre d’un essai de 30 jours. Au-delà, vous devez acheter une licence.  
  
    1.  Si Visual Studio 2017 est déjà installé, exécutez le **programme d’installation de Visual Studio** à partir du menu **Démarrer**.
  
2.  Dans le programme d’installation, cliquez sur le bouton **Choix supplémentaires** (icône à trois barres) _à côté de_ **Lancer**, puis choisissez **Modifier** :  
  
     ![Choisir l’option Modifier dans le programme d’installation de Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-1a.png "Configuration multiplateforme de Xamarin 1")  
  
3.  Cochez les cases suivantes :  
  
    1.  **Mobile et jeux > Développement mobile en .NET**. Différents outils Android sont aussi automatiquement sélectionnés sous Kits de développement logiciel (SDK) et outils courants. Cette option permet également de mettre à jour les installations Xamarin existantes.  
  
         ![Sélectionner l’option Développement mobile sous Jeux et Développement mobile](../cross-platform/media/cross-plat-xamarin-setup-2a.png "Configuration multiplateforme de Xamarin 2")  
  
    2. (Facultatif) **Windows > Développement pour la plateforme Windows universelle**. Des options y sont proposées pour l’installation d’images d’émulateurs dont le chargement prend davantage de temps : vous pouvez toujours revenir au programme d’installation de Visual Studio pour les ajouter ultérieurement. 
  
4.  Cliquez sur le bouton **Modifier** et laissez le processus s’exécuter. Là encore, cette opération va prendre un certain temps. Vous pouvez en profiter pour poursuivre la lecture des instructions de configuration du Mac, puis consulter [En savoir plus sur le développement mobile avec Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).  
  
5.  Une fois l’installation terminée, lancez Visual Studio et connectez-vous avec votre compte Microsoft si vous y êtes invité (il s’agit du même compte que celui que vous utilisez avec Windows).  
      
6.  Pour tester des applications Android, utilisez l’[émulateur Android SDK](https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debug-on-emulator/android-sdk-emulator/) si vous n’avez pas d’appareils physiques. Voir la remarque ci-dessous.  
  
 **Remarque pour les émulateurs sur des ordinateurs Windows :** Les UC ne prenant en charge qu’une seule technologie de virtualisation à la fois, il est préférable d’avoir un seul émulateur actif sur un ordinateur de développement. Il existe trois technologies de virtualisation principales : Hyper-V (utilisé par l’émulateur Visual Studio pour Android et par l’émulateur Windows Phone), Virtual Box (utilisé par Genymotion) et Intel HAXM (utilisé par l’émulateur du kit Android SDK). En raison de différents problèmes entre Hyper-V et Virtual Box, il est préférable d’utiliser des émulateurs d’un seul type sur un ordinateur donné. Ainsi, il est recommandé d’utiliser Hyper-V sur les ordinateurs Windows 8 (ou ultérieur) et les émulateurs Intel HAXM sur Windows 7 (ou antérieur) et dans les situations où Windows est exécuté sur un Mac.  
  
##  <a name="mac"></a> Configuration pour Mac (identifiant Apple, Xcode et Xamarin)  
  
1.  Créez un ID Apple gratuit sur [https://appleid.apple.com](https://appleid.apple.com/) si vous n’en avez pas encore. Cette opération est nécessaire pour l’installation et la connexion à Xcode.  
  
2.  Téléchargez et installez Xcode à partir de  [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/), puis ajoutez votre ID Apple comme décrit dans [Ajout de votre compte à XCode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com).  
  
3.  Téléchargez et installez Xamarin en suivant les instructions de [Installing and Configuring Xamarin.iOS](http://developer.xamarin.com/guides/ios/getting_started/installation/mac/) (xamarin.com).  
  
4.  Une fois que vous avez fini d’installer Xamarin sur les ordinateurs Windows et Mac, suivez les instructions de la page [Connecting to the Mac](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/) (xamarin.com) pour pouvoir utiliser iOS et le Mac à partir de Visual Studio sur l’ordinateur Windows.  
  
     Notez que les deux ordinateurs doivent être sur le même réseau local.
