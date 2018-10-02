---
title: 'Procédure pas à pas : création d’un composant simple avec Visual C# ou Visual Basic | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: get-started-article
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 269616a5d8725399ecc5f577bc400b75de596332
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47502379"
---
# <a name="walkthrough-create-a-simple-application-with-visual-c-or-visual-basic"></a>Procédure pas à pas : création d'un composant simple avec Visual C# ou Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [procédure pas à pas : créer une Application Simple avec Visual c# ou Visual Basic](https://docs.microsoft.com/visualstudio/ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic).  
  
En suivant cette procédure pas-à-pas, vous vous familiariserez avec la plupart des outils, boîtes de dialogue et concepteurs que vous pouvez utiliser lorsque vous développez des applications avec Visual Studio. Vous allez créer une application « Hello, World » simple, concevoir l'interface utilisateur, ajouter du code et déboguer des erreurs, tout en découvrant l'utilisation de l'environnement de développement intégré (IDE).  
  
 Cette rubrique contient les sections suivantes :  
  
 [Configurer l'IDE](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_ConfigureIDE)  
  
 [Créer une application simple](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_CreateApp)  
  
 [Déboguer et tester l'application](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_DebugTest)  
  
> [!NOTE]
>  Cette procédure pas-à-pas est basée sur Visual Studio Professional, qui offre le modèle d'application WPF sur lequel vous allez vous baser pour générer le projet. Visual Studio Express pour Windows Desktop offre également ce modèle, mais pas Visual Studio Express pour Windows et Visual Studio Express pour le Web. Pour obtenir une présentation de l’utilisation de Visual Studio Express pour Windows, consultez le [Centre de développement des applications du Windows Store](http://msdn.microsoft.com/windows/apps/br229519). Pour obtenir une présentation de l’utilisation de Visual Studio Express pour le web, consultez [Get Started with ASP.NET](http://www.asp.net/get-started)(Prise en main d’ASP.NET). De plus, votre édition de Visual Studio et les paramètres que vous utilisez déterminent les noms et les emplacements des éléments de l'interface utilisateur. Consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
##  <a name="BKMK_ConfigureIDE"></a> Configurer l'IDE  
 Au premier démarrage de Visual Studio, Visual Studio vous invite à vous connecter avec un compte de service Microsoft, [Se connecter à Visual Studio](http://blogs.msdn.com/b/visualstudio/archive/2013/06/28/welcome-sign-in-to-visual-studio.aspx). Vous n'avez pas besoin de vous connecter immédiatement ; vous pouvez le faire ultérieurement.  
  
 Lors de votre lancement de Visual Studio, vous devez choisir une combinaison de paramètres qui applique un ensemble de personnalisations prédéfinies à l'IDE. Chaque combinaison de paramètres a été conçue pour vous faciliter le développement d'applications.  
  
 Cette procédure pas à pas présume que vous ayez appliqué les **Paramètres de développement généraux**. Une personnalisation minime est ainsi appliquée à l'IDE. Si vous avez déjà choisi C# ou Visual Basic (les deux conviennent), vous n'êtes pas obligé de modifier vos paramètres.  Si vous souhaitez modifier vos paramètres, vous pouvez utiliser l' **Assistant Importation et exportation de paramètres**. Consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Après avoir ouvert Visual Studio, vous pouvez identifier les fenêtres Outil, les menus et barres d'outils et l'espace de la fenêtre principale. Les fenêtres Outil sont ancrées sur les côtés gauche et droit de la fenêtre d'application. **Lancement rapide**, la barre de menus et la barre d'outils standard sont situés en haut. La **page de démarrage**est située au centre de la fenêtre d'application. Lorsque vous chargez une solution ou un projet, les éditeurs et les concepteurs apparaissent dans l'espace où se trouve la **Page de démarrage** . Lorsque vous développez une application, vous passez la majeure partie de votre temps dans cette zone centrale.  
  
 Figure 2 : IDE de Visual Studio  
  
 ![IDE avec les paramètres généraux appliqués](../ide/media/exploreide-idewithgeneralsettings.png "ExploreIDE-IDEwithgeneralsettings")  
  
 Vous pouvez personnaliser davantage Visual Studio. Vous pouvez par exemple modifier le type de police et la taille utilisée pour le texte dans l’éditeur ou le thème de couleur appliqué à l’IDE à l’aide de la boîte de dialogue **Options**. Selon la combinaison de paramètres appliquée, certains éléments de cette boîte de dialogue peuvent ne pas apparaître automatiquement. Vous pouvez vous assurer que toutes les options possibles s'affichent en choisissant la case à cocher **Afficher tous les paramètres** .  
  
 Figure 3 : Boîte de dialogue Options  
  
 ![Boîte de dialogue Options, avec l’option Afficher tous les paramètres](../ide/media/exploreide-optionsdialogbox.png "ExploreIDE-Optionsdialogbox")  
  
 Dans cet exemple, vous changerez le thème de couleur « clair » de l'IDE par « sombre ».  Vous pouvez poursuivre pour créer un projet si vous le souhaitez.  
  
#### <a name="to-change-the-color-theme-of-the-ide"></a>Pour modifier le thème de couleur de l'IDE  
  
1.  Ouvrez la boîte de dialogue **Options** en sélectionnant le menu **Outils** en haut, puis l'élément **Options …** .  
  
     ![Options de commande dans le menu Outils](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE-ToolsOptionsmenu")  
  
2.  Modifiez le **Thème de couleur** par **Foncé**, puis cliquez sur **OK**.  
  
     ![Thème de couleur foncée sélectionné](../ide/media/exploreide-darkthemeoptionsdlgbox.png "ExploreIDE-Darkthemeoptionsdlgbox")  
  
 Dans Visual Studio, les couleurs devraient correspondre à l'image suivante :  
  
 ![IDE avec le thème foncé appliqué](../ide/media/exploreide-darkthemeide.png "ExploreIDE-DarkThemeIDE")  
  
 Le thème de couleur utilisé pour les images dans le reste de cette procédure pas à pas est le thème clair. Pour plus d’informations sur la personnalisation de l’IDE, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
##  <a name="BKMK_CreateApp"></a> Créer une application simple  
  
### <a name="create-the-project"></a>Créer le projet  
 Lorsque vous créez une application dans Visual Studio, vous créez d'abord un projet et une solution. Pour cet exemple, vous allez créer un projet Windows Presentation Foundation.  
  
##### <a name="to-create-the-wpf-project"></a>Pour créer le projet WPF  
  
1.  Créer un nouveau projet. Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet...**.  
  
     ![Dans la barre de menus, choisissez Fichier, Nouveau, Projet](../ide/media/exploreide-filenewproject.png "ExploreIDE-FileNewProject")  
  
     Vous pouvez également taper **Nouveau projet** dans la zone **Lancement rapide** pour effectuer la même opération.  
  
     ![Dans la zone de lancement rapide, indiquez "nouveau projet"](../ide/media/exploreide-quicklaunchnewprojectsmall.png "ExploreIDE-QuickLaunchNewProjectsmall")  
  
2.  Choisissez le modèle Application WPF Visual Basic ou Application WPF Visual C# en sélectionnant dans le volet gauche **Installé**, **Modèles**, **Visual C#**, **Windows**, par exemple, puis Application WPF dans le volet du milieu.  Nommez le projet HelloWPFApp en bas de la boîte de dialogue Nouveau projet.  
  
     ![Créer un projet Visual Basic WPF, HelloWPFApp](../ide/media/exploreide-newprojectvb.png "ExploreIDE-NewProjectVB")  
  
     OU  
  
     ![Créer un projet Visual C&#35; WPF, HelloWPFApp](../ide/media/exploreide-newprojectcsharp.png "ExploreIDE-NewProjectcsharp")  
  
 Visual Studio crée la solution et le projet HelloWPFApp, et l' **l'Explorateur de solutions** affiche les différents fichiers. Le Concepteur WPF affiche un mode Design et une vue XAML de MainWindow.xaml en mode Fractionné. Vous pouvez faire glisser le séparateur pour afficher une partie plus ou moins grande de chacune des vues.  Vous pouvez choisir d'afficher uniquement le mode visuel ou uniquement le mode XAML. (Pour plus d'informations, consultez [Concepteur WPF pour les développeurs Windows Forms](http://msdn.microsoft.com/en-us/47ad0909-e89b-4996-b4ac-874d929f94ca)). Les éléments suivants apparaissent dans l' **Explorateur de solutions**:  
  
 Figure 5 : Éléments du projet  
  
 ![Explorateur de solutions avec les fichiers HelloWPFApp chargés](../ide/media/exploreide-hellowpfappfiles.png "ExploreIDE-HelloWPFAppFiles")  
  
 Après avoir créé le projet, vous pouvez le personnaliser. Dans la fenêtre **Propriétés** (disponible dans le menu **Affichage** ), vous pouvez afficher et modifier les options des éléments du projet, des contrôles et des autres éléments d'une application. À l'aide des propriétés d'un projet et des pages de propriétés, vous pouvez afficher et modifier les options des projets et des solutions.  
  
##### <a name="to-change-the-name-of-mainwindowxaml"></a>Pour modifier le nom de MainWindow.xaml  
  
1.  Dans la procédure suivante, vous donnerez à MainWindow un nom plus spécifique. Dans l' **Explorateur de solutions**, sélectionnez MainWindow.xaml. Vous pouvez voir la fenêtre **Propriétés** , mais si tel n'est pas le cas, choisissez le menu **Affichage** et l'élément **Fenêtre des propriétés** . Remplacez la propriété **Nom de fichier** par `Greetings.xaml`.  
  
     ![Fenêtre Propriétés avec Nom de fichier en surbrillance](../ide/media/exploreide-filenameinpropertieswindow.png "ExploreIDE-FilenameinPropertiesWindow")  
  
     L'**Explorateur de solutions** indique que le nom du fichier est maintenant Greetings.xaml. Si vous développez le nœud MainWindow.xaml (en plaçant le focus dans le nœud et en appuyant sur la touche flèche droite), vous voyez que le nom de MainWindow.xaml.vb ou MainWindow.xaml.cs est désormais Greetings.xaml.vb ou Greetings.xaml.cs. Ce fichier de code est imbriqué sous le nœud de fichier .xaml pour montrer qu'ils sont étroitement liés entre eux.  
  
    > [!WARNING]
    >  Cette modification provoque une erreur que vous apprendrez à déboguer et à corriger à une étape ultérieure.  
  
2.  Dans l' **Explorateur de solutions**, ouvrez Greetings.xaml en mode concepteur (en appuyant sur la touche Entrée quand le nœud a le focus) et sélectionnez la barre de titre de la fenêtre à l'aide de la souris.  
  
3.  Dans la fenêtre **Propriétés** , remplacez la valeur de la propriété **Titre** par `Greetings`.  
  
 La barre de titre de MainWindow.xaml indique maintenant Greetings.  
  
### <a name="design-the-user-interface-ui"></a>Créer l'interface utilisateur  
 Nous allons ajouter trois types de contrôles à cette application : un contrôle TextBlock, deux contrôles RadioButton et un contrôle Button.  
  
##### <a name="to-add-a-textblock-control"></a>Pour ajouter un contrôle TextBlock  
  
1.  Ouvrez la fenêtre **Boîte à outils** en choisissant le menu **Affichage** , puis l'élément **Boîte à outils** .  
  
2.  Dans la **Boîte à outils**, recherchez le contrôle TextBlock.  
  
     ![Boîte à outils avec le contrôle TextBlock en surbrillance](../ide/media/exploreide-textblocktoolbox.png "ExploreIDE-TextBlockToolbox")  
  
3.  Ajoutez un contrôle TextBlock à l'aire de conception en choisissant l'élément TextBlock et en le faisant glisser vers la fenêtre de l'aire de conception.  Centrez le contrôle vers le haut de la fenêtre.  
  
 Votre fenêtre doit ressembler à l'illustration suivante :  
  
 Figure 7 : Fenêtre Greetings avec le contrôle TextBlock  
  
 ![Contrôle TextBlock sur le formulaire Greetings](../ide/media/exploreide-greetingswithtextblockonly.png "ExploreIDE-GreetingswithTextblockonly")  
  
 Le balisage XAML doit ressembler à ce qui suit :  
  
```  
<TextBlock HorizontalAlignment="Center" TextWrapping="Wrap" VerticalAlignment="Center" RenderTransformOrigin="4.08,2.312" Margin="237,57,221,238"><Run Text="TextBlock"/><InlineUIContainer><TextBlock TextWrapping="Wrap" Text="TextBlock"/>  
```  
  
##### <a name="to-customize-the-text-in-the-text-block"></a>Pour personnaliser le texte du bloc de texte  
  
1.  Dans la vue XAML, localisez la balise de TextBlock, puis remplacez l'attribut Text : `Text=”Select a message option and then choose the Display button.”`  
  
2.  Si le TextBlock ne se développe pas pour s'ajuster au mode Design, agrandissez le contrôle TextBlock, à l'aide des poignées latérales, afin qu'il affiche l'ensemble du texte.  
  
3.  Enregistrez vos modifications en appuyant sur Ctrl+S ou à l'aide de l'élément de menu **Fichier** .  
  
 Ensuite, vous allez ajouter deux contrôles [RadioButton](http://msdn.microsoft.com/library/6c9ba847-eab7-4bba-9c74-6b56ef72067b) au formulaire.  
  
##### <a name="to-add-radio-buttons"></a>Pour ajouter des cases d'option  
  
1.  Dans la **Boîte à outils**, recherchez le contrôle RadioButton.  
  
     ![Fenêtre Boîte à outils avec le contrôle RadioButton sélectionné](../ide/media/exploreide-radiobuttontoolbox.png "ExploreIDE-RadioButtonToolbox")  
  
2.  Ajoutez deux contrôles RadioButton à l'aire de conception en choisissant l'élément RadioButton et en le faisant glisser vers la fenêtre de l'aire de conception deux fois de suite, puis déplacez les boutons (en les sélectionnant et en utilisant les flèches de direction) afin que les boutons apparaissent côte à côte sous le contrôle TextBlock.  
  
     Votre fenêtre doit se présenter comme suit :  
  
     Figure 8 : RadioButtons dans la fenêtre Greetings.  
  
     ![Formulaire Greetings avec un bloc de texte et deux cases d’option](../ide/media/exploreide-greetingswithradiobuttons.png "ExploreIDE-Greetingswithradiobuttons")  
  
3.  Dans la fenêtre **Propriétés** du contrôle RadioButton de gauche, affectez à la propriété **Nom** (propriété en haut de la fenêtre **Propriétés**) la valeur `RadioButton1`.  Assurez-vous que vous avez sélectionné le contrôle RadioButton et pas la grille en arrière-plan sur le formulaire ; le champ Type de la Fenêtre des propriétés sous le champ Nom doit afficher RadioButton.  
  
4.  Dans la fenêtre **Propriétés** du contrôle RadioButton approprié, modifiez la propriété **Nom** en `RadioButton2`, puis enregistrez vos modifications en appuyant sur Ctrl+S ou à l'aide de l'élément de menu **Fichier** .  Assurez-vous d'avoir sélectionné le contrôle RadioButton avant toute modification et tout enregistrement.  
  
 Vous pouvez maintenant afficher du texte pour chaque contrôle RadioButton. La procédure suivante met à jour la propriété **Contenu** d'un contrôle RadioButton.  
  
##### <a name="to-add-display-text-for-each-radio-button"></a>Pour ajouter un texte à afficher pour chaque case d'option  
  
1.  Sur l'aire de conception, ouvrez le menu contextuel de RadioButton1 en appuyant sur le bouton droit de la souris tout en sélectionnant RadioButton1, choisissez **Modifier le texte**, puis entrez `Hello`.  
  
2.  Ouvrez le menu contextuel de RadioButton2 en appuyant sur le bouton droit de la souris tout en sélectionnant RadioButton2, choisissez **Modifier le texte**, puis entrez `Goodbye`.  
  
 Le dernier élément d’interface utilisateur que vous allez ajouter est un contrôle [Button](http://msdn.microsoft.com/library/a9d8f5a5-c98c-463e-808a-5a4e63173098).  
  
##### <a name="to-add-the-button-control"></a>Pour ajouter le contrôle bouton  
  
1.  Dans la **Boîte à outils**, recherchez le contrôle **Button** , puis ajoutez-le à l'aire de conception sous les contrôles RadioButton en sélectionnant Button et en le faisant glisser vers le formulaire en mode Design.  
  
2.  Dans la vue XAML, modifiez la valeur du **Contenu** du contrôle Button de `Content=”Button”` en `Content=”Display”`, puis enregistrez les modifications (Ctrl+S ou élément de menu **Fichier**).  
  
     La balise doit ressembler à l'exemple suivant : `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`  
  
 Votre fenêtre doit ressembler à l'illustration suivante.  
  
 Figure 9 : Interface utilisateur finale de Greetings  
  
 ![Formulaire Greetings avec des étiquettes de contrôle](../ide/media/exploreide-greetingswithconrollabels.png "ExploreIDE-Greetingswithconrollabels")  
  
### <a name="add-code-to-the-display-button"></a>Ajouter du code au bouton d'affichage  
 Lorsque cette application s'exécute, un message s'affiche une fois qu'un utilisateur choisit une case d'option et choisit ensuite le bouton **Afficher** . Un message s'affiche pour Hello et un autre pour Goodbye. Pour créer ce comportement, vous ajouterez du code à l'événement Button_Click dans Greetings.xaml.vb ou Greetings.xaml.cs.  
  
##### <a name="add-code-to-display-message-boxes"></a>Ajoutez le code pour afficher des boîtes de message  
  
1.  Dans l'aire de conception, double-cliquez sur le bouton **Afficher** .  
  
     Greetings.xaml.vb ou Greetings.xaml.cs s'ouvre, avec le curseur dans l'événement Button_Click. Vous pouvez également ajouter un gestionnaire d'événements Click comme suit (si le code collé présente une ligne ondulée rouge sous les noms, vous n'avez probablement pas sélectionné ni renommé les contrôles RadioButton sur l'aire de conception) :  
  
     Pour Visual Basic, le gestionnaire d'événements doit ressembler à ceci :  
  
    ```vb  
    Private Sub Button_Click_1(sender As Object, e As RoutedEventArgs)  
  
    End Sub  
    ```  
  
     Pour Visual C#, le gestionnaire d'événements doit ressembler à ceci :  
  
    ```csharp  
    private void Button_Click_1(object sender, RoutedEventArgs e)  
    {  
  
    }  
    ```  
  
2.  Pour Visual Basic, entrez le code suivant :  
  
    ```vb  
    If RadioButton1.IsChecked = True Then  
        MessageBox.Show("Hello.")  
    Else RadioButton2.IsChecked = True  
        MessageBox.Show("Goodbye.")  
    End If  
  
    ```  
  
     Pour Visual C#, entrez le code suivant :  
  
    ```  
    if (RadioButton1.IsChecked == true)  
    {  
        MessageBox.Show("Hello.");  
    }  
    else  
    {  
        RadioButton2.IsChecked = true;  
        MessageBox.Show("Goodbye.");  
    }  
    ```  
  
3.  Enregistrez l'application.  
  
##  <a name="BKMK_DebugTest"></a> Déboguer et tester l'application  
 Vous déboguerez ensuite l'application pour rechercher les erreurs et tester l'affichage correct des deux boîtes de message. Les instructions suivantes expliquent comment générer et lancer le débogueur. Pour plus d’informations, vous pourrez ultérieurement consulter [Génération d’une application WPF (WPF)](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c) et [Débogage WPF](../debugger/debugging-wpf.md).  
  
### <a name="find-and-fix-errors"></a>Rechercher et corriger des erreurs  
 Dans cette étape, vous trouverez l'erreur que nous avons provoquée précédemment en modifiant le nom du fichier XAML de la fenêtre principale.  
  
##### <a name="to-start-debugging-and-find-the-error"></a>Pour démarrer le débogage et rechercher l'erreur  
  
1.  Démarrez le débogueur en sélectionnant **Déboguer**, puis **Démarrer le débogage**.  
  
     ![Commande Démarrer le débogage du menu Débogage](../ide/media/exploreide-startdebugging.png "ExploreIDE-StartDebugging")  
  
     Une boîte de dialogue s'affiche, indiquant qu'une exception IOException s'est produite : Impossible de localiser la ressource « mainwindow.xaml ».  
  
2.  Choisissez le bouton **OK** , puis arrêtez le débogueur.  
  
     ![Commande Arrêter le débogage du menu Débogage](../ide/media/exploreide-stopdebugging.png "ExploreIDE-StopDebugging")  
  
 Nous avons renommé Mainwindow.xaml en Greetings.xaml au début de la procédure, mais le code continue toujours de faire référence à Mainwindow.xaml comme URI de démarrage de l'application. C'est pourquoi le projet ne peut pas démarrer.  
  
##### <a name="to-specify-greetingsxaml-as-the-startup-uri"></a>Pour spécifier Greetings.xaml comme l'URI de démarrage  
  
1.  Dans l' **Explorateur de solutions**, ouvrez le fichier App.xaml (dans le projet C#) ou le fichier Application.xaml (dans le projet Visual Basic) en mode XAML (il ne peut pas être ouvert en mode Design) en sélectionnant le fichier et en appuyant sur Entrée (ou en double-cliquant sur le fichier).  
  
2.  Modifiez `StartupUri="MainWindow.xaml"` en `StartupUri="Greetings.xaml"`, puis enregistrez les modifications avec Ctrl+S.  
  
 Démarrez à nouveau le débogueur (appuyez sur F5). Vous devez voir la fenêtre Greetings de l'application.  
  
### <a name="to-debug-with-breakpoints"></a>Pour déboguer avec des points d'arrêt  
 En ajoutant des points d'arrêt, vous pouvez tester le code pendant le débogage. Vous pouvez ajouter des points d'arrêt en choisissant **Déboguer** dans le menu principal, puis **Basculer le point d'arrêt** , ou en cliquant dans la marge de gauche de l'éditeur à côté de la ligne de code, à l'emplacement où vous voulez que l'arrêt se produise.  
  
##### <a name="to-add-breakpoints"></a>Pour ajouter des points d'arrêt  
  
1.  Ouvrez Greetings.xaml.vb ou Greetings.xaml.cs, puis sélectionnez la ligne suivante : `MessageBox.Show("Hello.")`  
  
2.  Ajoutez un point d'arrêt à partir du menu en sélectionnant **Déboguer**, puis **Basculer le point d'arrêt**.  
  
     ![Commande Basculer le point d’arrêt du menu Débogage](../ide/media/exploreide-togglebreakpoint.png "ExploreIDE-ToggleBreakpoint")  
  
     Un cercle rouge apparaît à côté de la ligne de code dans la bordure gauche de la fenêtre de l’éditeur.  
  
3.  Sélectionnez la ligne suivante : `MessageBox.Show("Goodbye.")`.  
  
4.  Appuyez sur la touche F9 pour ajouter un point d'arrêt, puis sur la touche F5 pour démarrer le débogage.  
  
5.  Dans la fenêtre **Greetings** , choisissez la case d'option **Hello** , puis le bouton **Afficher** .  
  
     La ligne `MessageBox.Show("Hello.")` est mise en surbrillance en jaune. Dans la partie inférieure de l'IDE, les fenêtres Automatique, Variables locales et Espion sont ancrées ensemble sur le côté gauche. Les fenêtres Pile des appels, Points d'arrêt, Commande, Immédiat et Sortie sont ancrées ensemble sur le côté droit.  
  
6.  Dans la barre de menus, choisissez **Déboguer**, **Pas à pas sortant**.  
  
     L'application reprend l'exécution et une boîte de message affiche le mot « Hello ».  
  
7.  Choisissez le bouton **OK** dans la boîte de message pour la fermer.  
  
8.  Dans la fenêtre **Greetings** , choisissez la case d'option **Goodbye** , puis le bouton **Afficher** .  
  
     La ligne `MessageBox.Show("Goodbye.")` est mise en surbrillance en jaune.  
  
9. Appuyez sur la touche F5 pour continuer le débogage. Lorsque la boîte de message s'affiche, choisissez le bouton **OK** sur la boîte de message pour la fermer.  
  
10. Appuyez sur les touches MAJ+F5 (appuyez d'abord sur la touche MAJ et tout en la maintenant enfoncée, appuyez sur F5) pour arrêter le débogage.  
  
11. Dans la barre de menus, choisissez **Débogage**, **Désactiver tous les points d'arrêt**.  
  
### <a name="build-a-release-version-of-the-application"></a>Générer une version Release de l'application  
 Maintenant que vous avez vérifié que tout fonctionne, vous pouvez préparer une version Release de l'application.  
  
##### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Pour nettoyer les fichiers solution et générer une version Release  
  
1.  Dans le menu principal, sélectionnez **Générer**, puis **Nettoyer la solution** pour supprimer les fichiers intermédiaires et les fichiers de sortie créés pendant les générations précédentes.  Cette opération n'est pas nécessaire, mais elle nettoie les sorties des versions Debug.  
  
     ![Commande Nettoyer la solution du menu Générer](../ide/media/exploreide-cleansolution.png "ExploreIDE-CleanSolution")  
  
2.  Modifiez la configuration de build pour HelloWPFApp de **Débogage** en **Version finale** à l’aide du contrôle déroulant de la barre d’outils (à cet instant, c'est « Débogage » qui s’affiche).  
  
     ![Barre d’outils Standard avec Version finale sélectionné](../ide/media/exploreide-releaseversion.png "ExploreIDE-ReleaseVersion")  
  
3.  Générez la solution en choisissant **Générer**, puis **Générer la solution** ou appuyez sur la touche F6.  
  
     ![Commande Générer la solution du menu Générer](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")  
  
 Félicitations ! Vous avez terminé cette procédure. Le fichier .exe que vous avez généré se trouve dans le répertoire de votre solution et de votre projet (…\HelloWPFApp\HelloWPFApp\bin\Release\\). Pour explorer d’autres exemples, consultez [Exemples Visual Studio](../ide/visual-studio-samples.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés dans Visual Studio 2015](../what-s-new-in-visual-studio-2015.md)   
 [Bien démarrer avec le développement dans Visual Studio](../ide/get-started-developing-with-visual-studio.md)   
 [Conseils de productivité](../ide/productivity-tips-for-visual-studio.md)



