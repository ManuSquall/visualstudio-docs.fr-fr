---
title: Application Hello World avec WPF dans Visual Basic
description: Créez une application de bureau Windows .NET simple en Visual Basic avec Visual Studio à l’aide du framework d’interface utilisateur WPF (Windows Presentation Foundation).
ms.custom: vs-acquisition, seodec18, get-started
ms.date: 04/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
dev_langs:
- VB
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: e757dc25fe094b1ffa745cd43ad251abbc9448a7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390123"
---
# <a name="tutorial-create-a-simple-application-with-visual-basic"></a>Didacticiel : créer une application simple avec Visual Basic

Avec ce didacticiel, vous allez vous familiariser avec la plupart des outils, boîtes de dialogue et concepteurs que vous pouvez utiliser lorsque vous développez des applications avec Visual Studio. Vous allez créer une application « Hello, World », concevoir l’interface utilisateur, ajouter du code et déboguer des erreurs, tout en découvrant l’utilisation de l’environnement de développement intégré ([IDE](visual-studio-ide.md)).

::: moniker range="vs-2017"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2019"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2022"

Si vous n’avez pas encore installé Visual Studio 2022 Preview, accédez à la page [téléchargements Visual studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) pour l’installer gratuitement.

::: moniker-end

## <a name="configure-the-ide"></a>Configurer l'IDE

::: moniker range="vs-2017"

Quand vous ouvrez Visual Studio pour la première fois, vous êtes invité à vous connecter. Cette étape est facultative pour ce didacticiel. Ensuite, vous pouvez voir s’afficher une boîte de dialogue qui vous invite à choisir vos paramètres de développement et le thème de couleur. Conservez les valeurs par défaut et choisissez **Démarrer Visual Studio**.

![Boîte de dialogue Choisir les paramètres](../media/exploreide-settings.png)

Après le démarrage de Visual Studio, vous voyez les fenêtres Outil, les menus, les barres d’outils et l’espace de la fenêtre principale. Les fenêtres Outil sont ancrées sur les côtés gauche et droit de la fenêtre d'application. **Lancement rapide**, la barre de menus et la barre d'outils standard sont situés en haut. La **page de démarrage** est située au centre de la fenêtre d'application. Lorsque vous chargez une solution ou un projet, les éditeurs et les concepteurs apparaissent dans l'espace où se trouve la **Page de démarrage** . Lorsque vous développez une application, vous passez la majeure partie de votre temps dans cette zone centrale.

![IDE Visual Studio 2017 avec paramètres généraux appliqués](../media/exploreide-idewithgeneralsettings.png)

::: moniker-end

::: moniker range=">=vs-2019"

Quand vous lancez Visual Studio, la fenêtre de démarrage s’ouvre en premier. Sélectionnez **Continuer sans code** pour ouvrir l’environnement de développement. Vous allez voir les fenêtres Outils, les menus et barres d’outils ainsi que l’espace de la fenêtre principale. Les fenêtres Outils sont ancrées sur les côtés gauche et droit de la fenêtre d’application. Une zone de recherche, la barre de menus et la barre d’outils standard sont situées en haut. Quand vous chargez une solution ou un projet, les éditeurs et les concepteurs apparaissent dans l’espace central de la fenêtre d’application. Lorsque vous développez une application, vous passez la majeure partie de votre temps dans cette zone centrale.

::: moniker-end

## <a name="create-the-project"></a>Créer le projet

Lorsque vous créez une application dans Visual Studio, vous créez d'abord un projet et une solution. Pour cet exemple, vous allez créer un projet WPF (Windows Presentation Foundation).

::: moniker range="vs-2017"

1. Créez un projet. Dans la barre de menus, sélectionnez **fichier**  >  **nouveau**  >  **projet**.

     ![Dans la barre de menus, choisissez Fichier, Nouveau, Projet](../media/exploreide-filenewproject.png)

2. Dans la boîte de dialogue **Nouveau projet**, sélectionnez la catégorie **Installé** > **Visual Basic** > **Bureau Windows**, puis sélectionnez le modèle **Application WPF (.NET Framework)**. Nommez le projet **HelloWPFApp** et sélectionnez **OK**.

     ![Modèle Application WPF dans la boîte de dialogue Nouveau projet de Visual Studio](media/exploreide-newproject-vb.png)

Visual Studio crée la solution et le projet HelloWPFApp, et affiche les différents fichiers dans **l’Explorateur de solutions**. Le **Concepteur WPF** affiche une vue Design et une vue XAML pour *MainWindow.xaml* dans une vue fractionnée. Vous pouvez faire glisser le séparateur pour afficher une partie plus ou moins grande de chacune des vues. Vous pouvez choisir d'afficher uniquement le mode visuel ou uniquement le mode XAML. Les éléments suivants apparaissent dans l’ **Explorateur de solutions**:

![Explorateur de solutions avec fichiers HelloWPFApp chargés](../media/exploreide-hellowpfappfiles.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Ouvrez Visual Studio.

2. Sur l’écran **Créer un projet**, recherchez « WPF », choisissez **Application WPF (.NET Framework)**, puis choisissez **Suivant**.

   ![Modèle Application WPF dans la boîte de dialogue Nouveau projet de Visual Studio](media/vs-2019/exploreide-newprojectvb-vs2019.png)

3. Sur l’écran suivant, nommez le projet **HelloWPFApp** et choisissez **Créer**.

Visual Studio crée la solution et le projet HelloWPFApp, et affiche les différents fichiers dans **l’Explorateur de solutions**. Le **Concepteur WPF** affiche une vue Design et une vue XAML pour *MainWindow.xaml* dans une vue fractionnée. Vous pouvez faire glisser le séparateur pour afficher une partie plus ou moins grande de chacune des vues. Vous pouvez choisir d'afficher uniquement le mode visuel ou uniquement le mode XAML. Les éléments suivants apparaissent dans l’ **Explorateur de solutions**:

![Explorateur de solutions avec fichiers HelloWPFApp chargés](../media/vs-2019/exploreide-hellowpfappfiles.png)

::: moniker-end

> [!NOTE]
> Pour plus d’informations sur XAML (Extensible Application Markup Language), voir la page [Vue d’ensemble de XAML pour WPF](/dotnet/framework/wpf/advanced/xaml-overview-wpf).

Après avoir créé le projet, vous pouvez le personnaliser. Dans la fenêtre **Propriétés** (disponible dans le menu **Affichage** ), vous pouvez afficher et modifier les options des éléments du projet, des contrôles et des autres éléments d'une application.

### <a name="change-the-name-of-mainwindowxaml"></a>Changer le nom de MainWindow.xaml

Donnons un nom plus spécifique à MainWindow. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur *MainWindow. Xaml* , puis choisissez **Renommer**. Renommez le fichier avec *Greetings. Xaml*.

## <a name="design-the-user-interface-ui"></a>Créer l'interface utilisateur

Si le concepteur n’est pas ouvert, sélectionnez *Greetings. Xaml* dans **Explorateur de solutions**, puis appuyez sur **MAJ** + **F7** pour ouvrir le concepteur.

Nous allons ajouter trois types de contrôles à cette application : un contrôle <xref:System.Windows.Controls.TextBlock>, deux contrôles <xref:System.Windows.Controls.RadioButton> et un contrôle <xref:System.Windows.Controls.Button>.

### <a name="add-a-textblock-control"></a>Pour ajouter un contrôle TextBlock

1. Appuyez sur **CTRL** + **Q** pour activer la zone de recherche et tapez **boîte à outils**. Choisissez **Affichage > Boîte à outils** dans la liste des résultats.

2. Dans la fenêtre **Boîte à outils**, développez le nœud **Contrôles WPF communs** pour afficher le contrôle TextBlock.

     ![Boîte à outils avec le contrôle TextBlock en surbrillance](../media/exploreide-textblocktoolbox.png)

3. Ajoutez un contrôle TextBlock à l’aire de conception en choisissant l’élément **TextBlock** et en le faisant glisser vers la fenêtre de l’aire de conception. Centrez le contrôle vers le haut de la fenêtre. Dans Visual Studio 2019 et versions ultérieures, vous pouvez utiliser les recommandations en rouge pour centrer le contrôle.

Votre fenêtre doit ressembler à l'illustration suivante :

![Contrôle TextBlock sur le formulaire Greetings](../media/exploreide-greetingswithtextblockonly.png)

Le balisage XAML devrait ressembler à l’exemple suivant :

```xaml
<TextBlock HorizontalAlignment="Left" Margin="381,100,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
```

### <a name="customize-the-text-in-the-text-block"></a>Personnaliser le texte du bloc de texte

1. Dans la vue XAML, localisez la balise de TextBlock, puis remplacez l'attribut Text :

   ```xaml
   Text="Select a message option and then choose the Display button."
   ```

2. Recentrez l’élément TextBlock si nécessaire, puis enregistrez vos modifications en appuyant sur Ctrl+S ou en utilisant l’élément de menu **Fichier**.

Vous ajouterez ensuite deux contrôles [RadioButton](/dotnet/framework/wpf/controls/radiobutton) au formulaire.

### <a name="add-radio-buttons"></a>Ajouter des cases d’option

1. Dans la fenêtre **Boîte à outils**, recherchez le contrôle **RadioButton**.

     ![Fenêtre Boîte à outils avec contrôle RadioButton sélectionné](../media/exploreide-radiobuttontoolbox.png)

2. Ajoutez deux contrôles RadioButton à l’aire de conception en choisissant l’élément **RadioButton** et en le faisant glisser vers la fenêtre de l’aire de conception. Déplacez les boutons (en les sélectionnant et en utilisant les flèches) pour les placer côte à côte sous le contrôle TextBlock. Utilisez les indications rouges pour aligner les contrôles.

     Votre fenêtre doit se présenter comme suit :

     ![Formulaire Greetings avec contrôle TextBlock et deux cases d’option](../media/exploreide-greetingswithradiobuttons.png)

3. Dans la fenêtre **Propriétés** du contrôle RadioButton de gauche, affectez à la propriété **Nom** (propriété en haut de la fenêtre **Propriétés**) la valeur `HelloButton`.

     ![Fenêtre Propriétés de RadioButton](../media/exploreide-buttonproperties.png)

4. Dans la fenêtre **Propriétés** du contrôle RadioButton de droite, remplacez la valeur de la propriété **Name** par `GoodbyeButton`, puis enregistrez les modifications.

Vous pouvez maintenant afficher du texte pour chaque contrôle RadioButton. La procédure suivante met à jour la propriété **Contenu** d'un contrôle RadioButton.

### <a name="add-display-text-for-each-radio-button"></a>Ajouter un texte à afficher pour chaque case d’option

Mettez à jour l’attribut **content** pour `HelloButton` et `GoodbyeButton` vers `"Hello"` et `"Goodbye"` dans le XAML. Le balisage XAML doit maintenant ressembler à l’exemple suivant :

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Définir une case d’option activée par défaut

Dans cette étape, nous allons faire en sorte que la case HelloButton soit cochée par défaut. Ainsi, il y aura toujours une des deux cases d’option sélectionnée.

Dans l’affichage XAML, recherchez la balise du contrôle HelloButton et ajoutez un attribut **IsChecked** :

```xaml
IsChecked="True"
```

Le dernier élément de l’interface utilisateur que vous ajouterez est un contrôle [Button](/dotnet/framework/wpf/controls/button).

### <a name="add-the-button-control"></a>Ajouter le contrôle bouton

1. Dans la fenêtre **Boîte à outils**, recherchez le contrôle **Button**, puis ajoutez-le à l’aire de conception sous les contrôles RadioButton en le faisant glisser vers le formulaire en mode Design. Si vous utilisez Visual Studio 2019 ou une version ultérieure, une ligne rouge vous aide à centrer le contrôle.

2. Dans l’affichage XAML, changez la valeur de l’élément **Content** du contrôle Button de `Content="Button"` en `Content="Display"`, puis enregistrez les modifications.

     La balise doit ressembler à l’exemple suivant :   `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`

     Votre fenêtre doit ressembler à l'illustration suivante.

     ![Formulaire Greetings avec des étiquettes de contrôle](../media/exploreide-greetingswithcontrollabels.png)

### <a name="add-code-to-the-display-button"></a>Ajouter du code au bouton d’affichage

Quand cette application s’exécute, un message s’affiche si un utilisateur choisit une case d’option et choisit ensuite le bouton **Afficher**. Un message s'affiche pour Hello et un autre pour Goodbye. Pour créer ce comportement, vous ajoutez du code à l’événement `Button_Click` dans *Greetings.xaml.vb* ou *Greetings.xaml.cs*.

1. Dans l'aire de conception, double-cliquez sur le bouton **Afficher** .

     *Greetings.Xaml.vb* s’ouvre, avec le curseur dans l’événement `Button_Click`.

    ```vb
    Private Sub Button_Click(sender As Object, e As RoutedEventArgs)

    End Sub
    ```

2. Entrez le code suivant :

    ```vb
    If HelloButton.IsChecked = True Then
        MessageBox.Show("Hello.")
    ElseIf GoodbyeButton.IsChecked = True Then
        MessageBox.Show("Goodbye.")
    End If
    ```

3. Enregistrez l'application.

## <a name="debug-and-test-the-application"></a>Déboguer et tester l'application

Vous déboguerez ensuite l’application pour rechercher les erreurs et tester l’affichage correct des deux boîtes de message. Les instructions suivantes expliquent comment générer et lancer le débogueur. Pour plus d’informations, vous pouvez ultérieurement consulter [Générer une application WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) et [Déboguer WPF](../../debugger/debugging-wpf.md).

### <a name="find-and-fix-errors"></a>Rechercher et corriger des erreurs

Dans cette étape, vous recherchez l’erreur que nous avons provoquée précédemment en changeant le nom du fichier *MainWindow.xaml*.

#### <a name="start-debugging-and-find-the-error"></a>Démarrer le débogage et rechercher l’erreur

1. Démarrez le débogueur en appuyant sur **F5** ou en sélectionnant **Déboguer**, puis **Démarrer le débogage**.

   Une fenêtre **Mode arrêt** s’affiche. La fenêtre **Sortie** indique qu’une exception IOException s’est produite : Impossible de trouver la ressource « mainwindow.xaml ».

   ![Capture d’écran de message IOException](../media/exploreide-ioexception.png)

2. Arrêtez le débogueur en sélectionnant **Déboguer**  >  **arrêter le débogage**.

Nous avons renommé *MainWindow.xaml* en *Greetings.xaml* au début de ce didacticiel, mais le code continue de faire référence à *MainWindow.xaml* comme URI de démarrage de l’application. Cela explique pourquoi le projet ne démarre pas.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Spécifier Greetings.xaml comme URI de démarrage

1. Dans l’**Explorateur de solutions**, ouvrez le fichier *Application.xaml*.

2. Remplacez `StartupUri="MainWindow.xaml"` par `StartupUri="Greetings.xaml"`, puis enregistrez les modifications.

Redémarrez le débogueur (appuyez sur **F5**). Vous devez voir la fenêtre **Greetings** de l’application.

::: moniker range="vs-2017"
![Capture d’écran de l’application en cours d’exécution](media/exploreide-wpf-running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Capture d’écran de l’application en cours d’exécution](media/vs-2019/exploreide-wpf-running-app.png)
::: moniker-end

 Maintenant, fermez la fenêtre d’application pour arrêter le débogage.

### <a name="debug-with-breakpoints&quot;></a>Déboguer à l’aide de points d’arrêt

Vous pouvez tester le code pendant le débogage en ajoutant des points d’arrêt. Vous pouvez ajouter des points d’arrêt en choisissant **Déboguer**  >  le **point d’arrêt**, en cliquant dans la marge de gauche de l’éditeur à côté de la ligne de code où vous souhaitez que le saut se produise, ou en appuyant sur **F9**.

#### <a name=&quot;add-breakpoints&quot;></a>Ajouter des points d’arrêt

1. Ouvrez *Greetings. Xaml. vb*, puis sélectionnez la ligne suivante : `MessageBox.Show(&quot;Hello.")`

2. Ajoutez un point d’arrêt en appuyant sur **F9** ou à partir du menu en sélectionnant **Déboguer**, puis **Basculer le point d’arrêt**.

   Un cercle rouge apparaît à côté de la ligne de code dans la bordure gauche de la fenêtre de l’éditeur.

3. Sélectionnez la ligne suivante : `MessageBox.Show("Goodbye.")`.

4. Appuyez sur la touche **F9** pour ajouter un point d’arrêt, puis sur la touche **F5** pour démarrer le débogage.

5. Dans la fenêtre **Greetings** , choisissez la case d'option **Hello** , puis le bouton **Afficher** .

   La ligne `MessageBox.Show("Hello.")` est mise en surbrillance en jaune. Dans la partie inférieure de l’IDE, les fenêtres Automatique, Variables locales et Espion sont ancrées ensemble sur le côté gauche. Les fenêtres Pile des appels, Points d’arrêt, Paramètres d’exception, Commande, Immédiat et Sortie sont ancrées ensemble sur le côté droit.

   ![Capteur d’écran de point d’arrêt dans le débogueur](media/exploreide-debugbreakpoint.png)

6. Dans la barre de menus, choisissez **Déboguer**  >  **pas à pas sortant**.

     L’application reprend l’exécution et une boîte de message affiche le mot « Hello ».

7. Choisissez le bouton **OK** dans la boîte de message pour la fermer.

8. Dans la fenêtre **Greetings** , choisissez la case d'option **Goodbye** , puis le bouton **Afficher** .

     La ligne `MessageBox.Show("Goodbye.")` est mise en surbrillance en jaune.

9. Appuyez sur la touche **F5** pour continuer le débogage. Lorsque la boîte de message s'affiche, choisissez le bouton **OK** sur la boîte de message pour la fermer.

10. Fermez la fenêtre d’application pour arrêter le débogage.

11. Dans la barre de menus, choisissez **Déboguer**  >  **Désactiver tous les points d’arrêt**.

### <a name="view-a-representation-of-the-ui-elements"></a>Afficher une représentation des éléments d’interface utilisateur

Dans l’application en cours d’exécution, vous devriez voir un widget qui apparaît en haut de la fenêtre. Il s’agit d’une application auxiliaire de Runtime qui fournit un accès rapide à certaines fonctionnalités de débogage utiles. Cliquez sur le premier bouton, puis sur **arborescence d’éléments visuels en direct**. Vous devez voir une fenêtre avec une arborescence qui contient tous les éléments visuels de votre page. Développez les nœuds pour rechercher les boutons que vous avez ajoutés.

![Capture d’écran de la fenêtre d’arborescence d’éléments visuels dynamique](media/vs-2019/exploreide-live-visual-tree.png)

### <a name="build-a-release-version-of-the-application"></a>Générer une version Release de l'application

Maintenant que vous avez vérifié que tout fonctionne, vous pouvez préparer une version Release de l’application.

1. Dans le menu principal, sélectionnez **générer** une  >  **solution propre** pour supprimer les fichiers intermédiaires et les fichiers de sortie créés pendant les générations précédentes. Cette opération n'est pas nécessaire, mais elle nettoie les sorties des versions Debug.

2. Remplacez la configuration de build **Debug** pour HelloWPFApp par **Release** à l’aide du contrôle de liste déroulante de la barre d’outils (« Debug » est actuellement affiché).

3. Générez la solution en choisissant **générer**  >  **générer la solution**.

Félicitations ! Vous avez terminé ce didacticiel. Vous pouvez trouver le *.exe* que vous avez généré dans le répertoire de votre solution et du projet (*. ..\HelloWPFApp\HelloWPFApp\bin\Release*).

## <a name="see-also"></a>Voir aussi

::: moniker range="vs-2017"

- [Nouveautés de Visual Studio 2017](../../ide/whats-new-visual-studio-2017.md)
- [Conseils de productivité](../../ide/productivity-features.md)

::: moniker-end

::: moniker range="vs-2019"

- [Nouveautés de Visual Studio 2019](../../ide/whats-new-visual-studio-2019.md)
- [Conseils de productivité](../../ide/productivity-features.md)

::: moniker-end

::: moniker range="vs-2022"

- [Conseils de productivité](../../ide/productivity-features.md)

::: moniker-end
