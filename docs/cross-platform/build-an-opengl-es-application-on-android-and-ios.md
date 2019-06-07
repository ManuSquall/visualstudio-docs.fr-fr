---
title: Générer une application OpenGL ES sur Android et iOS | Microsoft Docs
ms.custom: ''
ms.date: 05/16/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 76a67886-df57-4a81-accb-2e3c2eaf607b
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: aa8ffe308f8a1181ed18af52ba7537c46007de94
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317651"
---
# <a name="build-an-opengl-es-application-on-android-and-ios"></a>Générer une application OpenGL ES sur Android et iOS

Vous pouvez créer des solutions et des projets Visual Studio pour les applications iOS et Android qui partagent du code commun. Cet article vous guide tout au long d’un modèle de solution qui crée une application iOS simple et une application Android Native Activity. Les applications ont en commun une partie de code C++ qui utilise OpenGL ES pour afficher le même cube pivotant animé sur chaque plateforme. OpenGL ES (OpenGL for Embedded Systems ou GLES) est une API graphique 2D et 3D qui est prise en charge par de nombreux appareils mobiles.

## <a name="requirements"></a>Spécifications

Avant de pouvoir créer une application OpenGL ES pour iOS et Android, assurez-vous que votre système répond à toutes les exigences. Si cela n’est pas déjà fait, installez le développement mobile avec charge de travail C++ dans Visual Studio Installer. Pour générer pour iOS, incluez les outils de développement iOS C++ facultatifs. Pour générer pour Android, installez les outils de développement C++ Android et les outils tiers requis : Android NDK, Apache Ant, Émulateur Google Android et Hardware Accelerated Execution Manager Intel. Ensuite, configurez Intel HAXM et Émulateur Android à exécuter sur votre système. Pour obtenir plus d’informations et des instructions détaillées, consultez [Installer Visual C++ pour le développement mobile multiplateforme](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Pour générer et tester l’application iOS, vous devez disposer d’un ordinateur Mac configuré conformément aux instructions d’installation. Pour plus d’informations sur la configuration requise pour développer du code pour iOS, consultez [Installer et configurer des outils de génération en utilisant iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)

## <a name="create-a-new-opengles-application-project"></a>Créer un projet Application OpenGLES

Dans ce didacticiel, vous allez tout d’abord créer un projet Application OpenGLES, puis vous allez générer et exécuter l’application par défaut dans l’Émulateur Visual Studio pour Android. Ensuite, générez l’application pour iOS et exécutez l’application dans l’appareil iOS.

1. Dans Visual Studio, choisissez **Fichier** > **Nouveau** > **Projet**.

1. Dans la boîte de dialogue **Nouveau projet**, sous **Modèles**, choisissez **Visual C++**  > **Interplateforme**, puis choisissez le modèle **Application OpenGLES (Android, iOS)** .

1. Donnez à l’application un nom comme `MyOpenGLESApp`, puis choisissez **OK**.

   ![Nouveau projet d’application OpenGLES](../cross-platform/media/cppmdd_opengles_newproj.PNG "CPPMDD_OpenGLES_NewProj")

   Visual Studio crée la solution et ouvre l’Explorateur de solutions.

   ![MyOpenGLESApp dans l’Explorateur de solutions](../cross-platform/media/cppmdd_opengles_solexpl.PNG "CPPMDD_OpenGLES_SolExpl")

   La nouvelle solution Application OpenGLES comprend trois projets de bibliothèque et deux projets d’application. Le dossier de bibliothèques inclut un projet de code partagé et deux projets spécifiques à la plateforme qui référencent le code partagé :

- `MyOpenGLESApp.Android.NativeActivity` contient les références et le code de type glue qui implémente votre application en tant que Native Activity sur Android. L’implémentation des points d’entrée à partir du code de type glue se trouve dans *main.cpp*, qui comprend le code commun partagé dans `MyOpenGLESApp.Shared`. Les en-têtes précompilés sont dans *pch.h*. Ce projet d’application Native Activity est compilé en fichier de bibliothèque partagée ( *.so*), qui est récupéré par le projet `MyOpenGLESApp.Android.Packaging`.

- `MyOpenGLESApp.iOS.StaticLibrary` Crée un fichier de bibliothèque statique iOS ( *.a*) qui contient le code partagé dans `MyOpenGLESApp.Shared`. Il est lié à l’application créée par le projet `MyOpenGLESApp.iOS.Application`.

- `MyOpenGLESApp.Shared` contient le code partagé qui fonctionne sur plusieurs plateformes. Il utilise des macros de préprocesseur pour compiler de façon conditionnelle le code spécifique à la plateforme. Le code partagé est récupéré par la référence de projet à la fois dans `MyOpenGLESApp.Android.NativeActivity` et dans `MyOpenGLESApp.iOS.StaticLibrary`.

La solution comporte deux projets visant à générer des applications pour les plateformes Android et iOS :

- `MyOpenGLESApp.Android.Packaging` crée le fichier *.apk* pour le déploiement sur un émulateur ou un appareil Android. Ce fichier contient les ressources et le fichier AndroidManifest.xml dans lequel vous avez défini les propriétés de manifeste. Il contient aussi le fichier *build.xml* qui contrôle le processus de génération Ant. Il est configuré comme projet de démarrage par défaut et peut donc être déployé et exécuté directement à partir de Visual Studio.

- **MyOpenGLESApp.iOS.Application** contient les ressources et le code de type glue Objective-C nécessaires pour créer une application iOS liée au code de la bibliothèque statique C++ dans `MyOpenGLESApp.iOS.StaticLibrary`. Ce projet crée un package de build qui est transféré vers votre Mac par Visual Studio et l’agent distant. Quand vous générez ce projet, Visual Studio envoie les fichiers et les commandes pour générer et déployer votre application sur le Mac.

## <a name="build-and-run-the-android-app"></a>Générer et exécuter l’application Android

La solution créée par le modèle définit l’application Android en tant que projet par défaut.  Vous pouvez générer et exécuter cette application pour vérifier votre installation et votre configuration. Pour un test initial, exécutez l’application sur l’un des profils d’appareils installés par l’émulateur pour Android. Si vous préférez tester votre application sur une autre cible, vous pouvez charger l’émulateur cible ou connecter l’appareil à votre ordinateur.

### <a name="to-build-and-run-the-android-native-activity-app"></a>Pour générer et exécuter l’application Android Native Activity

1. Si ce n’est pas déjà fait, choisissez **x86** dans la liste déroulante **Plateformes Solution**.

   ![Définir la plateforme de solution x86](../cross-platform/media/cppmdd_opengles_solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")

   Utilisez x86 pour cibler l’émulateur. Pour cibler un appareil, choisissez la plateforme solution basée sur le processeur de l’appareil. Si la liste **Plateformes solution** n’est pas visible, choisissez **Plateformes solution** dans la liste **Ajouter/supprimer des boutons**, puis choisissez votre plateforme.

1. Dans **l’Explorateur de solutions**, ouvrez le menu du projet `MyOpenGLESApp.Android.Packaging`, puis choisissez **Générer**.

   ![Générer un projet de package Android](../cross-platform/media/cppmdd_opengles_andbuild.png "CPPMDD_OpenGLES_AndBuild")

   La fenêtre Sortie affiche la sortie du processus de génération pour la bibliothèque partagée Android et l’application Android.

   ![Générer la sortie de projets Android](../cross-platform/media/cppmdd_opengles_andoutput.png "CPPMDD_OpenGLES_AndOutput")

1. Sélectionnez l’un des profils d’appareil Android émulé comme cible de déploiement.

   ![Choisir une cible de déploiement](../cross-platform/media/cppmdd_opengles_pickemulator.png "CPPMDD_OpenGLES_PickEmulator")

   Si vous avez installé d’autres émulateurs ou si vous avez connecté un appareil Android, vous pouvez les choisir dans la liste déroulante de cible de déploiement. Pour exécuter l’application, la Plateforme Solution intégrée doit correspondre à la plateforme de l’appareil cible.

1. Appuyez sur F5 pour démarrer le débogage, ou sur Maj+F5 pour démarrer sans débogage.

   Visual Studio démarre l’émulateur qui, après quelques secondes, charge et déploie votre code. Voici comment l’application apparaît dans l’émulateur :

   ![Application en cours d’exécution dans l’émulateur Android](../cross-platform/media/cppmdd_opengles_andemulator.png "CPPMDD_OpenGLES_AndEmulator")

   Une fois l’application démarrée, vous pouvez définir des points d’arrêt et utiliser le débogueur pour parcourir le code, examiner les variables locales et observer les valeurs.

1. Appuyez sur **Maj**+**F5** pour arrêter le débogage.

   L’émulateur est un processus distinct qui continue à s’exécuter. Vous pouvez modifier, compiler et déployer votre code plusieurs fois sur le même émulateur. Vous pouvez démarrer votre application directement à partir de la collection d’applications dans laquelle elle apparaît sur l’émulateur.

   Les projets de bibliothèque et d’application Android Native Activity générés placent le code C++ partagé dans une bibliothèque dynamique qui contient du code de type « glue » pour interagir avec la plateforme Android. La majeure partie du code d’application se trouve dans la bibliothèque et le manifeste, les ressources et les instructions de la build se trouvent dans le projet de création de package. Le code partagé est appelé à partir de main.cpp dans le projet NativeActivity. Pour plus d’informations sur la programmation d’une activité Android Native Activity, consultez la page [Concepts](https://developer.android.com/ndk/guides/concepts.html) du NDK Android.

   Visual Studio génère les projets Android Native Activity à l’aide du NDK Android, ce dernier utilisant l’ensemble d’outils de plateforme Clang. Visual Studio mappe les propriétés du projet NativeActivity aux options servant aux opérations de compilation, de liaison et de débogage sur la plateforme cible. Pour plus d’informations, ouvrez la boîte de dialogue **Pages de propriétés** pour le projet MyOpenGLESApp.Android.NativeActivity. Pour plus d’informations sur les commutateurs de ligne de commande, consultez le [manuel de l’utilisateur du compilateur Clang](http://clang.llvm.org/docs/UsersManual.html).

## <a name="build-and-run-the-ios-app-on-an-ios-device"></a>Générer et exécuter l’application iOS sur un appareil iOS

Le projet d’application iOS est créé et modifié dans Visual Studio, mais du fait de restrictions de licences, il doit être créé et déployé sur un Mac. Visual Studio communique avec un agent distant s’exécutant sur le Mac pour transférer les fichiers du projet et exécuter les commandes de génération, de déploiement et de débogage. Installez et configurez votre Mac et Visual Studio pour communiquer avant de générer l’application iOS. Pour obtenir des instructions détaillées, consultez [Installer et configurer des outils de génération en utilisant iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Une fois que l’agent distant est en cours d’exécution sur votre Mac et associé à Visual Studio, vous pouvez générer et exécuter l’application iOS pour vérifier votre installation et votre configuration.

Pour déployer une application iOS sur un appareil iOS, vous devez également configurer la signature automatique sur Xcode sur le Mac. Automatiquement la signature automatique gère la signature des applications et crée un profil d’approvisionnement pour vous connecter à une build de l’application.

### <a name="to-set-up-automatic-signing-on-xcode"></a>Pour configurer la signature automatique sur Xcode

1. Si ce n’est pas déjà fait, installez [Xcode](https://developer.apple.com/xcode/downloads/) version 10.2.1 ou version ultérieure sur votre Mac.

1. Ouvrez l’application Xcode sur votre Mac.

1. Créez un nouveau projet Xcode **d'application avec affichage unique**. Renseignez les champs requis lors de la création du projet. Les valeurs peuvent être arbitraires, étant donné que le projet est uniquement utilisé pour créer un profil d’approvisionnement qui sera utilisé ultérieurement pour vous connecter à une build de l’application.

1. Ajoutez votre ID Apple qui est inscrit dans un compte de [programme de développement Apple](https://developer.apple.com/programs/) sur Xcode. Votre ID Apple est utilisé comme une identité de signature pour signer des applications. Pour ajouter votre identité de signature dans Xcode, ouvrez le menu **Xcode** et choisissez **Préférences**. Sélectionnez **Comptes** et cliquez sur le bouton Ajouter (+) pour ajouter votre ID Apple. Consultez [Ajouter votre compte ID Apple](https://help.apple.com/xcode/mac/current/#/devaf282080a) pour obtenir des instructions détaillées.

1. À partir des paramètres « Général » du projet Xcode, remplacez la valeur **identificateur du Bundle** par `com.<NameOfVSProject>`, où `<NameOfVSProject>` est le même nom que le projet de solution Visual Studio que vous avez créé. Par exemple, si vous avez créé un projet appelé `MyOpenGLESApp` sur Visual Studio, puis défini **identificateur du Bundle** sur `com.MyOpenGLESApp`.

   ![Identificateur du bundle Xcode](../cross-platform/media/cppmdd-opengles-iosxcodeid.png "CPPMDD_OpenGLES_iOSXcodeId")

1. Pour activer la signature automatique, vérifiez. Gestion automatique des signatures**.

   ![Signature automatique Xcode](../cross-platform/media/cppmdd-opengles-iosxcodesign.png "CPPMDD_OpenGLES_iOSXcodeSign")

1. Sélectionnez le nom d’équipe de l’ID Apple que vous avez ajouté en tant qu’**équipe** de développement.

   ![Équipe Xcode](../cross-platform/media/cppmdd-opengles-iosxcodeteam.png "CPPMDD_OpenGLES_iOSXcodeTeam")

### <a name="to-build-and-run-the-ios-app-on-an-ios-device"></a>Pour générer et exécuter l’application iOS sur un appareil iOS

1. Exécutez l’agent distant sur votre Mac et vérifiez que Visual Studio est associé à l’agent distant. Pour démarrer l’agent distant, ouvrez une fenêtre d’application Terminal et entrez `vcremote`. Pour plus d’informations, consultez [Configurer l’agent distant dans Visual Studio](../cross-platform/install-and-configure-tools-to-build-using-ios.md#ConfigureVS).

   ![Fenêtre Terminal Mac exécutant vcremote](../cross-platform/media/cppmdd_common_vcremote.png "CPPMDD_common_vcremote")

1. Joindre un appareil iOS à votre Mac. Lorsque vous joignez votre appareil à un ordinateur pour la première fois, une alerte vous demande si vous faites confiance à l’ordinateur pour accéder à votre appareil. Permettez à l’appareil de faire confiance à l’ordinateur Mac.

1. Dans Visual Studio, si elle n’est pas déjà sélectionnée, choisissez la plateforme solution à partir de la liste déroulante **Plateformes Solution**, selon le processeur de votre appareil. Dans cet exemple, il s’agit d’un processeur **ARM64**.

   ![Définir la plateforme solution sur ARM64](../cross-platform/media/cppmdd-opengles-pickplatformarm64.png "CPPMDD_OpenGLES_SolutionPlatARM64")

1. Dans l’Explorateur de solutions, ouvrez le menu contextuel du projet MyOpenGLESApp.iOS.Application, puis choisissez **Décharger le projet** pour décharger le projet.

1. Une fois de plus, ouvrez le menu contextuel du projet MyOpenGLESApp.iOS.Application déchargé, puis choisissez **Modifier projet.pbxproj** pour modifier le fichier du projet. Dans le fichier `project.pbxproj`, recherchez l’attribut `buildSettings` et ajoutez `DEVELOPMENT_TEAM` à l’aide de votre ID d’équipe Apple. La capture d’écran ci-dessous montre un exemple de valeur `123456ABC` pour l’ID de l’équipe Apple. Vous pouvez trouver la valeur de votre ID d’équipe Apple à partir de Xcode. Accédez à **Paramètres de la build** et pointez sur le nom de votre équipe de développement pour afficher une info-bulle. L’info-bulle affiche votre ID d’équipe.

   ![Définir l’équipe de développement](../cross-platform/media/cppmdd-opengles-iosdevelopmentteam.png "CPPMDD_OpenGLES_iOSDevelopmentTeam")

1. Fermez le fichier `project.pbxproj`, puis ouvrez le menu contextuel du projet MyOpenGLESApp.iOS.Application déchargé et choisissez **Recharger le projet** pour recharger le projet.

1. Générez à présent le projet MyOpenGLESApp.iOS.Application en ouvrant le menu contextuel du projet et en choisissant **Build**.

   ![Générer un projet d’application iOS](../cross-platform/media/cppmdd_opengles_iosbuild.png "CPPMDD_OpenGLES_iOSBuild")

   La fenêtre Sortie affiche la sortie du processus de génération pour la bibliothèque statique iOS et l’application iOS. Sur le Mac, la fenêtre Terminal exécutant l’agent distant affiche la commande et l’activité de transfert de fichier.

   Sur votre ordinateur Mac, vous pouvez être invité à autoriser codesign à accéder à votre trousseau. Cliquez sur **Autoriser** pour continuer.

1. Choisissez votre appareil iOS dans la barre d’outils pour exécuter l’application sur votre périphérique joint à votre Mac. Si l’application ne démarre pas, vérifiez que l’appareil autorise votre application déployée à s’exécuter sur l’appareil. Cette autorisation peut être définie en accédant à **Paramètres** > **Général** > **Gestion des périphériques** sur l’appareil. Sélectionnez votre compte d’application développeur, faites confiance à votre compte et vérifiez l’application. Essayez à nouveau d’exécuter l’application à partir de Visual Studio.

   ![Application iOS sur un appareil iOS](../cross-platform/media/cppmdd-opengles-iosdevice.png "CPPMDD_OpenGLES_iOSDevice")
   
   Une fois l’application démarrée, vous pouvez définir des points d’arrêt et utiliser le débogueur Visual Studio pour examiner les variables locales, consulter la pile des appels et observer les valeurs.

   ![Débogueur au point d’arrêt dans une application iOS](../cross-platform/media/cppmdd_opengles_iosdebug.png "CPPMDD_OpenGLES_iOSDebug")

1. Appuyez sur **Maj**+**F5** pour arrêter le débogage.

   Les projets de bibliothèque et d’application iOS générés placent le code C++ dans une bibliothèque statique qui implémente uniquement le code partagé. La majeure partie du code d’application se trouve dans le projet `Application`. Les appels au code de bibliothèque partagée dans ce modèle de projet sont effectués dans le fichier *GameViewController.m*. Pour générer votre application iOS, Visual Studio utilise l’ensemble d’outils de plateforme Xcode, celui-ci nécessitant une communication avec un client distant qui s’exécute sur un Mac.

   Visual Studio transfère les fichiers de projet et envoie les commandes au client distant pour générer l’application à l’aide de la plateforme Xcode. Le client distant renvoie les informations d’état de build à Visual Studio. Une fois l’application générée, vous pouvez utiliser Visual Studio pour envoyer des commandes en vue d’exécuter et de déboguer l’application. Le débogueur dans Visual Studio contrôle l’application en cours d’exécution dans votre appareil iOS joint à votre Mac. Visual Studio mappe les propriétés du projet StaticLibrary aux options servant aux opérations de compilation, de liaison et de débogage sur la plateforme iOS cible. Pour obtenir les détails de l’option de ligne de commande du compilateur, ouvrez la boîte de dialogue **Pages de propriétés** du projet MyOpenGLESApp.iOS.StaticLibrary.

## <a name="customize-your-apps"></a>Personnaliser vos applications

Vous pouvez modifier le code C++ partagé pour ajouter ou modifier des fonctionnalités communes. Vous devez modifier les appels au code partagé dans les projets `MyOpenGLESApp.Android.NativeActivity` et `MyOpenGLESApp.iOS.Application` pour établir une correspondance. Vous pouvez utiliser des macros de préprocesseur pour spécifier des sections spécifiques à la plateforme dans votre code commun. La macro de préprocesseur `__ANDROID__` est prédéfinie quand vous générez pour Android. La macro de préprocesseur `__APPLE__` est prédéfinie quand vous générez pour iOS.

Pour bénéficier de la fonctionnalité IntelliSense pour une plateforme de projet spécifique, choisissez le projet dans la liste déroulante du sélecteur de contexte dans la barre Navigation en haut de la fenêtre de l’éditeur.

![Liste déroulante du sélecteur de contexte de projet dans l'éditeur](../cross-platform/media/cppmdd_opengles_contextswitcher.png)

Les problèmes IntelliSense dans le code utilisé par le projet actuel sont signalés par un trait ondulé rouge. Les problèmes dans d’autres projets sont signalés par un trait ondulé violet. Visual Studio ne prend en charge ni la colorisation de code ni IntelliSense pour les fichiers Java ou Objective-C. Toutefois, vous pouvez modifier les fichiers sources et les ressources pour définir le nom de votre application, son icône et d’autres détails d’implémentation.
