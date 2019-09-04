---
title: Application Hello World avec WPF en C#
description: Créez une application de bureau Windows .NET simple en C# avec Visual Studio à l’aide du framework d’interface utilisateur WPF (Windows Presentation Foundation).
ms.custom: seodec18, get-started
ms.date: 08/09/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d146416190924c8f1835ef17bc0fb622fcc53e03
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70180219"
---
# <a name="tutorial-create-a-simple-application-with-c"></a>Tutoriel : Créer une application simple en C\#

Avec ce didacticiel, vous allez vous familiariser avec la plupart des outils, boîtes de dialogue et concepteurs que vous pouvez utiliser lorsque vous développez des applications avec Visual Studio. Vous allez créer une application « Hello, World », concevoir l’interface utilisateur, ajouter du code et déboguer des erreurs, tout en découvrant l’utilisation de l’environnement de développement intégré ([IDE](visual-studio-ide.md)).

::: moniker range="vs-2017"
Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.
::: moniker-end
::: moniker range=">=vs-2019"
Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.
::: moniker-end

## <a name="configure-the-ide"></a>Configurer l'IDE

::: moniker range="vs-2017"

Quand vous ouvrez Visual Studio pour la première fois, vous êtes invité à vous connecter. Cette étape est facultative pour ce didacticiel. Ensuite, vous pouvez voir s’afficher une boîte de dialogue qui vous invite à choisir vos paramètres de développement et le thème de couleur. Conservez les valeurs par défaut et choisissez **Démarrer Visual Studio**.

![Boîte de dialogue Choisir les paramètres](../media/exploreide-settings.png)

Après le démarrage de Visual Studio, vous voyez les fenêtres Outil, les menus, les barres d’outils et l’espace de la fenêtre principale. Les fenêtres Outil sont ancrées sur les côtés gauche et droit de la fenêtre d'application. **Lancement rapide**, la barre de menus et la barre d'outils standard sont situés en haut. La **page de démarrage**est située au centre de la fenêtre d'application. Lorsque vous chargez une solution ou un projet, les éditeurs et les concepteurs apparaissent dans l'espace où se trouve la **Page de démarrage** . Quand vous développez une application, vous passez la majeure partie de votre temps dans cette zone centrale.

![IDE Visual Studio 2017 avec Paramètres généraux appliqués](../media/exploreide-idewithgeneralsettings.png "Capture d’écran de l’IDE Visual Studio 2017 avec les Paramètres généraux appliqués")

::: moniker-end

::: moniker range=">=vs-2019"

Quand vous lancez Visual Studio, la fenêtre de démarrage s’ouvre en premier. Sélectionnez **Continuer sans code** pour ouvrir l’environnement de développement. Vous allez voir les fenêtres Outils, les menus et barres d’outils ainsi que l’espace de la fenêtre principale. Les fenêtres Outils sont ancrées sur les côtés gauche et droit de la fenêtre d’application. Une zone de recherche, la barre de menus et la barre d’outils standard sont situées en haut. Quand vous chargez une solution ou un projet, les éditeurs et les concepteurs apparaissent dans l’espace central de la fenêtre d’application. Quand vous développez une application, vous passez la majeure partie de votre temps dans cette zone centrale.

::: moniker-end

## <a name="create-the-project"></a>Créer le projet

Lorsque vous créez une application dans Visual Studio, vous créez d'abord un projet et une solution. Pour cet exemple, vous allez créer un projet WPF (Windows Presentation Foundation).

::: moniker range="vs-2017"

1. Créer un nouveau projet. Dans la barre de menus, sélectionnez **Fichier** > **Nouveau** > **Projet**.

     ![Dans la barre de menus, choisissez Fichier, Nouveau, Projet](../media/exploreide-filenewproject.png "Capture d’écran de la barre de menus où vous sélectionnez Fichier, Nouveau, Projet")

1. Dans la boîte de dialogue**Nouveau projet**, sélectionnez la catégorie **Installé** > **Visual C#**  > **Bureau Windows**, puis sélectionnez le modèle **Application WPF (.NET Framework)** . Nommez le projet **HelloWPFApp** et sélectionnez **OK**.

     ![Modèle d’application WPF dans la boîte de dialogue Nouveau projet de Visual Studio](media/exploreide-newprojectcsharp.png "Capture d’écran du modèle d’application WPF dans la boîte de dialogue Nouveau projet")

::: moniker-end

::: moniker range="vs-2019"

1. Ouvrez Visual Studio 2019.

1. Dans la fenêtre de démarrage, choisissez **Créer un projet**.

   ![Afficher la fenêtre 'Créer un projet'](../../get-started/media/vs-2019/start-window-create-new-project.png "Capture d’écran de la fenêtre 'Créer un projet'")

1. Sur l’écran **Créer un projet**, recherchez « WPF », choisissez **Application WPF (.NET Framework)** , puis choisissez **Suivant**.

   ![Modèle d’application WPF dans la boîte de dialogue 'Créer un projet'](media/vs-2019/exploreide-newprojectcsharp-vs2019.png "Capture d’écran du modèle d’application WPF dans la boîte de dialogue 'Créer un projet'")

1. Sur l’écran suivant, nommez le projet **HelloWPFApp** et choisissez **Créer**.

   ![Nommez votre projet 'HelloWPFApp'](./media/vs-2019/exploreide-nameproject.png "Capture d’écran de la fenêtre où vous nommez votre projet")

::: moniker-end

Visual Studio crée la solution et le projet HelloWPFApp, et affiche les différents fichiers dans **l’Explorateur de solutions**. Le **Concepteur WPF** affiche une vue Design et une vue XAML pour *MainWindow.xaml* dans une vue fractionnée. Vous pouvez faire glisser le séparateur pour afficher une partie plus ou moins grande de chacune des vues. Vous pouvez choisir d'afficher uniquement le mode visuel ou uniquement le mode XAML.

![Projet et solution WPF dans l’IDE](media/exploreide-wpfproject-cs.png "Capture d’écran du projet et de la solution WPF dans l’IDE")

> [!NOTE]
> Pour plus d’informations sur XAML (Extensible Application Markup Language), voir la page [Vue d’ensemble de XAML pour WPF](/dotnet/framework/wpf/advanced/xaml-overview-wpf).

Après avoir créé le projet, vous pouvez le personnaliser. Pour cela, choisissez **Fenêtre Propriétés** dans le menu **Affichage** ou appuyez sur **F4**. Ensuite, vous pouvez afficher et changer les options des éléments du projet, des contrôles et d’autres éléments d’une application.

   ![Fenêtre Propriétés](../media/exploreide-hellowpfappfiles.png "Capture d’écran de la fenêtre Propriétés avec les noms des applications de fichiers WPF")   

### <a name="change-the-name-of-mainwindowxaml"></a>Changer le nom de MainWindow.xaml

Donnons un nom plus spécifique à MainWindow.

1. Dans **l’Explorateur de solutions**, sélectionnez *MainWindow.xaml*. Vous devez normalement voir la fenêtre **Propriétés**. Si ce n’est pas le cas, choisissez le menu **Affichage**, puis l’élément **Fenêtre Propriétés**. (Ou, appuyez sur **F4**.)

1. Remplacez la propriété **Nom de fichier** par `Greetings.xaml`.

     ![Fenêtre Propriétés avec Nom de fichier en surbrillance](../media/exploreide-filenameinpropertieswindow.png "Capture d’écran de la fenêtre Propriétés avec le nom de fichier mis en surbrillance")

     Dans l’**Explorateur de solutions**, le nom du fichier est maintenant *Greetings.xaml* et le nom du fichier de code imbriqué est maintenant *Greetings.xaml.cs*. Ce fichier de code est imbriqué sous le nœud de fichier *.xaml* pour montrer que les deux fichiers sont étroitement liés.

     ![Fenêtre Propriétés et fenêtre Explorateur de solutions avec nom de fichier Greetings](../media/exploreide-greetingsfilename.png "Capture d’écran de la fenêtre Propriétés et de la fenêtre Explorateur de solutions avec le nom de fichier Greetings")     

## <a name="design-the-user-interface-ui"></a>Créer l'interface utilisateur

Nous allons ajouter trois types de contrôles à cette application : un contrôle <xref:System.Windows.Controls.TextBlock>, deux contrôles <xref:System.Windows.Controls.RadioButton> et un contrôle <xref:System.Windows.Controls.Button>.

### <a name="add-a-textblock-control"></a>Pour ajouter un contrôle TextBlock

1. Entrez **Ctrl**+**Q** pour activer la zone de recherche et tapez **Boîte à outils**. Choisissez **Affichage > Boîte à outils** dans la liste des résultats.

1. Dans la fenêtre **Boîte à outils**, développez le nœud **Contrôles WPF communs** pour afficher le contrôle TextBlock.

     ![Boîte à outils avec le contrôle TextBlock en surbrillance](../media/exploreide-textblocktoolbox.png "Capture d’écran de la fenêtre Boîte à outils avec le contrôle TextBlock mis en surbrillance")

1. Ajoutez un contrôle TextBlock à l’aire de conception en choisissant l’élément **TextBlock** et en le faisant glisser vers la fenêtre de l’aire de conception. Centrez le contrôle vers le haut de la fenêtre.

    Votre fenêtre doit ressembler à l'illustration suivante :

    ![Contrôle TextBlock sur le formulaire Greetings](../media/exploreide-greetingswithtextblockonly.png "Capture d’écran du contrôle TextBlock sur le formulaire Greetings")

   Le balisage XAML devrait ressembler à l’exemple suivant :

    ```xaml
    <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
    </Grid>
    ```

### <a name="customize-the-text-in-the-text-block"></a>Personnaliser le texte du bloc de texte

1. Dans la vue XAML, localisez la balise de **TextBlock,** puis modifiez l'attribut **Text** de `TextBox` à `Select a message option and then choose the Display button.`

   Le balisage XAML devrait ressembler à l’exemple suivant :

   ```xaml
   <Grid>
       <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
   </Grid>
   ```

1. Recentrez l’élément TextBlock si nécessaire, puis enregistrez vos modifications en appuyant sur **Ctrl+S** ou en utilisant l’élément de menu **Fichier**.

Vous ajouterez ensuite deux contrôles [RadioButton](/dotnet/framework/wpf/controls/radiobutton) au formulaire.

### <a name="add-radio-buttons"></a>Ajouter des cases d’option

1. Dans la fenêtre **Boîte à outils**, recherchez le contrôle **RadioButton**.

     ![Fenêtre Boîte à outils avec le contrôle RadioButton sélectionné](../media/exploreide-radiobuttontoolbox.png "Capture d’écran de la fenêtre Boîte à outils avec le contrôle RadioButton sélectionné")

1. Ajoutez deux contrôles RadioButton à l’aire de conception en choisissant l’élément **RadioButton** et en le faisant glisser vers la fenêtre de l’aire de conception. Déplacez les boutons (en les sélectionnant et en utilisant les flèches) pour les placer côte à côte sous le contrôle TextBlock.

   Votre fenêtre doit se présenter comme suit :

   ![Formulaire Greetings avec TextBlock et deux cases d’option](../media/exploreide-greetingswithradiobuttons.png "Capture d’écran du formulaire Greetings avec TextBlock et deux cases d’option")

1. Dans la fenêtre **Propriétés** du contrôle RadioButton de gauche, affectez à la propriété **Nom** (propriété en haut de la fenêtre **Propriétés**) la valeur `HelloButton`.

    ![Fenêtre des propriétés RadioButton](../media/exploreide-buttonproperties.png "Capture d’écran de la fenêtre des propriétés de RadioButton")

1. Dans la fenêtre **Propriétés** du contrôle RadioButton de droite, remplacez la valeur de la propriété **Name** par `GoodbyeButton`, puis enregistrez les modifications.

Vous allez ensuite afficher du texte pour chaque contrôle RadioButton. La procédure suivante met à jour la propriété **Contenu** d'un contrôle RadioButton.

### <a name="add-display-text-for-each-radio-button"></a>Ajouter un texte à afficher pour chaque case d’option

1. Sur l’aire de conception, ouvrez le menu contextuel du contrôle HelloButton en cliquant avec le bouton droit sur HelloButton, choisissez **Modifier le texte**, puis entrez `Hello`.

1. Ouvrez le menu contextuel du contrôle GoodbyeButton en cliquant avec le bouton droit sur GoodbyeButton, choisissez **Modifier le texte**, puis entrez `Goodbye`.

   Le balisage XAML doit maintenant ressembler à l’exemple suivant :

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Définir une case d’option activée par défaut

Dans cette étape, nous allons faire en sorte que la case HelloButton soit cochée par défaut. Ainsi, il y aura toujours une des deux cases d’option sélectionnée.

1. Dans l’affichage XAML, recherchez la balise de HelloButton.

1. Ajoutez un attribut **IsChecked** et affectez-lui la valeur **True**. Plus précisément, ajoutez `IsChecked="True"`.

   Le balisage XAML doit maintenant ressembler à l’exemple suivant :

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

Le dernier élément de l’interface utilisateur que vous ajouterez est un contrôle [Button](/dotnet/framework/wpf/controls/button).

### <a name="add-the-button-control"></a>Ajouter le contrôle bouton

1. Dans la fenêtre **Boîte à outils**, recherchez le contrôle **Button**, puis ajoutez-le à l’aire de conception sous les contrôles RadioButton en le faisant glisser vers le formulaire en mode Design.

1. Dans l’affichage XAML, changez la valeur de l’élément **Content** du contrôle Button de `Content="Button"` en `Content="Display"`, puis enregistrez les modifications.

     Votre fenêtre doit ressembler à l'illustration suivante.

     ![Formulaire Greetings avec étiquettes de contrôle](media/exploreide-greetingswithcontrollabels-cs.png "Capture d’écran du formulaire Greetings avec des étiquettes de contrôle")

   Le balisage XAML doit maintenant ressembler à l’exemple suivant :

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
        <Button Content="Display" HorizontalAlignment="Left" Margin="377,270,0,0" VerticalAlignment="Top" Width="75"/>
   </Grid>
   ```

### <a name="add-code-to-the-display-button"></a>Ajouter du code au bouton d’affichage

Quand cette application s’exécute, un message s’affiche si un utilisateur choisit une case d’option et choisit ensuite le bouton **Afficher**. Un message s'affiche pour Hello et un autre pour Goodbye. Pour créer ce comportement, vous ajoutez du code à l’événement `Button_Click` dans *Greetings.xaml.cs*.

1. Dans l'aire de conception, double-cliquez sur le bouton **Afficher** .

     *Greetings.xaml.cs* s’ouvre, avec le curseur dans l’événement `Button_Click`.

    ```csharp
    private void Button_Click_1(object sender, RoutedEventArgs e)
    {

    }
    ```

1. Entrez le code suivant :

    ```csharp
    if (HelloButton.IsChecked == true)
    {
         MessageBox.Show("Hello.");
    }
    else if (GoodbyeButton.IsChecked == true)
    {
        MessageBox.Show("Goodbye.");
    }
    ```

1. Enregistrez l'application.

## <a name="debug-and-test-the-application"></a>Déboguer et tester l'application

Vous déboguerez ensuite l’application pour rechercher les erreurs et tester l’affichage correct des deux boîtes de message. Les instructions suivantes expliquent comment générer et lancer le débogueur. Pour plus d’informations, vous pouvez ultérieurement consulter [Générer une application WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) et [Déboguer WPF](../../debugger/debugging-wpf.md).

### <a name="find-and-fix-errors"></a>Rechercher et corriger des erreurs

Dans cette étape, vous recherchez l’erreur que nous avons provoquée précédemment en changeant le nom du fichier *MainWindow.xaml*.

#### <a name="start-debugging-and-find-the-error"></a>Démarrer le débogage et rechercher l’erreur

1. Démarrez le débogueur en appuyant sur **F5** ou en sélectionnant **Déboguer**, puis **Démarrer le débogage**.

   Une fenêtre **Mode arrêt** s’affiche. La fenêtre **Sortie** indique qu’une exception IOException s’est produite : Impossible de trouver la ressource « mainwindow.xaml ».

   ![Message IOException](../media/exploreide-ioexception.png "Capture d’écran du message IOException")

1. Arrêtez le débogueur en choisissant **Déboguer** > **Arrêter le débogage**.

Nous avons renommé *MainWindow.xaml* en *Greetings.xaml* au début de ce didacticiel, mais le code continue de faire référence à *MainWindow.xaml* comme URI de démarrage de l’application. Cela explique pourquoi le projet ne démarre pas.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Spécifier Greetings.xaml comme URI de démarrage

1. Dans l’**Explorateur de solutions**, ouvrez le fichier *App.xaml*.

1. Remplacez `StartupUri="MainWindow.xaml"` par `StartupUri="Greetings.xaml"`, puis enregistrez les modifications.

Redémarrez le débogueur (appuyez sur **F5**). Vous devez voir la fenêtre **Greetings** de l’application. Maintenant, fermez la fenêtre d’application pour arrêter le débogage.

### <a name="debug-with-breakpoints"></a>Déboguer avec des points d’arrêt

Vous pouvez tester le code pendant le débogage en ajoutant des points d’arrêt. Vous pouvez ajouter des points d’arrêt en choisissant **Déboguer** > **Basculer le point d’arrêt**, en cliquant dans la marge gauche de l’éditeur à côté de la ligne de code où mettre le point d’arrêt, ou en appuyant sur **F9**.

#### <a name="add-breakpoints"></a>Ajouter des points d’arrêt

1. Ouvrez *Greetings.xaml.cs*, puis sélectionnez la ligne suivante : `MessageBox.Show("Hello.")`

1. Ajoutez un point d'arrêt à partir du menu en sélectionnant **Déboguer**, puis **Basculer le point d'arrêt**.

     Un cercle rouge apparaît à côté de la ligne de code dans la bordure gauche de la fenêtre de l’éditeur.

1. Sélectionnez la ligne suivante : `MessageBox.Show("Goodbye.")`.

1. Appuyez sur la touche **F9** pour ajouter un point d’arrêt, puis sur la touche **F5** pour démarrer le débogage.

1. Dans la fenêtre **Greetings** , choisissez la case d'option **Hello** , puis le bouton **Afficher** .

    La ligne `MessageBox.Show("Hello.")` est mise en surbrillance en jaune. Dans la partie inférieure de l’IDE, les fenêtres Automatique, Variables locales et Espion sont ancrées ensemble sur le côté gauche. Les fenêtres Pile des appels, Points d’arrêt, Paramètres d’exception, Commande, Immédiat et Sortie sont ancrées ensemble sur le côté droit.

    ![Point d’arrêt dans le débogueur](media/exploreide-debugbreakpoint.png "Capture d’écran du point d’arrêt dans le débogueur")

1. Dans la barre de menus, choisissez **Déboguer** > **Pas à pas sortant**.

     L’application reprend l’exécution et une boîte de message affiche le mot « Hello ».

1. Choisissez le bouton **OK** dans la boîte de message pour la fermer.

1. Dans la fenêtre **Greetings** , choisissez la case d'option **Goodbye** , puis le bouton **Afficher** .

     La ligne `MessageBox.Show("Goodbye.")` est mise en surbrillance en jaune.

1. Appuyez sur la touche **F5** pour continuer le débogage. Lorsque la boîte de message s'affiche, choisissez le bouton **OK** sur la boîte de message pour la fermer.

1. Fermez la fenêtre d’application pour arrêter le débogage.

1. Dans la barre de menus, choisissez **Débogage** > **Désactiver tous les points d’arrêt**.

### <a name="build-a-release-version-of-the-application"></a>Générer une version Release de l'application

Maintenant que vous avez vérifié que tout fonctionne, vous pouvez préparer une version Release de l’application.

1. Dans le menu principal, sélectionnez **Générer** > **Nettoyer la solution** pour supprimer les fichiers intermédiaires et les fichiers de sortie créés lors des builds précédentes. Cette opération n'est pas nécessaire, mais elle nettoie les sorties des versions Debug.

1. Remplacez la configuration de build **Debug** pour HelloWPFApp par **Release** à l’aide du contrôle de liste déroulante de la barre d’outils (« Debug » est actuellement affiché).

1. Générez la solution en choisissant **Générer** > **Générer la solution**.

Félicitations ! Vous avez terminé ce didacticiel. Le fichier *.exe* que vous avez généré se trouve sous le répertoire de votre solution et de votre projet ( *...\HelloWPFApp\HelloWPFApp\bin\Release*).

## <a name="next-steps"></a>Étapes suivantes

Félicitations ! Vous avez terminé ce didacticiel. Pour plus d’informations, passez aux tutoriels suivants.

> [!div class="nextstepaction"]
> [Continuer avec d’autres tutoriels WPF](/dotnet/framework/wpf/getting-started/wpf-walkthroughs/)

## <a name="see-also"></a>Voir aussi

- [Conseils de productivité](../../ide/productivity-features.md)
