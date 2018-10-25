---
title: Générer une application OpenGL ES sur Android et iOS | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: 76a67886-df57-4a81-accb-2e3c2eaf607b
caps.latest.revision: 7
author: BrianPeek
ms.author: brpeek
manager: ghogen
ms.openlocfilehash: 3788c85f0e176f55f062869a1001fb7c1c35101d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812957"
---
# <a name="build-an-opengl-es-application-on-android-and-ios"></a>Générer une application OpenGL ES sur Android et iOS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Quand vous installez l’option Développement multiplateforme en Visual C++ pour appareils mobiles, vous pouvez créer des solutions et des projets Visual Studio pour des applications iOS et Android qui partagent du code commun. Cette rubrique vous guide tout au long d’un modèle de solution qui crée une application iOS simple et une application Android Native Activity. Les applications ont en commun une partie de code C++ qui utilise OpenGL ES pour afficher le même cube pivotant animé sur chaque plateforme. OpenGL ES (OpenGL for Embedded Systems ou GLES) est une API graphique 2D et 3D qui est prise en charge par de nombreux appareils mobiles.  
  
 [Configuration requise](#req)   
 [Créer un projet Application OpenGLES](#Create)   
 [Générer et exécuter l’application Android](#BuildAndroid)   
 [Générer et exécuter l’application iOS](#BuildIOS)   
 [Personnaliser vos applications](#Customize)  
  
##  <a name="req"></a> Configuration requise  
 Avant de pouvoir créer une application OpenGL ES pour iOS et Android, vous devez vous assurer que votre système répond à la configuration requise. Vous devez installer l’option Visual C++ pour le développement mobile multiplateforme dans Visual Studio 2015. Assurez-vous que les SDK et les outils tiers requis sont inclus dans l’installation, et que l’Émulateur Visual Studio pour Android est installé. Pour obtenir plus d’informations et des instructions détaillées, consultez [Install Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Pour générer et tester l’application iOS, vous devez disposer d’un ordinateur Mac configuré conformément aux instructions d’installation. Pour plus d’informations sur la configuration requise pour développer du code pour iOS, consultez [Install And Configure Tools to Build using iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)  
  
##  <a name="Create"></a> Créer un projet Application OpenGLES  
 Dans ce didacticiel, vous allez tout d’abord créer un projet Application OpenGLES, puis vous allez générer et exécuter l’application par défaut dans l’Émulateur Visual Studio pour Android. Ensuite, vous allez générer l’application pour iOS et exécuter l’application dans iOS Simulator.  
  
#### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
1. Ouvrez Visual Studio. Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
2. Dans la boîte de dialogue **Nouveau projet** , sous **Modèles**, choisissez **Visual C++**, **Interplateforme**, puis choisissez le modèle **Application OpenGLES (Android, iOS)** .  
  
3. Donnez à l’application un nom, par exemple `MyOpenGLESApp`, puis choisissez **OK**.  
  
    ![Nouveau projet d’application OpenGLES](../cross-platform/media/cppmdd-opengles-newproj.PNG "CPPMDD_OpenGLES_NewProj")  
  
    Visual Studio crée la solution et ouvre l’Explorateur de solutions.  
  
    ![MyOpenGLESApp dans l’Explorateur de solutions](../cross-platform/media/cppmdd-opengles-solexpl.PNG "CPPMDD_OpenGLES_SolExpl")  
  
   La nouvelle solution Application OpenGLES comprend trois projets de bibliothèque et deux projets d’application. Le dossier de bibliothèques inclut un projet de code partagé et deux projets spécifiques à la plateforme qui référencent le code partagé :  
  
- **MyOpenGLESApp.Android.NativeActivity** contient les références et le code de type glue qui implémente votre application en tant que Native Activity sur Android. L’implémentation des points d’entrée à partir du code de type glue se trouve dans main.cpp, qui comprend le code commun partagé dans MyOpenGLESApp.Shared. Les en-têtes précompilés sont dans pch.h. Ce projet d’application Native Activity est compilé en fichier de bibliothèque partagée (.so), qui est utilisé par le projet MyOpenGLESApp.Android.Packaging.  
  
- **MyOpenGLESApp.iOS.StaticLibrary** crée un fichier de bibliothèque statique (.a) iOS qui contient le code partagé dans MyOpenGLESApp.Shared. Il est lié à l’application créée par le projet MyOpenGLESApp.iOS.Application.  
  
- **MyOpenGLESApp.Shared** contient le code partagé qui fonctionne sur plusieurs plateformes. Il utilise des macros de préprocesseur pour compiler de façon conditionnelle le code spécifique à la plateforme. Le code partagé est récupéré par la référence de projet dans MyOpenGLESApp.Android.NativeActivity et MyOpenGLESApp.iOS.StaticLibrary.  
  
  La solution comporte deux projets visant à générer des applications pour les plateformes Android et iOS :  
  
- **MyOpenGLESApp.Android.Packaging** crée le fichier .apk pour le déploiement sur un émulateur ou un appareil Android. Il contient les ressources et le fichier AndroidManifest.xml où vous avez défini les propriétés de manifeste. Il contient aussi le fichier build.xml qui contrôle le processus de génération Ant. Il est configuré comme projet de démarrage par défaut et peut donc être déployé et exécuté directement à partir de Visual Studio.  
  
- **MyOpenGLESApp.iOS.Application** contient les ressources et le code de type glue Objective-C nécessaires pour créer une application iOS liée au code de la bibliothèque statique C++ dans MyOpenGLESApp.iOS.StaticLibrary. Ce projet crée un package de build qui est transféré vers votre Mac par Visual Studio et l’agent distant. Quand vous générez ce projet, Visual Studio envoie les fichiers et les commandes pour générer et déployer votre application sur le Mac.  
  
##  <a name="BuildAndroid"></a> Générer et exécuter l’application Android  
 La solution créée par le modèle définit l’application Android en tant que projet par défaut.  Vous pouvez générer et exécuter cette application pour vérifier votre installation et votre configuration. Pour un test initial, exécutez l’application sur l’un des profils d’appareils installés par l’Émulateur Visual Studio pour Android. Si vous préférez tester votre application sur une autre cible, vous pouvez charger l’émulateur cible ou connecter l’appareil à votre ordinateur.  
  
#### <a name="to-build-and-run-the-android-native-activity-app"></a>Pour générer et exécuter l’application Android Native Activity  
  
1. Si ce n’est pas déjà fait, choisissez **x86** dans la liste déroulante **Plateformes Solution** .  
  
    ![Définir la plateforme de solution x86](../cross-platform/media/cppmdd-opengles-solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")  
  
    Utilisez x86 pour cibler l’émulateur Android pour Windows. Si vous ciblez un appareil, choisissez la plateforme de solution basée sur le processeur de l’appareil. Si la liste **Plateformes Solution** n’est pas visible, choisissez **Plateformes Solution** dans la liste **Ajouter/supprimer des boutons** , puis choisissez votre plateforme.  
  
2. Dans l’ **Explorateur de solutions**, ouvrez le menu contextuel du projet MyOpenGLESApp.Android.Packaging, puis choisissez **Générer**.  
  
    ![Générer un projet de package Android](../cross-platform/media/cppmdd-opengles-andbuild.png "CPPMDD_OpenGLES_AndBuild")  
  
    La fenêtre Sortie affiche la sortie du processus de génération pour la bibliothèque partagée Android et l’application Android.  
  
    ![Générer la sortie de projets Android](../cross-platform/media/cppmdd-opengles-andoutput.png "CPPMDD_OpenGLES_AndOutput")  
  
3. Sélectionnez l’un des profils Émulateur VS Android Phone (x86) comme cible de déploiement.  
  
    ![Choisir une cible de déploiement](../cross-platform/media/cppmdd-opengles-pickemulator.png "CPPMDD_OpenGLES_PickEmulator")  
  
    Si vous avez installé d’autres émulateurs ou si vous avez connecté un appareil Android, vous pouvez les choisir dans la liste déroulante de cible de déploiement. Pour exécuter l’application, la Plateforme Solution intégrée doit correspondre à la plateforme de l’appareil cible.  
  
4. Appuyez sur F5 pour démarrer le débogage, ou sur Maj+F5 pour démarrer sans débogage.  
  
    Visual Studio démarre l’émulateur qui, après quelques secondes, charge et déploie votre code. Voici comment l’application apparaît dans l’émulateur Visual Studio pour Android.  
  
    ![Application en cours d’exécution dans l’émulateur Android](../cross-platform/media/cppmdd-opengles-andemulator.png "CPPMDD_OpenGLES_AndEmulator")  
  
    Une fois l’application démarrée, vous pouvez définir des points d’arrêt et utiliser le débogueur pour parcourir le code, examiner les variables locales et observer les valeurs.  
  
5. Appuyez sur Maj+F5 pour arrêter le débogage.  
  
    L’émulateur est un processus distinct qui continue à s’exécuter. Vous pouvez modifier, compiler et déployer votre code plusieurs fois sur le même émulateur. Vous pouvez démarrer votre application directement à partir de la collection d’applications dans laquelle elle apparaît sur l’émulateur.  
  
   Les projets de bibliothèque et d’application Android Native Activity générés placent le code C++ partagé dans une bibliothèque dynamique qui contient du code de type « glue » pour interagir avec la plateforme Android. Cela signifie que la majeure partie du code d’application se trouve dans la bibliothèque, et que le manifeste, les ressources et les instructions de génération se trouvent dans le projet de création de package. Le code partagé est appelé à partir de main.cpp dans le projet NativeActivity. Pour plus d’informations sur la programmation d’une activité Android Native Activity, consultez la page [Concepts](https://developer.android.com/ndk/guides/concepts.html) du NDK Android.  
  
   Visual Studio génère les projets Android Native Activity à l’aide du NDK Android, ce dernier utilisant l’ensemble d’outils de plateforme Clang. Visual Studio mappe les propriétés du projet NativeActivity aux commutateurs et options de ligne de commande servant aux opérations de compilation, de liaison et de débogage sur la plateforme cible. Pour plus d’informations, ouvrez la boîte de dialogue **Pages de propriétés** pour le projet MyOpenGLESApp.Android.NativeActivity. Pour plus d’informations sur les commutateurs de ligne de commande, consultez le [manuel de l’utilisateur du compilateur Clang](http://clang.llvm.org/docs/UsersManual.html).  
  
##  <a name="BuildIOS"></a> Générer et exécuter l’application iOS  
 Le projet d’application iOS est créé et modifié dans Visual Studio, mais du fait de restrictions de licences, il doit être créé et déployé sur un Mac. Visual Studio communique avec un agent distant s’exécutant sur le Mac pour transférer les fichiers du projet et exécuter les commandes de génération, de déploiement et de débogage. Vous devez installer et configurer votre Mac et Visual Studio pour communiquer avant de générer l’application iOS. Pour obtenir des instructions détaillées, consultez [Install And Configure Tools to Build using iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Une fois que l’agent distant est en cours d’exécution et que Visual Studio est associé à votre Mac, vous pouvez générer et exécuter l’application iOS pour vérifier votre installation et votre configuration.  
  
#### <a name="to-build-and-run-the-ios-app"></a>Pour générer et exécuter l’application iOS  
  
1. Vérifiez que l’agent distant est en cours d’exécution sur votre Mac et que Visual Studio est associé à l’agent distant. Pour démarrer l’agent distant, ouvrez une fenêtre d’application Terminal et entrez `vcremote`. Pour plus d’informations, consultez [Configurer l’agent distant dans Visual Studio](../cross-platform/install-and-configure-tools-to-build-using-ios.md#ConfigureVS).  
  
    ![Fenêtre Terminal Mac exécutant vcremote](../cross-platform/media/cppmdd-common-vcremote.png "CPPMDD_common_vcremote")  
  
2. Si ce n’est pas déjà fait, choisissez **x86** dans la liste déroulante **Plateformes Solution** .  
  
    ![Définir la plateforme de solution x86](../cross-platform/media/cppmdd-opengles-solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")  
  
    Utilisez x86 pour cibler iOS Simulator. Si vous ciblez un appareil iOS, choisissez la plateforme de solution basée sur le processeur de l’appareil (en général, il s’agit d’un processeur ARM). Si la liste **Plateformes Solution** n’est pas visible, choisissez **Plateformes Solution** dans la liste **Ajouter/supprimer des boutons** , puis choisissez votre plateforme.  
  
3. Dans l’Explorateur de solutions, ouvrez le menu contextuel du projet MyOpenGLESApp.iOS.Application, puis choisissez **Générer**.  
  
    ![Générer un projet d’application iOS](../cross-platform/media/cppmdd-opengles-iosbuild.png "CPPMDD_OpenGLES_iOSBuild")  
  
    La fenêtre Sortie affiche la sortie du processus de génération pour la bibliothèque statique iOS et l’application iOS. Sur le Mac, la fenêtre Terminal exécutant l’agent distant affiche la commande et l’activité de transfert de fichier.  
  
    Sur votre ordinateur Mac, vous pouvez être invité à accepter une demande de signature de code. Cliquez sur Autoriser pour continuer.  
  
4. Choisissez **iOS Simulator** dans la barre d’outils pour exécuter l’application dans iOS Simulator sur votre Mac. Le démarrage du simulateur peut prendre quelques instants. Vous devrez peut-être mettre le simulateur au premier plan sur votre Mac pour visualiser sa sortie.  
  
    ![Application en cours d’exécution sur le simulateur iOS](../cross-platform/media/cppmdd-opengles-iossimulator.png "CPPMDD_OpenGLES_iOSSimulator")  
  
    Une fois l’application démarrée, vous pouvez définir des points d’arrêt et utiliser le débogueur Visual Studio pour examiner les variables locales, consulter la pile des appels et observer les valeurs.  
  
    ![Débogueur au point d’arrêt dans une application iOS](../cross-platform/media/cppmdd-opengles-iosdebug.png "CPPMDD_OpenGLES_iOSDebug")  
  
5. Appuyez sur Maj+F5 pour arrêter le débogage.  
  
    iOS Simulator est un processus distinct qui continue à s’exécuter sur votre Mac. Vous pouvez modifier, compiler et déployer votre code plusieurs fois sur la même instance d’iOS Simulator. Vous pouvez également exécuter votre code directement dans le simulateur une fois le déploiement terminé.  
  
   Les projets de bibliothèque et d’application iOS générés placent le code C++ dans une bibliothèque statique qui implémente uniquement le code partagé. La majeure partie du code d’application se trouve dans le projet Application. Les appels au code de bibliothèque partagée dans ce modèle de projet sont effectués dans le fichier GameViewController.m. Pour générer votre application iOS, Visual Studio utilise l’ensemble d’outils de plateforme Xcode, celui-ci nécessitant une communication avec un client distant qui s’exécute sur un Mac.  
  
   Visual Studio transfère les fichiers de projet et envoie les commandes au client distant pour générer l’application à l’aide de la plateforme Xcode. Le client distant renvoie les informations d’état de build à Visual Studio. Une fois l’application générée, vous pouvez utiliser Visual Studio pour envoyer des commandes en vue d’exécuter et de déboguer l’application. Le débogueur dans Visual Studio contrôle l’application en cours d’exécution dans iOS Simulator (sur votre Mac) ou sur un appareil iOS attaché. Visual Studio mappe les propriétés du projet StaticLibrary aux commutateurs et options de ligne de commande servant aux opérations de génération, de liaison et de débogage sur la plateforme iOS cible. Pour obtenir les détails de l’option de ligne de commande du compilateur, ouvrez la boîte de dialogue **Pages de propriétés** du projet MyOpenGLESApp.iOS.StaticLibrary.  
  
##  <a name="Customize"></a> Personnaliser vos applications  
 Vous pouvez modifier le code C++ partagé pour ajouter ou modifier des fonctionnalités communes. Vous devez modifier les appels au code partagé dans les projets MyOpenGLESApp.Android.NativeActivity et MyOpenGLESApp.iOS.Application pour les faire correspondre. Vous pouvez utiliser des macros de préprocesseur pour spécifier des sections spécifiques à la plateforme dans votre code commun. La macro de préprocesseur `__ANDROID__` est prédéfinie quand vous générez pour Android. La macro de préprocesseur `__APPLE__` est prédéfinie quand vous générez pour iOS.  
  
 Pour bénéficier de la fonctionnalité IntelliSense pour une plateforme de projet spécifique, choisissez le projet dans la liste déroulante du sélecteur de contexte dans la barre Navigation en haut de la fenêtre de l’éditeur.  
  
 ![Liste déroulante du sélecteur de contexte de projet dans l’éditeur](../cross-platform/media/cppmdd-opengles-contextswitcher.png "CPPMDD_OpenGLES_ContextSwitcher")  
  
 Les problèmes IntelliSense dans le projet actuel sont signalés par un trait ondulé rouge. Les problèmes dans d’autres projets sont signalés par un trait ondulé violet. Par défaut, Visual Studio ne prend en charge ni la colorisation de code ni IntelliSense pour les fichiers Java ou Objective-C. Toutefois, vous pouvez modifier les fichiers sources et les ressources pour définir le nom de votre application, son icône et d’autres détails d’implémentation.

