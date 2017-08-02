---
title: "Cr&#233;er des applications interplateformes avec Visual C++ | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 44c16342-6951-4852-95b0-b97ae858ee50
caps.latest.revision: 13
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Cr&#233;er des applications interplateformes avec Visual C++
Vous pouvez générer du code multiplateforme pour des appareils Android, iOS et Windows à l'aide de Visual for Cross\-Platform Mobile Development.  Il s'agit d'une fonctionnalité facultative disponible dans Visual Studio 2015, qui permet le développement multiplateforme de code pour iOS, Android et Windows à l'aide de Visual C\+\+.  
  
 Vous pouvez utiliser Visual Studio pour générer des bibliothèques partagées de code C\+\+ standard pour les applications Windows classiques pour les applications universelles Windows, et pour les plateformes iOS et Android.  Vous pouvez générer des applications natives pour les plateformes Windows et Android uniquement à l'aide de Visual C\+\+ et des outils tiers intégrés à Visual Studio.  Si vous avez un ordinateur Mac, vous pouvez utiliser Visual Studio pour créer et déboguer du code C\+\+ pour les applications iOS qui sont créées et déployées sur votre Mac.  
  
> [!NOTE]
>  Visual C\+\+ for Cross\-Platform Mobile Development prend en charge le niveau d'API Android 19 et 21, avec le ciblage d'Android 4.4 et 5.0.  D'autres niveaux d'API peuvent être installés avec le gestionnaire du Kit de développement logiciel \(SDK\).  Le débogueur Android Visual Studio C\+\+ requiert que les émulateurs ou appareils cibles exécutent au minimum le niveau d'API Android 17 \(version 4.2\) ou plus récent.  
  
 Cet article décrit comment créer des applications multiplateformes à l'aide de Visual C\+\+ for Cross\-Platform Mobile Development dans Visual Studio 2015 :  
  
 [Configuration requise](#req)   
 [Se procurer les outils](#GetTools)  
 [Créer un projet Android Native Activity](#Create)  
 [Générer et exécuter l'application Android Native Activity](#BuildHello)  
  
##  <a name="req"></a> Configuration requise  
  
-   Pour connaître la configuration requise pour l'installation, consultez [Configuration système requise pour Visual Studio 2015](https://www.visualstudio.com/visual-studio-2015-system-requirements-vs).  
  
    > [!IMPORTANT]
    >  Si vous utilisez Windows 7 ou Windows Server 2008 R2, vous pouvez développer du code pour les applications Windows classiques, pour les applications et les bibliothèques de code Android Native Activity, et pour les applications et les bibliothèques de code pour iOS, mais pas pour le Windows Store ou les applications Windows universelles.  
  
 Pour créer des applications pour des plateformes d'appareils spécifiques, il y a quelques spécifications requises supplémentaires :  
  
-   L'émulateur Visual Studio pour Android et les émulateurs Windows Phone requièrent un ordinateur qui peut exécuter Hyper\-V.  Pour plus d'informations, consultez la [configuration système requise](http://msdn.microsoft.com/fr-fr/4d5bb438-231a-4cd2-84b7-e9660b0e3baf) de l'émulateur.  
  
-   Les émulateurs Android x86 fournis avec le SDK Android offrent des performances optimales sur des ordinateurs pouvant exécuter le pilote Intel HAXM.  Ce pilote nécessite un processeur Intel x64 avec prise en charge de Execute Disable Bit et de VT\-x.  Pour plus d'informations, consultez les [Instructions d'installation pour le gestionnaire d'exécution à accélération matérielle Intel® \- Microsoft Windows](http://go.microsoft.com/fwlink/p/?LinkId=536385).  
  
-   La génération d'applications pour iOS nécessite un compte iOS Developer Program et un ordinateur Mac pouvant exécuter Xcode 6.  
  
##  <a name="GetTools"></a> Se procurer les outils  
 Visual C\+\+ for Cross\-Platform Mobile Development est un composant facultatif inclus dans Visual Studio 2015.  Pour obtenir Visual Studio, accédez à la page [Téléchargements de Visual Studio 2015](http://go.microsoft.com/fwlink/?linkid=517106) et téléchargez Visual Studio 2015.  
  
 Le programme d'installation de Visual Studio 2015 comprend une option de prise en charge du développement multiplateforme pour appareils mobiles.  Cette option permet d'installer le développement en Visual C\+\+ pour appareils mobiles ainsi que les outils et Kits de développement logiciel \(SDK\) courants suivants.  La plupart d'entre eux sont des logiciels open source nécessaires pour la prise en charge multiplateforme.  
  
-   Android NDK \(Native Development Kit\) \(R10E, 32 bits\) est requis dans le processus de génération Android.  
  
-   Le SDK Android, Apache Ant et le Kit de développement Java SE sont requis dans le processus de génération Android.  
  
-   L'émulateur Microsoft Visual Studio pour Android est un émulateur rapide et compatible pour le développement Android.  
  
 Pour obtenir des instructions d'installation détaillées, consultez [Installer Visual C\+\+ pour le développement mobile multiplateforme](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md).  
  
 Pour générer du code pour iOS, vous devez installer et configurer un agent de build distant sur votre Mac et vous y connecter dans Visual Studio.  Pour obtenir des instructions détaillées d'installation et de configuration, consultez [Installer et configurer des outils de génération en utilisant iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
##  <a name="Create"></a> Créer un projet Android Native Activity  
 Vous pouvez utiliser Visual C\+\+ for Cross\-Platform Mobile Development pour créer, générer, exécuter et déboguer une application Android complète en utilisant C\+\+.  Visual Studio comprend un modèle pour un projet Android Native Activity qui peut vous aider à démarrer.  
  
 Dans ce didacticiel, vous allez d'abord créer un projet, puis générer et exécuter l'application par défaut.  
  
 Avant de pouvoir créer un projet, assurez\-vous que vous disposez de la configuration système requise et que vous avez installé Visual C\+\+ for Cross\-Platform Mobile Development for Visual Studio.  Pour plus d'informations, consultez [Installer Visual C\+\+ pour le développement mobile multiplateforme](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md).  
  
#### Pour créer un projet  
  
1.  Ouvrez Visual Studio.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet**, sous **Modèles**, choisissez **Visual C\+\+**, **Interplateforme**, puis choisissez le modèle **Application d'activité native \(Android\)**.  
  
3.  Donnez à l'application un nom comme `MonApplicationAndroid`, puis choisissez **OK**.  
  
     ![Créer un projet d'activité native](../cross-platform/media/cppmdd_newproject.PNG "CppMDD\_NewProject")  
  
     Visual Studio crée la solution et ouvre l'Explorateur de solutions.  
  
 La nouvelle solution Application d'activité native Android comprend deux projets :  
  
-   **MonApplicationAndroid.NativeActivity** contient les références et le code de type glue pour que votre application s'exécute comme Activité native sur Android.  L'implémentation des points d'entrée à partir du code de type glue se trouve dans main.cpp.  Les en\-têtes précompilés sont dans pch.h.  Votre projet d'application est compilé en un fichier de bibliothèque partagée \(.so\), qui est utilisé par le projet de package.  
  
-   **MyAndroidApp.Packaging** crée le fichier de package \(.apk\) pour le déploiement sur un émulateur ou un appareil Android.  Il contient les ressources et le fichier AndroidManifest.xml où vous avez défini les propriétés de manifeste.  Il contient aussi le fichier build.xml qui contrôle le processus de génération Ant.  Il est configuré comme projet de démarrage par défaut et peut donc être déployé et exécuté directement à partir de Visual Studio.  
  
##  <a name="BuildHello"></a> Générer et exécuter l'application Android Native Activity  
 Générez et exécutez l'application générée par le modèle pour vérifier votre installation et votre configuration.  Par défaut, le modèle définit Debug comme configuration de solution et x86 comme plateforme de solution pour exécuter l'application sur l'émulateur Microsoft Visual Studio pour Android.  Si vous préférez tester votre application sur une autre cible, chargez l'émulateur cible ou connectez votre appareil à votre ordinateur.  
  
#### Pour générer et exécuter l'application Native Activity par défaut  
  
1.  Dans la barre de menus, choisissez **Générer**, puis **Générer la solution**.  
  
     La fenêtre **Sortie** affiche la sortie du processus de génération pour les deux projets de la solution.  
  
2.  Sélectionnez l'un des profils d'émulateur Visual Studio comme cible de déploiement.  
  
     Si vous avez installé d'autres émulateurs ou si vous avez connecté un appareil Android, vous pouvez les choisir dans la liste déroulante de cible de déploiement.  
  
3.  Appuyez sur F5 pour démarrer le débogage, ou sur Maj\+F5 pour démarrer sans débogage.  
  
     Voici à quoi ressemble l'application par défaut dans l'émulateur Visual Studio pour Android.  
  
     ![Émulateur exécutant votre application](~/docs/cross-platform/media/cppmdd_emulator_running_app.PNG "CppMDD\_Emulator\_Running\_App")  
  
    > [!TIP]
    >  Visual Studio démarre l'émulateur qui, après quelques secondes, charge et déploie votre code.  Une fois l'application démarrée, vous pouvez définir des points d'arrêt et utiliser le débogueur pour parcourir le code, examiner les variables locales et observer les valeurs.  
  
4.  Appuyez sur Maj\+F5 pour arrêter le débogage.  
  
     L'émulateur est un processus distinct qui continue à s'exécuter.  Vous pouvez modifier, compiler et déployer votre code plusieurs fois sur le même émulateur.  
  
## Voir aussi  
 [Télécharger Visual Studio 2015](http://go.microsoft.com/fwlink/?linkid=517106)