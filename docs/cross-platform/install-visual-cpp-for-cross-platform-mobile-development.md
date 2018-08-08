---
title: Installer Visual C++ pour le développement mobile multiplateforme | Microsoft Docs
ms.custom: ''
ms.date: 05/21/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 5dffe82511e75889ea588cb23b1f19490f991ab0
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251905"
---
# <a name="install-cross-platform-mobile-development-with-c"></a>Installer le développement mobile multiplateforme avec C++

Vous pouvez utiliser C++ dans Visual Studio pour créer des applications de bureau Windows, des applications de la plateforme Windows universelle (UWP), des applications Linux et, désormais, des applications pour Android et iOS. La charge de travail **Développement mobile en C++** est un ensemble installable de composants dans Visual Studio qui inclut des modèles Visual Studio multiplateformes iOS, Android et UWP. Elle installe les outils multiplateformes ainsi que les Kits de développement logiciel nécessaires à une prise en main rapide, sans que vous n’ayez à effectuer les recherches, le téléchargement ni la configuration. Vous pouvez utiliser ces outils dans Visual Studio pour créer, modifier, déboguer et tester facilement vos projets multiplateformes. Cette rubrique décrit comment installer les outils et les logiciels tiers requis pour développer des applications multiplateformes dans C++ à l’aide de Visual Studio. Pour obtenir une vue d’ensemble, consultez [Développement multiplateforme en Visual C++ pour appareils mobiles](https://go.microsoft.com/fwlink/p/?LinkId=536383)

## <a name="requirements"></a>Configuration requise

- Pour connaître la configuration requise pour l’installation, consultez [Configuration système requise pour la famille de produits Visual Studio](/visualstudio/productinfo/vs2017-system-requirements-vs).

   > [!IMPORTANT]
   > Si vous utilisez Windows 7 ou Windows Server 2008 R2, vous pouvez développer du code pour les applications de bureau Windows, pour les applications et les bibliothèques Android Native Activity, et pour les applications et les bibliothèques de code pour iOS, mais pas pour les applications Windows Phone ni UWP.

Pour créer des applications pour des plateformes d’appareils spécifiques, il y a quelques spécifications requises supplémentaires :

- Les émulateurs Windows Phone et l’émulateur Microsoft Visual Studio pour Android requièrent un ordinateur qui peut exécuter Hyper-V. La fonctionnalité Hyper-V de Windows doit être activée pour permettre l’installation et l’exécution des émulateurs. Pour plus d’informations, consultez la [configuration requise](system-requirements-for-the-visual-studio-emulator-for-android.md) de l’émulateur.

- Les émulateurs Android x86 fournis avec le SDK Android offrent des performances optimales sur des ordinateurs pouvant exécuter le pilote Intel HAXM. Ce pilote nécessite un processeur Intel x64 avec prise en charge de Execute Disable Bit et de VT-x. Pour plus d’informations, consultez [Intel® Hardware Accelerated Execution Manager (Intel® HAXM)](https://go.microsoft.com/fwlink/p/?LinkId=536385).

- La génération du code pour iOS nécessite un identifiant Apple, un compte iOS Developer Program et un ordinateur Mac pouvant exécuter [Xcode](https://go.microsoft.com/fwlink/p/?LinkId=536387) version 6 (ou ultérieure) sur OS X Mavericks (version 10.9) ou ultérieure. Pour obtenir un lien pointant vers la procédure d’installation, consultez [Installer les outils pour iOS](#install-tools-for-ios).

## <a name="get-the-tools"></a>Se procurer les outils

Le développement mobile en C++ est disponible dans les éditions Community, Professional et Enterprise de Visual Studio. Pour obtenir Visual Studio, visitez la page [Téléchargements Visual Studio](https://go.microsoft.com/fwlink/p/?linkid=517106). Les outils multiplateformes de développement mobile sont disponibles à partir de Visual Studio 2015 Update 2 ou version ultérieure.

## <a name="install-the-tools"></a>Installer les outils

Le programme d’installation pour Visual Studio 2017 inclut une charge de travail **Développement mobile en C++**, qui installe les outils de langage, modèles et composants C++ requis pour le développement Android et iOS dans Visual Studio. Elle installe les ensembles d’outils GCC et Clang nécessaires pour les builds Android et le débogage, ainsi que les composants permettant de communiquer avec un Mac pour le développement iOS. Elle installe également tous les outils tiers et kits de développement logiciel qui sont requis pour prendre en charge le développement d’applications iOS et Android. La plupart de ces outils tiers sont des logiciels open source nécessaires pour la prise en charge de la plateforme Android.

- Android NDK (Native Development Kit) est obligatoire pour générer du code C++ qui cible la plateforme Android.

- Le SDK Android, Apache Ant et le Kit de développement Java SE sont requis dans le processus de génération Android.

- L’émulateur Google Android et Intel Hardware Accelerated Execution Manager sont des composants facultatifs mais recommandés. Vous pouvez développer et déboguer directement sur un appareil Android, mais il est souvent plus facile d’utiliser un émulateur sur votre bureau. Microsoft fournit également un Émulateur Visual Studio pour Android qui peut être installé séparément.

#### <a name="to-install-the-mobile-development-with-c-workload-in-visual-studio-2017"></a>Pour installer la charge de travail Développement mobile en C++ dans Visual Studio 2017

1. Exécutez le **programme d’installation de Visual Studio** à partir du menu **Démarrer**.

1. Si vous avez déjà installé Visual Studio, choisissez le bouton **Modifier** pour la version installée de Visual Studio que vous souhaitez modifier. Sinon, choisissez **Installer** pour installer Visual Studio.

1. Après avoir sélectionné l’onglet **Charges de travail**, faites défiler vers le bas et sélectionnez la charge de travail **Développement mobile en C++** dans le programme d’installation de Visual Studio. Lorsque cette charge de travail est sélectionnée, les autres composants requis pour le développement C++ sont également sélectionnés. Vous pouvez également choisir d’autres charges de travail et composants individuels à installer en même temps. Pour générer un code multiplateforme qui cible la plateforme Windows universelle, sélectionnez la charge de travail **Développement de la plateforme universelle Windows**.

1. Dans le volet **Détails de l’installation**, développez **Développement mobile en C++**. Dans la section **Facultatif**, vous pouvez choisir des versions supplémentaires du NDK, l’émulateur Google Android, Hardware Accelerated Execution Manager et l’outil d’accélération de build IncrediBuild.

1. Par défaut, un ou plusieurs composants du programme d’installation du SDK Android sont inclus par la charge de travail. D’autres versions du SDK Android sont disponibles. Pour en ajouter une à votre installation, choisissez l’onglet **Composants individuels**, puis faites défiler jusqu'à la section **SDK, bibliothèques et frameworks** pour effectuer votre sélection.

1. Choisissez le bouton **Modifier** ou **Installer** pour installer la charge de travail **Développement mobile en C++** et vos autres charges de travail et composants facultatifs sélectionnés.

   À la fin de l’installation, fermez le programme d’installation, puis redémarrez l’ordinateur. Certaines actions d’installation des composants tiers ne prennent pas effet tant que l’ordinateur n’a pas redémarré.

   > [!IMPORTANT]
   > Vous devez redémarrer pour vous assurer que tout est installé correctement.

1. Ouvrez Visual Studio. S’il s’agit de la première exécution de Visual Studio, la configuration et la connexion peuvent prendre un certain temps. Lorsque Visual Studio est prêt, vérifiez les mises à jour et installez-les.

#### <a name="to-install-the-mobile-development-component-and-third-party-tools-in-visual-studio-2015"></a>Pour installer le composant Développement mobile et des outils tiers dans Visual Studio 2015

Si vous utilisez Visual Studio 2015, son programme d’installation inclut une option permettant d’installer Visual C++ pour le développement mobile multiplateforme, qui installe les outils de langage, modèles et composants C++ requis dans Visual Studio 2015.

1. Exécutez le programme d’installation de Visual Studio 2015. Pour installer les composants facultatifs, choisissez **Personnalisé** comme type d’installation. Choisissez **Suivant** pour sélectionner les composants facultatifs à installer.

1. Dans **Sélectionner les fonctionnalités**, développez **Développement mobile multiplateforme** et cochez **Développement mobile Visual C++**.

   ![Sélectionner Développement mobile Visual C&#43;&#43;](../cross-platform/media/cppmdd_install_vcmdd.png "CPPMDD_Install_VCMDD")

   Par défaut, quand vous sélectionnez **Développement mobile Visual C++**, l’option **Langages de programmation** est définie pour installer **Visual C++**. De plus, l’option **Kits de développement logiciel (SDK) et outils courants** est définie pour installer les composants tiers nécessaires. Vous pouvez choisir des composants supplémentaires si vous en avez besoin. Par défaut, **Émulateur Microsoft Visual Studio pour Android** est également sélectionné. Les composants qui sont déjà installés apparaissent inactifs dans la liste.

   Pour générer des applications Windows universelles et partager du code entre ces applications et vos projets Android et iOS, dans **Sélectionner les fonctionnalités**, développez **Développement d’applications Windows et web**, puis cochez **Outils de développement d’applications Windows universelles**. Si vous ne prévoyez pas de créer des applications Windows universelles, vous pouvez ignorer cette option.

   Choisissez **Suivant** pour continuer.

1. Les composants tiers ont leurs propres termes du contrat de licence. Vous pouvez afficher les termes du contrat de licence en cliquant sur le lien **Termes du contrat de licence** en regard de chaque composant. Choisissez **Installer** pour ajouter les composants et installer Visual Studio et Visual C++ pour le développement mobile multiplateforme.

1. À la fin de l’installation, fermez le programme d’installation, puis redémarrez l’ordinateur. Certaines actions d’installation des composants tiers ne prennent pas effet tant que l’ordinateur n’a pas redémarré.

   > [!IMPORTANT]
   > Vous devez redémarrer pour vous assurer que tout est installé correctement.

   Si l’installation du composant Émulateur Microsoft Visual Studio pour Android ne peut pas s’effectuer, il est possible qu’Hyper-V ne soit pas activé sur votre ordinateur. Utilisez l’application du Panneau de configuration **Activer ou désactiver des fonctionnalités Windows** pour activer Hyper-V, puis réexécutez le programme d’installation de Visual Studio.

   > [!NOTE]
   > Si votre ordinateur ou votre version de Windows ne prend pas en charge Hyper-V, vous ne pouvez pas utiliser le composant Émulateur Microsoft Visual Studio pour Android. L’Édition familiale de Windows n’inclut pas la prise en charge d’Hyper-V.

1. Ouvrez Visual Studio. S’il s’agit de la première exécution de Visual Studio, la configuration et la connexion peuvent prendre un certain temps. Quand Visual Studio est prêt, dans le menu **Outils** , sélectionnez **Extensions et mises à jour**, **Mises à jour**. Si des mises à jour Visual Studio sont disponibles pour Développement multiplateforme en Visual C++ pour appareils mobiles ou pour l’émulateur Microsoft Visual Studio pour Android, installez-les.

## <a name="install-tools-for-ios"></a>Install tools for iOS

Vous pouvez utiliser Visual C++ pour le développement mobile multiplateforme pour modifier, déboguer du code iOS et ensuite le déployer dans le simulateur iOS ou sur un appareil iOS mais, en raison de restrictions de licences, le code doit être généré à distance sur un Mac. Pour générer et exécuter des applications iOS à l’aide de Visual Studio, vous devez installer et configurer l’agent distant sur votre Mac. Pour obtenir des instructions d’installation détaillées, connaître les prérequis et les options de configuration, consultez [Installer et configurer des outils de génération en utilisant iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Si vous ne générez pas pour iOS, vous pouvez ignorer cette étape.

## <a name="install-or-update-dependencies-manually"></a>Installer ou mettre à jour manuellement les dépendances

Si vous décidez de ne pas installer une ou plusieurs dépendances tierces à l’aide du programme d’installation de Visual Studio quand vous installez la charge de travail **Développement mobile en C++** (ou l’option Développement mobile Visual C++ dans Visual Studio 2015), vous pouvez les installer ultérieurement à l’aide de la procédure décrite dans [Installer les outils](#install-the-tools). Le programme d’installation de Visual Studio est régulièrement mis à jour pour installer les derniers composants tiers. Vous pouvez l’utiliser pour installer Kits de développement logiciel (SDK) et les NDK. Vous pouvez également les installer ou les mettre à jour indépendamment de Visual Studio.

> [!CAUTION]
> Vous pouvez installer les dépendances dans n’importe quel ordre, excepté pour Java. Vous devez installer et configurer le JDK avant d’installer le Kit de développement logiciel (SDK) Android.

Lisez les informations suivantes et utilisez ces liens pour installer des dépendances manuellement.

- [Kit de développement Java SE](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

   Par défaut, le programme d’installation place les outils Java dans *C:\Program Files (x86)\Java*.

- [Kit de développement logiciel Android SDK](https://developer.android.com/sdk/index.html#command-tools)

   Lors de l’installation, mettez à jour les API comme recommandé. Vérifiez que le kit SDK pour Android 5.0 Lollipop (niveau d’API 21), ou version ultérieure, est installé. Par défaut, le programme d’installation place le SDK Android dans *C:\Program Files (x86)\Android\android-sdk*.

   Vous pouvez réexécuter l’application SDK Manager dans le répertoire Android SDK pour mettre à jour le kit SDK et installer des outils facultatifs, ainsi que des niveaux d’API supplémentaires. L’installation des mises à jour risque d’échouer, sauf si vous utilisez **Exécuter en tant qu’administrateur** pour exécuter l’application du Gestionnaire du SDK. Si vous rencontrez des problèmes lors de la génération d’une application Android, recherchez des mises à jour pour les kits SDK installés dans le Gestionnaire du SDK.

   Pour utiliser certains émulateurs Android fournis avec le kit SDK Android, vous devez installer les pilotes Intel HAXM facultatifs. Vous devrez peut-être supprimer la fonctionnalité Hyper-V de Windows pour installer correctement les pilotes Intel HAXM. Vous devez restaurer la fonctionnalité Hyper-V pour utiliser les émulateurs Windows Phone et l’émulateur Microsoft Visual Studio pour Android. Pour plus d’informations, consultez [Accélération matérielle de l’Émulateur Android](https://docs.microsoft.com/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin).

- [Kit de développement natif (NDK) Android](https://developer.android.com/tools/sdk/ndk/index.html)

   Par défaut, le programme d’installation place le Kit de développement natif (NDK) Android dans *C:\ProgramData\Microsoft\AndroidNDK*. Vous pouvez retélécharger et réinstaller le Kit de développement natif (NDK) Android pour mettre à jour son installation.

- [Apache Ant](https://ant.apache.org/bindownload.cgi)

   Par défaut, le programme d’installation place Apache Ant dans *C:\Program Files (x86)\Microsoft Visual Studio 14.0\Apps*.

- [Émulateur Microsoft Visual Studio pour Android](https://aka.ms/vscomemudownload)

   L’émulateur Microsoft Visual Studio pour Android est un émulateur facultatif utile pour tester et déboguer votre code. Après le lancement de l’émulateur Visual Studio pour Android, Google a mis à jour son émulateur Android pour utiliser l’accélération matérielle Intel par le biais du gestionnaire HAXM d’Intel. Nous vous recommandons d'utiliser l’émulateur accéléré de Google lorsque cela est possible car il permet d’accéder aux dernières images du système d’exploitation Android et aux derniers services Google Play.

Dans la plupart des cas, Visual Studio peut détecter les configurations pour les logiciels tiers que vous avez installés et gère les chemins d’installation dans des variables d’environnement internes. Vous pouvez remplacer les chemins par défaut de ces outils de développement multiplateformes dans l’IDE de Visual Studio.

#### <a name="to-set-the-paths-for-third-party-tools"></a>Pour définir les chemins des outils tiers

1. Dans la barre de menus Visual Studio, choisissez **Outils** > **Options**.

1. Dans la boîte de dialogue **Options**, sélectionnez **Multiplateforme** > **C++** > **Android**.

   ![Options de chemin de l’outil Android](../cross-platform/media/cppmdd_options_android.PNG "CPPMDD_Options_Android")

1. Pour modifier le chemin utilisé par un outil, cochez la case en regard du chemin et modifiez le chemin du dossier dans la zone de texte. Vous pouvez également utiliser le bouton Parcourir (**...**) pour ouvrir une boîte de dialogue **Sélectionner un emplacement** et choisir le dossier.

1. Choisissez **OK** pour enregistrer les emplacements des dossiers d’outils personnalisés.

## <a name="see-also"></a>Voir aussi

- [Installer et configurer des outils de génération en utilisant iOS](install-and-configure-tools-to-build-using-ios.md)
- [Développement multiplateforme en Visual C++ pour appareils mobiles](https://go.microsoft.com/fwlink/p/?LinkId=536383)
