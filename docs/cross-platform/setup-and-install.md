---
title: Installer Xamarin pour Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
ms.technology: vs-ide-mobile
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 4dcd83ffb1076211f8d23aa4491f853d2b7d316f
ms.sourcegitcommit: a0a49cceb0fdc1465ddf76d131c6575018b628b8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2018
---
# <a name="setup-and-install"></a>Configurer et installer

Pour générer des applications iOS, Android et Windows natives à partir d’une base de code C#/.NET commune en utilisant Xamarin, vous avez besoin des composants matériels et logiciels suivants :

-   Pour utiliser des applications Windows et Android : un ordinateur de développement Windows (pas une machine virtuelle) sur lequel Visual Studio 2017 (dont les fonctionnalités de développement Xamarin) est installé.  

-   Pour utiliser des applications iOS : un Mac avec macOS Sierra 10.12 ou version ultérieure, Xcode et Visual Studio pour Mac installés.

Aucune licence distincte n’est nécessaire pour utiliser la plateforme Xamarin.
 
Vous pouvez configurer les ordinateurs Windows et Mac en même temps. Pendant l’exécution de ces programmes d’installation, vous pouvez parcourir la rubrique [En savoir plus sur le développement mobile avec Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) pour vous familiariser avec les informations nécessaires.

Si vous rencontrez des problèmes d’utilisation de la plateforme Xamarin après les phases d’installation et de configuration, postez votre question sur [forums.xamarin.com](http://forums.xamarin.com/).

<a name="prereq" /> 

## <a name="pre-requisites"></a>Conditions préalables

###  <a name="for-targeting-windows-and-android"></a>Pour cibler Windows et Android

Consultez [Configuration exigée pour la famille de produits Visual Studio 2017](https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs) afin de connaître en détail les prérequis pour l’installation de Visual Studio 2017.

Installez Visual Studio 2017 sur un ordinateur Windows physique (pas une machine virtuelle) exécutant Windows 10 avec toutes les mises à jour installées. 

### <a name="for-targeting-ios"></a>Pour cibler iOS

Pour cibler les appareils et émulateurs iOS à partir de votre ordinateur Windows, vous avez également besoin d’un Mac en réseau ou d’un Mac mini exécutant macOS 10.12 ou version ultérieure, et de Xcode 8.3. Consultez [Configurer et installer Visual Studio pour Mac](/visualstudio/mac/installation.md) pour afficher une configuration requise plus détaillée.

<a name="windows" /> 

##  <a name="windows-setup-visual-studio-and-xamarin"></a>Configuration de Windows (Visual Studio et Xamarin)

Si vous n’avez pas encore installé Visual Studio 2017, effectuez les étapes suivantes :

1.  [Téléchargez et lancez le programme d’installation de n’importe quelle édition de Visual Studio 2017](https://www.visualstudio.com/downloads/) (Community, Professional ou Enterprise). Visual Studio Community 2017 est l’édition gratuite. Les éditions Professional et Enterprise peuvent être utilisées dans le cadre d’une évaluation de 30 jours, période après laquelle une licence est nécessaire.

2.  Quand la boîte de dialogue **d’installation** s’affiche, cochez les cases suivantes :    

    - **Mobile et jeux > Développement mobile en .NET**. Cette option sélectionne aussi automatiquement différents outils Android et kits SDK (Software Development Kit). 

        ![Sélectionner l’option Développement mobile sous Jeux et Développement mobile](../cross-platform/media/cross-plat-xamarin-setup-2a.png "Configuration multiplateforme de Xamarin 2")

    - (Facultatif) **Windows > Développement pour la plateforme Windows universelle**. 

Si vous avez déjà installé Visual Studio 2017, mais pas encore la plateforme Xamarin, effectuez les étapes suivantes :

1. Exécutez le **programme d’installation de Visual Studio** à partir du menu **Démarrer**.

2.  Dans le programme d’installation, cliquez sur le bouton **Plus**, puis choisissez **Modifier** :

    ![Choisir l’option Modifier dans le programme d’installation de Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-1a.png "Configuration multiplateforme de Xamarin 1")

3.  Quand la boîte de dialogue **d’installation** s’affiche, cochez **Mobile et jeux > Développement mobile en .NET** et (en option) **Windows > Développement pour la plateforme Windows universelle**. L’option **Développement mobile en .NET** permet également de mettre à jour les installations Xamarin existantes.

Pendant que l’installation est en cours, vous pouvez poursuivre la lecture des instructions de configuration du Mac, puis consulter [En savoir plus sur le développement mobile avec Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).

5.  Une fois l’installation terminée, lancez Visual Studio et connectez-vous avec votre compte Microsoft si vous y êtes invité. Il s’agit du même compte que celui que vous utilisez avec Windows.

6.  Pour tester des applications Android, utilisez [l’émulateur Android SDK](/xamarin/android/get-started/installation/android-emulator/) si vous n’avez pas d’appareil Android physique. 

<a name="mac" />

##  <a name="mac-setup-apple-id-xcode-and-xamarin"></a>Configuration du Mac (ID Apple, Xcode et Xamarin)

1.  Créez un identifiant Apple gratuit sur [https://appleid.apple.com](https://appleid.apple.com/) si vous n’en avez pas encore. Cet ID Apple est nécessaire pour l’installation et la connexion à Xcode.

2.  Téléchargez et installez Xcode à partir de [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/), puis ajoutez votre ID Apple comme décrit dans [Ajout de votre compte à Xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com).

3.  Téléchargez et installez Visual Studio pour Mac en suivant les instructions dans [Configurer et installer Visual Studio pour Mac](/visualstudio/mac/installation.md).

4.  Une fois que vous avez fini d’installer Xamarin sur les ordinateurs Windows et Mac, suivez les instructions dans [Connexion au Mac](/xamarin/ios/get-started/installation/windows/connecting-to-mac/) pour pouvoir utiliser iOS et le Mac à partir de Visual Studio sur l’ordinateur Windows.

Les deux ordinateurs doivent être sur le même réseau local.