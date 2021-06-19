---
title: 'Didacticiel : créer des applications UWP avec Visual Studio & C #'
description: Créer une application UWP dans Visual Studio avec XAML et C#
titleSuffix: ''
ms.custom: vs-acquisition, get-started, SEO-VS-2020
ms.date: 09/20/2019
ms.technology: vs-ide-general
ms.topic: tutorial
ms.devlang: CSharp
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 2e89c58e3c0dca2b5d009a592d3f242646339f8f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390292"
---
# <a name="tutorial-create-your-first-universal-windows-platform-application-in-visual-studio-with-xaml-and-c35"></a>Didacticiel : créer votre première plateforme Windows universelle application dans Visual Studio avec XAML et C&#35;

Dans cette présentation de l’environnement de développement intégré (IDE) Visual Studio, vous allez créer une application « Hello World » qui s’exécute sur n’importe quel appareil Windows 10. Pour ce faire, vous allez utiliser un modèle de projet de plateforme Windows universelle (UWP), le langage XAML (Extensible Application Markup Language) et le langage de programmation C#.

::: moniker range="vs-2017"
Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.
::: moniker-end
::: moniker range="vs-2019"
Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.
::: moniker-end

## <a name="create-a-project"></a>Création d’un projet

Créez tout d’abord un projet de plateforme Windows universelle. Le type de projet inclut tous les fichiers de modèle dont vous avez besoin au départ.

::: moniker range="vs-2017"
1. Ouvrez Visual Studio.

1. Dans la barre de menus supérieure, choisissez **fichier** > **nouveau** > **projet**.

1. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, développez **Visual C#**, puis choisissez **Windows universel**. Dans le volet central, choisissez **Application vide (Windows universel)**. Ensuite, nommez le projet *HelloWorld* et choisissez **OK**.

   > [!NOTE]
   > Assurez-vous que l’emplacement du projet source se trouve sur un nouveau lecteur formaté en **NTFS** , tel que votre lecteur de système d’exploitation. Dans le cas contraire, vous risquez de rencontrer des problèmes pour générer et exécuter votre projet. 

   ![Modèle de projet Windows universel dans la boîte de dialogue Nouveau projet dans l’IDE Visual Studio](media/new-project-csharp-uwp-helloworld.png)

   > [!NOTE]
   > Si vous ne voyez pas le modèle de projet **Application vide (Windows universel)**, cliquez sur le lien **Ouvrir le programme d’installation de Visual Studio** dans le volet gauche de la boîte de dialogue **Nouveau projet**.<br><br>![Cliquer sur le lien Ouvrir le programme d’installation de Visual Studio dans la boîte de dialogue Nouveau projet](../../ide/media/vb-open-visual-studio-installer-hello-world.png)<br><br>Visual Studio Installer est lancé. Choisissez la charge de travail **Développement pour la plateforme Windows universelle**, puis **Modifier**.<br><br>![Charge de travail Développement pour la plateforme Windows universelle dans le programme d’installation de Visual Studio](media/uwp-dev-workload.png)

1. Acceptez les paramètres par défaut pour **Version cible** et **Version minimale** dans la boîte de dialogue **Nouveau projet de plateforme Windows universelle**.

   ![Accepter les paramètres par défaut pour Version cible et Version minimale dans la boîte de dialogue Nouveau projet de plateforme Windows universelle](media/new-uwp-project-target-minver-dialog.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. Ouvrez Visual Studio puis, dans la fenêtre de démarrage, choisissez **Créer un projet**.

1. Sur l’écran **Créer un projet**, entrez *Windows universel* dans la zone de recherche, choisissez le modèle C# pour **Application vide (Windows universel)**, puis choisissez **Suivant**.

   ![Capture d’écran de l’écran Créer un projet](media/vs-2019/uwp-create-new-project.png)

   > [!NOTE]
   > Si vous ne voyez pas le modèle de projet **Application vide (Windows universel)**, cliquez sur le lient **Installer plus d’outils et de fonctionnalités**.<br><br>![Cliquer sur le lien Installer plus d’outils et de fonctionnalités](media/vs-2019/uwp-not-finding.png)<br><br>Visual Studio Installer est lancé. Choisissez la charge de travail **Développement pour la plateforme Windows universelle**, puis **Modifier**.<br><br>![Charge de travail Développement pour la plateforme Windows universelle dans le programme d’installation de Visual Studio](media/uwp-dev-workload.png)

1. Donnez un nom à votre projet, _HelloWorld_, puis choisissez **créer**.

   ![Écran de configuration de votre projet](media/vs-2019/uwp-configure-your-project.png)

1. Acceptez les paramètres par défaut pour **Version cible** et **Version minimale** dans la boîte de dialogue **Nouveau projet de plateforme Windows universelle**.

   ![Accepter la version cible par défaut et les paramètres de version minimale dans la boîte de dialogue Nouveau projet de plateforme Windows universelle](media/vs-2019/new-uwp-project-target-minver-dialog.png)
::: moniker-end

   > [!NOTE]
   > S’il s’agit de la première fois que vous avez utilisé Visual Studio pour créer une application UWP, une boîte de dialogue **Paramètres** peut s’afficher. Choisissez **Mode développeur**, puis **Oui**.<br><br>
   > ![Activer le mode développeur dans la boîte de dialogue Paramètres du projet UWP](media/enable-developer-mode.png)<br><br>Visual Studio installe un autre package en mode développeur pour vous. Une fois l’installation du package terminée, fermez la boîte de dialogue **Paramètres**.

## <a name="create-the-application"></a>Création de l'application

Il est temps de commencer à développer. Vous allez ajouter un contrôle bouton, ajouter une action au bouton, puis démarrer l’application « Hello World » pour voir à quoi elle ressemble.

### <a name="add-a-button-to-the-design-canvas"></a>Ajouter un bouton à la zone de conception

1. Dans **l’Explorateur de solutions**, double-cliquez sur *MainPage.xaml* pour ouvrir un mode fractionné.

   ::: moniker range="vs-2017"
   ![Ouvrir MainPage.xaml à partir de l’Explorateur de solutions ](media/uwp-solution-explorer-MainPage-xaml.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Ouvrir MainPage.xaml à partir de l’Explorateur de solutions](media/vs-2019/uwp-solution-explorer-mainpage-xaml.png)
   ::: moniker-end

   Il existe deux volets : **le concepteur XAML**, qui comprend une zone de conception et **l’éditeur XAML**, où vous pouvez ajouter ou modifier le code.

   ![Volet du concepteur XAML dans l’éditeur XAML](media/uwp-xaml-editor.png)

1. Choisissez **Boîte à outils** pour ouvrir la fenêtre volante Boîte à outils.

   ![Cliquer sur Boîte à outils pour ouvrir la fenêtre volante Boîte à outils](media/uwp-toolbox.png)

   (Si vous ne voyez pas l’option **boîte à outils** , vous pouvez l’ouvrir à partir de la barre de menus. Pour ce faire, choisissez **Afficher** la  >  **barre d’outils**. Ou appuyez sur **CTRL** + **ALT** + **X**.)

1. Cliquez sur l’icône **épingler** pour ancrer la fenêtre boîte à outils.

   ![Cliquer sur l’icône Épingler pour ancrer la fenêtre Boîte à outils](media/uwp-toolbox-autohide.png)

1. Cliquez sur le contrôle **Button**, puis faites-le glisser dans la zone de conception.

   ![Cliquer sur le contrôle Button, puis le faire glisser dans la zone de conception](media/uwp-toolbox-add-button-control.png)

   Si vous examinez le code dans l' **éditeur XAML**, vous verrez que le bouton y a également été ajouté :

   ![Afficher le bouton dans l’éditeur XAML](media/uwp-xaml-control-code-window.png)

### <a name="add-a-label-to-the-button"></a>Ajouter une étiquette au bouton

1. Dans l' **éditeur XAML**, remplacez la valeur de contenu du bouton « Button » par « Hello World ! ».

   ![Remplacer la valeur de Button Content par Hello World](media/uwp-change-button-text-in-xaml-code-window.png)

1. Notez que le bouton dans le **Concepteur XAML** change également.

   ![Le bouton devient Hello World dans la zone de conception](media/uwp-button-text-change-in-design-canvas.png)

### <a name="add-an-event-handler"></a>Ajouter un gestionnaire d’événements

Un « gestionnaire d’événements » semble compliqué, mais il s’agit simplement d’un autre nom pour le code qui est appelé quand un événement se produit. Dans ce cas, il ajoute une action au bouton « Hello World! » .

1. Double-cliquez sur le contrôle bouton dans la zone de conception.

1. Modifiez le code du gestionnaire d’événements dans *MainPage.xaml.cs*, la page code-behind.

   C’est ici que les choses deviennent intéressantes. Le gestionnaire d’événements par défaut se présente ceci :

   ![Gestionnaire d’événements Button_Click par défaut ](media/uwp-button-click-code.png)

   Modifions-le de sorte qu’il se présente comme ceci :

   ![Nouveau gestionnaire d’événements Button_Click asynchrone ](media/uwp-add-hello-world-async-code.png)

   Voici le code à copier et coller :

   ```C#
   private async void Button_Click(object sender, RoutedEventArgs e)
         {
             MediaElement mediaElement = new MediaElement();
             var synth = new Windows.Media.SpeechSynthesis.SpeechSynthesizer();
             Windows.Media.SpeechSynthesis.SpeechSynthesisStream stream = await synth.SynthesizeTextToStreamAsync("Hello, World!");
             mediaElement.SetSource(stream, stream.ContentType);
             mediaElement.Play();
         }
   ```

#### <a name="what-did-we-just-do"></a>Que venons-nous de faire ?

Le code utilise des API Windows pour créer un objet de synthèse vocale, puis lui donne du texte à dire. (Pour plus d’informations sur l’utilisation de `SpeechSynthesis`, consultez <xref:System.Speech.Synthesis>.)

## <a name="run-the-application"></a>Exécution de l'application

::: moniker range="vs-2017"
Il est temps de générer, déployer et lancer l’application UWP « Hello World » pour voir à quoi elle ressemble. Voici comment procéder.

1. Utilisez le bouton Lecture (il contient le texte **Ordinateur local**) pour démarrer l’application sur l’ordinateur local.

   ![Cliquer sur Ordinateur local pour démarrer et déboguer votre application UWP](media/uwp-start-or-debug.png)

   (Vous pouvez également choisir **Déboguer** > **Démarrez le débogage** à partir de la barre de menus ou appuyez sur F5 pour démarrer votre application.)

1. Examinez votre application, qui apparaît vite après la disparition d’un écran de démarrage. L’application doit ressembler à ceci :

   ![Application UWP « Hello World »](media/uwp-hello-world-app.png)

1. Cliquez sur le bouton **Hello World**.

   Votre appareil Windows 10 dira littéralement « Hello, World ! »

1. Pour fermer l’application, cliquez sur le bouton **Arrêter le débogage** dans la barre d’outils. (Vous pouvez également choisir **Déboguer**  >  **Arrêtez le débogage** à partir de la barre de menus, ou appuyez sur Maj + F5.)

::: moniker-end
::: moniker range=">=vs-2019"
Il est temps de générer, déployer et lancer l’application UWP « Hello World » pour voir à quoi elle ressemble. Voici comment procéder.

1. Utilisez le bouton Lecture (il contient le texte **Ordinateur local**) pour démarrer l’application sur l’ordinateur local.

   ![Cliquer sur Ordinateur local pour démarrer et déboguer votre application UWP](media/uwp-start-or-debug.png)

   (Vous pouvez également choisir **Déboguer** > **Démarrez le débogage** à partir de la barre de menus ou appuyez sur F5 pour démarrer votre application.)

1. Examinez votre application, qui apparaît vite après la disparition d’un écran de démarrage. L’application doit ressembler à ceci :

   ![Application « Hello World » UWP](media/vs-2019/uwp-hello-world-app.png)

1. Cliquez sur le bouton **Hello World**.

   Votre appareil Windows 10 dira littéralement « Hello, World ! »

1. Pour fermer l’application, cliquez sur le bouton **Arrêter le débogage** dans la barre d’outils. (Vous pouvez également choisir **Déboguer**  >  **Arrêtez le débogage** à partir de la barre de menus, ou appuyez sur Maj + F5.)

::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

Félicitations ! Vous avez terminé ce didacticiel. Nous espérons que vous avez appris quelques principes fondamentaux sur UWP et l’IDE Visual Studio. Pour en savoir plus, passez au tutoriel suivant :

> [!div class="nextstepaction"]
> [Créer une interface utilisateur](/windows/uwp/design/basics/xaml-basics-ui)

## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble de la plateforme Windows universelle](/windows/uwp/get-started/universal-application-platform-guide)
- [Obtenir des exemples d’applications UWP](/windows/uwp/get-started/get-uwp-app-samples)
