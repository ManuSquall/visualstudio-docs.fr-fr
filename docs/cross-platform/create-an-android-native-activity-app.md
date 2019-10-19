---
title: Créer une application Android Native Activity | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 884014b1-5208-45ec-b0da-ad0070d2c24d
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 2b8fbc8d651536c35ee2dae985876f38336c9061
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72588912"
---
# <a name="create-an-android-native-activity-app"></a>Créer une application Android Native Activity

Lorsque vous installez le **développement mobile multiplateforme avec C++**  une charge de travail, Visual Studio peut être utilisé pour créer des applications Android Native Activity entièrement fonctionnelles. Android Native Development Kit (NDK) est un ensemble d’outils vous permettant d’implémenter la majorité de votre application Android au moyen de code C/C++ pur. Certaines parties de code Java JNI font office de colle pour permettre à votre code C/C++ d’interagir avec Android. Android NDK a introduit la possibilité de créer des applications Native Activity à l’aide de l’API Android de niveau 9. Le code Native Activity est couramment employé pour créer des jeux et des applications à fort contenu graphique qui utilisent Unreal Engine ou OpenGL. Cette rubrique vous guide tout au long de la création d’une application Native Activity simple utilisant OpenGL. D’autres rubriques examinent plus en détail les étapes du cycle de développement, à savoir la modification, la génération, le débogage et le déploiement de code Native Activity.

## <a name="requirements"></a>spécifications

Avant de pouvoir créer une application Android Native Activity, vous devez vous assurer que vous avez répondu à la configuration système requise et que vous avez installé le **développement mobile avec C++**  la charge de travail dans Visual Studio. Pour plus d’informations, consultez [installer le développement mobile multiplateforme avec C++ ](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Assurez-vous que les outils et kits de développement logiciel tiers requis sont inclus dans l’installation, et qu’un émulateur Android est installé.

## <a name="create-a-new-native-activity-project"></a>Créer un projet Native Activity

Dans ce didacticiel, vous allez d’abord créer un projet Android Native Activity, puis générer et exécuter l’application par défaut dans un émulateur Android.

::: moniker range="vs-2017"

1. Dans Visual Studio, choisissez **fichier** > **nouveau** **projet**>.

1. Dans la boîte de dialogue **nouveau projet** , sous **modèles**, **Choisissez C++ Visual** > **multiplateforme**, puis choisissez le modèle **application native-Activity (Android)** .

1. Donnez un nom à l’application, par exemple *MyAndroidApp*, puis choisissez **OK**.

   ![Créer un projet d’activité Native](../cross-platform/media/cppmdd_newproject.PNG "CppMDD_NewProject")

   Visual Studio crée la solution et ouvre l’Explorateur de solutions.

   ![Projet Native Activity dans Explorateur de solutions](../cross-platform/media/cppmdd_rc_na_solutionexp.PNG "CPPMDD_RC_NA_SolutionExp")

::: moniker-end

::: moniker range=">=vs-2019"

1. Dans Visual Studio, choisissez **fichier** > **nouveau** **projet**>.

1. Dans la boîte de dialogue **créer un nouveau projet** , sélectionnez le modèle **application d’activité native (Android)** , puis choisissez **suivant**.

1. Dans la boîte de dialogue **configurer votre nouveau projet** , entrez un nom tel que *MyAndroidApp* dans **nom du projet**, puis choisissez **créer**.

   Visual Studio crée la solution et ouvre l’Explorateur de solutions.

::: moniker-end

La nouvelle solution Application Android Native Activity comprend deux projets :

- `MyAndroidApp.NativeActivity` contient les références et le code de type glue pour que votre application s’exécute comme Native Activity sur Android. L’implémentation des points d’entrée à partir du code de type glue se trouve dans *main.cpp*. Les en-têtes précompilés sont dans *pch.h*. Ce projet d’application Native Activity est compilé en fichier de bibliothèque partagée *.so*, qui est utilisé par le projet de création de package.

- `MyAndroidApp.Packaging` crée le fichier *.apk* pour le déploiement sur un émulateur ou un appareil Android. Il contient les ressources et le fichier *AndroidManifest.xml* où vous avez défini les propriétés de manifeste. Il contient aussi le fichier *build.xml* qui contrôle le processus de génération Ant. Il est configuré comme projet de démarrage par défaut et peut donc être déployé et exécuté directement à partir de Visual Studio.

## <a name="build-and-run-the-default-android-native-activity-app"></a>Générer et exécuter l’application Android Native Activity par défaut

Générez et exécutez l’application générée par le modèle pour vérifier votre installation et votre configuration. Pour ce test initial, exécutez l’application sur l’un des profils d’appareil installés par l’émulateur Android. Si vous préférez tester votre application sur une autre cible, vous pouvez charger l’émulateur cible ou connecter l’appareil à votre ordinateur.

## <a name="to-build-and-run-the-default-native-activity-app"></a>Pour générer et exécuter l’application Native Activity par défaut

1. Si ce n’est pas déjà fait, choisissez **x86** dans la liste déroulante **Plateformes Solution** .

     ![Plateformes de solution, sélection x86](../cross-platform/media/cppmdd_rc_na_solution_x86.png "CPPMDD_RC_NA_Solution_x86")

     Si la liste **Plateformes Solution** n’est pas visible, choisissez **Plateformes Solution** dans la liste **Ajouter/supprimer des boutons**, puis choisissez votre plateforme.

1. Dans la barre de menus, choisissez **Générer**  >  **Générer la solution**.

     La fenêtre Sortie affiche la sortie du processus de génération pour les deux projets de la solution.

1. Choisissez l’un des profils d’émulateur Android comme cible de déploiement.

     Si vous avez installé d’autres émulateurs ou si vous avez connecté un appareil Android, vous pouvez les choisir dans la liste déroulante de cible de déploiement.

1. Appuyez sur **F5** pour démarrer le débogage, ou sur **MAJ** +**F5** pour démarrer sans débogage.

   Voici à quoi ressemble l’application par défaut dans un émulateur Android.

   ![L’émulateur exécutant votre application](../cross-platform/media/cppmdd_emulator_running_app.PNG "CppMDD_Emulator_Running_App")

   Visual Studio démarre l’émulateur qui, après quelques secondes, charge et déploie votre code. Une fois l’application démarrée, vous pouvez définir des points d’arrêt et utiliser le débogueur pour parcourir le code, examiner les variables locales et observer les valeurs.

1. Appuyez sur **Maj**+**F5** pour arrêter le débogage.

   L’émulateur est un processus distinct qui continue à s’exécuter. Vous pouvez modifier, compiler et déployer votre code plusieurs fois sur le même émulateur.
