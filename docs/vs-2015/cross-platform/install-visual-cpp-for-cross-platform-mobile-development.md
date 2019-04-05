---
title: Installer Visual C++ pour le développement mobile multiplateforme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 504f7f002c41832294e61fa968f7cfd2d32b54b0
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "57869120"
---
# <a name="install-visual-c-for-cross-platform-mobile-development"></a>Installer Visual C++ pour le développement mobile multiplateforme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Visual C++ pour le développement mobile multiplateforme] (http://go.microsoft.com/fwlink/p/?LinkId=536383) est un composant installable de Visual Studio 2015. Il inclut des modèles Visual Studio multiplateformes et installe les outils multiplateformes ainsi que les Kits de développement logiciel pour une prise en main rapide, sans que vous n’ayez à effectuer les recherches, le téléchargement ni la configuration. Vous pouvez utiliser ces outils dans Visual Studio pour créer, modifier, déboguer et tester facilement des projets multiplateformes. Cette rubrique décrit comment installer les outils et les logiciels tiers requis pour développer des applications multiplateformes à l’aide de Visual Studio. Pour obtenir une vue d’ensemble du composant, consultez [Développement multiplateforme en Visual C++ pour appareils mobiles](http://go.microsoft.com/fwlink/p/?LinkId=536387)  
  
 [Spécifications](#Requirements)   
 [Se procurer les outils](#GetTheTools)   
 [Installer les outils](#InstallTheTools)   
 [Install tools for iOS](#InstallForiOS)   
 [Installer ou mettre à jour manuellement les dépendances](#ThirdParty)  
  
##  <a name="Requirements"></a> Spécifications  
  
- Pour connaître la configuration requise pour l’installation, consultez [Configuration système requise pour Visual Studio 2015](https://www.visualstudio.com/visual-studio-2015-system-requirements-vs).  
  
  > [!IMPORTANT]
  >  Si vous utilisez Windows 7 ou Windows Server 2008 R2, vous pouvez développer du code pour les applications Windows classiques, pour les applications et les bibliothèques Android Native Activity, et pour les applications et les bibliothèques de code pour iOS, mais pas pour les applications Windows Store ni Windows universelles.  
  
  Pour créer des applications pour des plateformes d’appareils spécifiques, il y a quelques spécifications requises supplémentaires :  
  
- Les émulateurs Windows Phone et l’émulateur Microsoft Visual Studio pour Android requièrent un ordinateur qui peut exécuter Hyper-V. La fonctionnalité Hyper-V de Windows doit être activée pour permettre l’installation et l’exécution des émulateurs. Pour plus d’informations, consultez la [configuration requise](http://msdn.microsoft.com/4d5bb438-231a-4cd2-84b7-e9660b0e3baf) de l’émulateur.  
  
- Les émulateurs Android x86 fournis avec le SDK Android offrent des performances optimales sur des ordinateurs pouvant exécuter le pilote Intel HAXM. Ce pilote nécessite un processeur Intel x64 avec prise en charge de Execute Disable Bit et de VT-x. Pour plus d’informations, consultez les [Instructions d’installation pour le gestionnaire d’exécution à accélération matérielle Intel® - Microsoft Windows](http://go.microsoft.com/fwlink/p/?LinkId=536385).  
  
- La génération du code pour iOS nécessite un identifiant Apple, un compte iOS Developer Program et un ordinateur Mac pouvant exécuter [Xcode 6](http://go.microsoft.com/fwlink/p/?LinkId=536387) (ou ultérieur) sur OS X Mavericks (ou ultérieur). Pour obtenir une procédure d’installation simple, consultez [Install tools for iOS](#InstallForiOS).  
  
##  <a name="GetTheTools"></a> Obtenir les outils  
 Visual C++ pour le développement mobile multiplateforme est un composant installable inclus dans les éditions Visual Studio Community, Professional et Enterprise. Pour obtenir Visual Studio, accédez à la page [Téléchargements de Visual Studio 2015](http://go.microsoft.com/fwlink/p/?linkid=517106) et téléchargez Visual Studio 2015 avec Update 2 ou version ultérieure.  
  
##  <a name="InstallTheTools"></a> Installer les outils  
 Le programme d’installation de Visual Studio 2015 comprend une option d’installation de Visual C++ pour le développement mobile multiplateforme. Cette option installe les outils, modèles et composants de langage C++ pour les ensembles d’outils Visual Studio, GCC et Clang nécessaires aux builds Android et au débogage, ainsi que les composants permettant de communiquer avec un Mac pour le développement iOS. Elle installe également tous les outils tiers et kits de développement logiciel qui sont requis pour prendre en charge le développement d’applications iOS et Android. La plupart de ces outils tiers sont des logiciels open source nécessaires pour la prise en charge de la plateforme Android.  
  
-   Android NDK (Native Development Kit) est obligatoire pour générer du code C++ qui cible la plateforme Android.  
  
-   Le SDK Android, Apache Ant et le Kit de développement Java SE sont requis dans le processus de génération Android.  
  
-   L’émulateur Microsoft Visual Studio pour Android est un émulateur à hautes performances facultatif utile pour tester et déboguer votre code.  
  
#### <a name="to-install-visual-c-for-cross-platform-mobile-development-and-the-third-party-tools"></a>Pour installer Visual C++ pour le développement mobile multiplateforme et les outils tiers  
  
1.  Exécutez le programme d’installation de Visual Studio 2015 que vous avez téléchargé en suivant le lien dans [Se procurer les outils](#GetTheTools). Pour installer les composants facultatifs, choisissez **Personnalisé** comme type d’installation. Choisissez **Suivant** pour sélectionner les composants facultatifs à installer.  
  
2.  Dans Sélectionner les fonctionnalités, développez **Développement mobile multiplateforme** et cochez **Développement mobile Visual C++**.  
  
     ![Sélectionner Développement mobile Visual C&#43;&#43;](../cross-platform/media/cppmdd-install-vcmdd.png "CPPMDD_Install_VCMDD")  
  
     Par défaut, quand vous sélectionnez **Développement mobile Visual C++**, l’option **Langages de programmation** est définie pour installer **Visual C++**. De plus, l’option **Kits de développement logiciel (SDK) et outils courants** est définie pour installer les composants tiers nécessaires. Vous pouvez choisir des composants supplémentaires si vous en avez besoin. Par défaut, **Émulateur Microsoft Visual Studio pour Android** est également sélectionné. Les composants qui sont déjà installés apparaissent inactifs dans la liste.  
  
     Pour générer des applications Windows universelles et partager du code entre ces applications et vos projets Android et iOS, dans **Sélectionner les fonctionnalités**, développez **Développement d’applications Windows et web**, puis cochez **Outils de développement d’applications Windows universelles**. Si vous ne prévoyez pas de créer des applications Windows universelles, vous pouvez ignorer cette option.  
  
     Choisissez **Suivant** pour continuer.  
  
3.  Les composants tiers ont leurs propres termes du contrat de licence. Vous pouvez afficher les termes du contrat de licence en cliquant sur le lien **Termes du contrat de licence** en regard de chaque composant. Choisissez **Installer** pour ajouter les composants et installer Visual Studio et Visual C++ pour le développement mobile multiplateforme.  
  
4.  À la fin de l’installation, fermez le programme d’installation, puis redémarrez l’ordinateur. Certaines actions d’installation des composants tiers ne prennent pas effet tant que l’ordinateur n’a pas redémarré.  
  
    > [!IMPORTANT]
    >  Vous devez redémarrer pour vous assurer que tout est installé correctement.  
  
     Si l’installation du composant Émulateur Microsoft Visual Studio pour Android ne peut pas s’effectuer, il est possible qu’Hyper-V ne soit pas activé sur votre ordinateur. Utilisez l’application du Panneau de configuration **Activer ou désactiver des fonctionnalités Windows** pour activer Hyper-V, puis réexécutez le programme d’installation de Visual Studio.  
  
    > [!NOTE]
    >  Si votre ordinateur ou votre version de Windows ne prend pas en charge Hyper-V, vous ne pouvez pas utiliser le composant Émulateur Microsoft Visual Studio pour Android. L’Édition familiale de Windows n’inclut pas la prise en charge d’Hyper-V.  
  
5.  Ouvrez Visual Studio. S’il s’agit de la première exécution de Visual Studio, la configuration et la connexion peuvent prendre un certain temps. Quand Visual Studio est prêt, dans le menu **Outils** , sélectionnez **Extensions et mises à jour**, **Mises à jour**. Si des mises à jour Visual Studio sont disponibles pour Développement multiplateforme en Visual C++ pour appareils mobiles ou pour l’émulateur Microsoft Visual Studio pour Android, installez-les.  
  
##  <a name="InstallForiOS"></a> Install tools for iOS  
 Vous pouvez utiliser Visual C++ pour le développement mobile multiplateforme pour modifier, déboguer du code iOS et ensuite le déployer dans le simulateur iOS ou sur un appareil iOS mais, en raison de restrictions de licences, le code doit être généré à distance sur un Mac. Pour générer et exécuter des applications iOS à l’aide de Visual Studio, vous devez installer et configurer l’agent distant sur votre Mac. Pour obtenir des instructions d’installation détaillées, les conditions préalables et les options de configuration, consultez [Install And Configure Tools to Build using iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Si vous ne générez pas pour iOS, vous pouvez ignorer cette étape.  
  
##  <a name="ThirdParty"></a> Installer ou mettre à jour manuellement les dépendances  
 Si vous décidez de ne pas installer une ou plusieurs dépendances tierces à l’aide du programme d’installation de Visual Studio quand vous installez l’option Développement en Visual C++ pour appareils mobiles, vous pouvez les installer ultérieurement à l’aide de la procédure décrite dans [Install the tools](#InstallTheTools). Vous pouvez également les installer ou les mettre à jour indépendamment de Visual Studio.  
  
> [!CAUTION]
>  Vous pouvez installer les dépendances dans n’importe quel ordre, excepté pour Java. Vous devez installer et configurer le JDK avant d’installer le Kit de développement logiciel (SDK) Android.  
  
 Lisez les informations suivantes et utilisez ces liens pour installer des dépendances manuellement.  
  
- [Kit de développement Java SE](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)  
  
   Par défaut, le programme d’installation place les outils Java dans C:\Program Files (x86)\Java.  
  
- [Kit de développement logiciel Android SDK](https://developer.android.com/sdk/index.html#Other)  
  
   Lors de l’installation, mettez à jour les API comme recommandé. Vérifiez que le kit SDK pour Android 5.0 Lollipop (niveau d’API 21), ou version ultérieure, est installé. Par défaut, le programme d’installation place le SDK Android dans C:\Program Files (x86)\Android\android-sdk.  
  
   Vous pouvez réexécuter l’application SDK Manager dans le répertoire Android SDK pour mettre à jour le kit SDK et installer des outils facultatifs, ainsi que des niveaux d’API supplémentaires. L’installation des mises à jour risque d’échouer, sauf si vous utilisez **Exécuter en tant qu’administrateur** pour exécuter l’application du Gestionnaire du SDK. Si vous rencontrez des problèmes lors de la génération d’une application Android, recherchez des mises à jour pour les kits SDK installés dans le Gestionnaire du SDK.  
  
   Pour utiliser certains émulateurs Android fournis avec le kit SDK Android, vous devez installer les pilotes Intel HAXM facultatifs. Vous devrez peut-être supprimer la fonctionnalité Hyper-V de Windows pour installer correctement les pilotes Intel HAXM. Vous devez restaurer la fonctionnalité Hyper-V pour utiliser les émulateurs Windows Phone et l’émulateur Microsoft Visual Studio pour Android.  
  
- [Kit de développement natif (NDK) Android](https://developer.android.com/tools/sdk/ndk/index.html)  
  
   Par défaut, le programme d’installation place le Kit de développement natif (NDK) Android dans C:\ProgramData\Microsoft\AndroidNDK. Vous pouvez retélécharger et réinstaller le Kit de développement natif (NDK) Android pour mettre à jour son installation.  
  
- [Apache Ant](http://ant.apache.org/bindownload.cgi)  
  
   Par défaut, le programme d’installation place Apache Ant dans C:\Program Files (x86)\Microsoft Visual Studio 14.0\Apps.  
  
- [Émulateur Microsoft Visual Studio pour Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/)  
  
   Vous pouvez installer et mettre à jour l’émulateur Microsoft Visual Studio pour Android à partir de la galerie Visual Studio.  
  
  Dans la plupart des cas, Visual Studio peut détecter les configurations pour les logiciels tiers que vous avez installés et gère les chemins d’installation dans des variables d’environnement internes. Vous pouvez remplacer les chemins par défaut de ces outils de développement multiplateformes dans l’IDE de Visual Studio.  
  
#### <a name="to-set-the-paths-for-third-party-tools"></a>Pour définir les chemins des outils tiers  
  
1.  Dans la barre de menus Visual Studio, choisissez **Outils**, **Options**.  
  
2.  Dans la boîte de dialogue **Options** , développez **Multiplateforme**, **C++**, puis sélectionnez **Android**.  
  
     ![Options de chemin de l’outil Android](../cross-platform/media/cppmdd-options-android.PNG "CPPMDD_Options_Android")  
  
3.  Pour modifier le chemin utilisé par un outil, cochez la case en regard du chemin et modifiez le chemin du dossier dans la zone de texte. Vous pouvez également utiliser le bouton Parcourir (**...**) pour ouvrir une boîte de dialogue **Sélectionner un emplacement** et choisir le dossier.  
  
4.  Choisissez **OK** pour enregistrer les emplacements des dossiers d’outils personnalisés.  
  
## <a name="see-also"></a>Voir aussi  
 [Installer et configurer des outils de génération en utilisant iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)   
 [Développement multiplateforme en Visual C++ pour appareils mobiles](https://www.visualstudio.com/explore/cplusplus-mdd-vs.aspx)
