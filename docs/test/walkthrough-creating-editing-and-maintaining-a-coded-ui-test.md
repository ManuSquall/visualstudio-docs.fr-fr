---
title: Créer un test codé de l'interface utilisateur
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: d7659de6e90ca13172459b1bcc1e305e14a91cfc
ms.sourcegitcommit: a916ce1eec19d49f060146f7dd5b65f3925158dd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2019
ms.locfileid: "55231959"
---
# <a name="walkthrough-create-edit-and-maintain-a-coded-ui-test"></a>Procédure pas à pas : Créer, modifier et gérer un test codé de l’interface utilisateur

Dans cette procédure pas à pas, vous allez apprendre à créer, modifier et gérer un test codé de l’interface utilisateur pour tester une application WPF (Windows Presentation Framework). La procédure pas à pas fournit des solutions pour corriger des tests interrompus par différents problèmes de synchronisation et de refactorisation des contrôles.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-wpf-app"></a>Créer une application WPF

1.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis sélectionnez **Projet**.

     La boîte de dialogue **Nouveau projet** s’affiche.

2.  Dans le volet **Installé**, développez **Visual C#** puis sélectionnez **Bureau Windows**.

3.  Au-dessus du volet central, vérifiez que la liste déroulante des frameworks cibles est définie sur **.NET Framework 4.5**.

4.  Dans le volet central, sélectionnez le modèle **Application WPF**.

5.  Dans la zone de texte **Nom**, tapez **SimpleWPFApp**.

6.  Choisissez un dossier dans lequel enregistrer le projet. Dans la zone de texte **Emplacement**, tapez le nom du dossier.

7.  Cliquez sur **OK**.

     Le **Concepteur WPF pour Visual Studio** s’ouvre et affiche la fenêtre MainWindow du projet.

8.  Si la boîte à outils n'est pas encore ouverte, ouvrez-la. Choisissez le menu **Affichage**, puis **Boîte à outils**.

9. Sous la section **Tous les contrôles WPF**, faites glisser un contrôle **Button**, **CheckBox** et **ProgressBar** sur la fenêtre MainWindow de l’aire de conception.

10. Sélectionnez le contrôle **Button**. Dans la fenêtre **Propriétés**, changez la valeur de la propriété **Nom** de \<Sans nom> en button1. Changez ensuite la valeur de la propriété **Contenu** de Button en Start.

11. Sélectionnez le contrôle **ProgressBar**. Dans la fenêtre **Propriétés**, changez la valeur de la propriété **Nom** de \<Sans nom> en progressBar1. Changez ensuite la valeur de la propriété **Maximum** de **100** en **10000**.

12. Sélectionnez le contrôle **Checkbox**. Dans la fenêtre **Propriétés**, changez la valeur de la propriété **Nom** de \<Sans nom> en checkBox1 et effacez la valeur de la propriété **IsEnabled**.

     ![Application WPF simple](../test/media/codedui_wpfapp.png)

13. Double-cliquez sur le contrôle bouton pour ajouter un gestionnaire d'événements Click.

     *MainWindow.xmal.cs* s’affiche dans l’éditeur de code avec le curseur dans la nouvelle méthode button1_Click.

14. Au début de la classe MainWindow, ajoutez un délégué. Le délégué sera utilisé pour la barre de progression. Pour ajouter le délégué, ajoutez le code suivant :

    ```csharp
    public partial class MainWindow : Window
    {
            private delegate void ProgressBarDelegate(System.Windows.DependencyProperty dp, Object value);

        public MainWindow()
        {

            InitializeComponent();
        }
    ```

15. Dans la méthode button1_Click, ajoutez le code suivant :

    ```csharp
    private void button1_Click(object sender, RoutedEventArgs e)
    {
        double progress = 0;

        ProgressBarDelegate updatePbDelegate =
            new ProgressBarDelegate(progressBar1.SetValue);

        do
        {
            progress ++;

            Dispatcher.Invoke(updatePbDelegate,
                System.Windows.Threading.DispatcherPriority.Background,
                new object[] { ProgressBar.ValueProperty, progress });
            progressBar1.Value = progress;
        }
        while (progressBar1.Value != progressBar1.Maximum);

        checkBox1.IsEnabled = true;
    }
    ```

16. Enregistrez le fichier.

### <a name="run-the-wpf-app"></a>Exécuter l’application WPF

1.  Dans le menu **Débogage**, sélectionnez **Démarrer le débogage** ou appuyez sur **F5**.

2.  Notez que le contrôle CheckBox est désactivé. Choisissez **Démarrer**.

     En quelques secondes, la barre de progression atteint 100 %.

3.  Vous pouvez maintenant sélectionner le contrôle CheckBox.

4.  Fermez SimpleWPFApp.

## <a name="create-a-shortcut-to-the-wpf-app"></a>Créer un raccourci vers l’application WPF

1.  Recherchez l'application SimpleWPFApp que vous avez créée précédemment.

2.  Créez un raccourci sur le bureau à l'application SimpleWPFApp. Cliquez avec le bouton droit sur *SimpleWPFApp.exe* et choisissez **Copier**. Sur votre Bureau, cliquez avec le bouton droit et choisissez **Coller le raccourci**.

    > [!TIP]
    > Un raccourci vers l’application simplifie l’ajout ou la modification des tests codés de l'interface utilisateur de votre application parce qu’il permet de démarrer l’application rapidement.

## <a name="create-a-coded-ui-test-for-simplewpfapp"></a>Créer un test codé de l’interface utilisateur pour SimpleWPFApp

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur la solution, choisissez **Ajouter** puis sélectionnez **Nouveau projet**.

     La boîte de dialogue **Ajouter un nouveau projet** apparaît.

1. Dans le volet **Installé**, développez **Visual C#** puis sélectionnez **Test**.

1. Dans le volet central, sélectionnez le modèle **Projet de test codé de l’interface utilisateur**.

   > [!NOTE]
   > Si vous ne voyez pas le modèle **Projet de test codé de l’interface utilisateur**, vous devez [installer le composant de test codé de l’interface utilisateur](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

1. Cliquez sur **OK**.

     Le nouveau projet de test codé de l’interface utilisateur nommé **CodedUITestProject1** est ajouté à votre solution.

     La boîte de dialogue **Générer le code pour le test codé de l’interface utilisateur** s’affiche.

1. Sélectionnez l’option **Enregistrer les actions, modifier le mappage de l’interface utilisateur ou ajouter des assertions** et choisissez **OK**.

     La boîte de dialogue **UIMap - Générateur de test codé de l’interface utilisateur** apparaît et la fenêtre Visual Studio est réduite.

     Pour plus d’informations sur les options de la boîte de dialogue, consultez [Créer des tests codés de l’interface utilisateur](../test/use-ui-automation-to-test-your-code.md).

1. Choisissez **Démarrer l’enregistrement** dans la boîte de dialogue **UIMap - Générateur de test codé de l’interface utilisateur**.

     ![Démarrer l'enregistrement](../test/media/cuit_builder_record.png)

     Vous pouvez mettre l'enregistrement en pause si nécessaire, par exemple si vous recevez du courrier électronique et que vous souhaitez y répondre.

     ![Suspendre l'enregistrement](../test/media/cuit_.png)

    > [!WARNING]
    > Toutes les actions effectuées sur le Bureau sont enregistrées. Mettez l'enregistrement en pause si vous effectuez des actions susceptibles d'inclure des données confidentielles dans l'enregistrement.

1. Démarrez SimpleWPFApp à l'aide du raccourci sur le Bureau.

     Comme précédemment, notez que le contrôle CheckBox est désactivé.

1. Sur SimpleWPFApp, choisissez **Démarrer**.

     En quelques secondes, la barre de progression atteint 100 %.

1. Sélectionnez le contrôle CheckBox qui est maintenant activé.

1. Fermez l'application SimpleWPFApp.

1. Dans la boîte de dialogue **UIMap - Générateur de test codé de l’interface utilisateur**, choisissez **Générer le code**.

1. Dans la zone **Nom de la méthode**, tapez **SimpleAppTest** et choisissez **Ajouter et générer**. En quelques secondes, le test codé de l’interface utilisateur s’affiche et s’ajoute à la solution.

1. Fermez la boîte de dialogue **UIMap - Générateur de test codé de l’interface utilisateur**.

     Le fichier *CodedUITest1.cs* s’affiche dans l’éditeur de code.

1. Enregistrez votre projet.

### <a name="run-the-test"></a>Exécuter le test

1. Dans le menu **Test**, choisissez **Fenêtres**, puis **Explorateur de tests**.

2. Dans le menu **Générer** , cliquez sur **Générer la solution**.

3. Dans le fichier *CodedUITest1.cs*, recherchez la méthode **CodedUITestMethod**, cliquez avec le bouton droit et sélectionnez **Exécuter les tests** ou exécutez le test à partir de l’**Explorateur de tests**.

   Pendant l'exécution du test codé de l'interface utilisateur, SimpleWPFApp est visible. Les étapes que vous avez effectuées dans la procédure précédente sont exécutées. Toutefois, quand le test tente de cocher la case du contrôle CheckBox, la fenêtre **Résultats des tests** indique que le test a échoué. Cela s'explique par le fait que le test tente de cocher la case, mais ne sait pas que le contrôle CheckBox est désactivé tant que la barre de progression n'a pas atteint 100 %. Vous pouvez corriger ce problème et d'autres problèmes connexes à l'aide des différentes méthodes `UITestControl.WaitForControlXXX()` disponibles pour les tests codés de l'interface utilisateur. La procédure suivante montrera l'utilisation de la méthode `WaitForControlEnabled()` pour corriger le problème à l'origine de l'échec de ce test. Pour plus d’informations, consultez [Mettre en suspens des tests codés de l’interface utilisateur en attendant des événements spécifiques lors de la lecture](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

## <a name="edit-and-rerun-the-coded-ui-test"></a>Modifier et réexécuter le test codé de l’interface utilisateur

1.  Dans la fenêtre de l’**Explorateur de tests**, sélectionnez le test qui a échoué et, dans la section **StackTrace**, choisissez le premier lien vers **UIMap.SimpleAppTest()**.

2.  Le fichier *UIMap.Designer.cs* s’ouvre avec le point d’erreur mis en surbrillance dans le code :

    ```csharp
    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

3.  Pour résoudre ce problème, le test codé de l'interface utilisateur peut attendre que le contrôle CheckBox soit activé avant de continuer sur cette ligne à l'aide de la méthode `WaitForControlEnabled()`.

    > [!WARNING]
    > Ne modifiez pas le fichier *UIMap.Designer.cs*. Toutes les modifications apportées au code seront remplacées chaque fois que vous générez du code dans **UIMap - Générateur de test codé de l'interface utilisateur**. Si vous devez modifier une méthode enregistrée, copiez-la dans le fichier *UIMap.cs* et renommez-la. Le fichier *UIMap.cs* peut être utilisé pour remplacer les méthodes et les propriétés dans le fichier *UIMapDesigner.cs*. Vous devez supprimer la référence à la méthode d’origine dans le fichier *CodedUITest.cs* et la remplacer par le nom de la méthode renommée.

4.  Dans l’**Explorateur de solutions**, recherchez *UIMap.uitest* dans votre projet de test codé de l’interface utilisateur.

5.  Ouvrez le menu contextuel pour *UIMap.uitest* et choisissez **Ouvrir**.

     Le test codé de l'interface utilisateur s'affiche dans l'éditeur de test codé de l'interface utilisateur. Vous pouvez à présent afficher et modifier le test codé de l'interface utilisateur.

6.  Dans le volet **Action de l’interface utilisateur**, sélectionnez la méthode de test (SimpleAppTest) que vous souhaitez déplacer vers le fichier *UIMap.cs* ou *UIMap.vb*. Le déplacement de la méthode dans un autre fichier permet au code personnalisé à ajouter de ne pas être remplacé quand le code de test est recompilé.

7.  Choisissez le bouton **Déplacer le code** dans la barre d’outils de l’**éditeur de test codé de l’interface utilisateur**.

8.  Une boîte de dialogue Microsoft Visual Studio s'affiche. Elle vous informe que la méthode sera déplacée du fichier *UIMap.uitest* dans le fichier *UIMap.cs* et que vous ne pourrez plus la modifier à l’aide de l’éditeur de test codé de l’interface utilisateur. Cliquez sur **Oui**.

     La méthode de test est supprimée du fichier *UIMap.uitest* et n’apparaît plus dans le volet Actions de l’interface utilisateur. Pour modifier le fichier de test déplacé, ouvrez le fichier *UIMap.cs* dans l’**Explorateur de solutions**.

9. Dans la barre d’outils Visual Studio, choisissez **Enregistrer**.

     Les mises à jour apportées à la méthode de test sont enregistrées dans le fichier *UIMap.Designer*.

    > [!WARNING]
    > Une fois que vous avez déplacé la méthode, vous ne pouvez plus la modifier à l'aide de l'éditeur de test codé de l'interface utilisateur. Vous devez ajouter le code personnalisé et le gérer à l'aide de l'éditeur de code.

10. Renommez la méthode `SimpleAppTest()` en `ModifiedSimpleAppTest()`.

11. Ajoutez au fichier la méthode suivante à l'aide de l'instruction :

    ```csharp
    using Microsoft.VisualStudio.TestTools.UITesting.WpfControls;
    ```

12. Ajoutez la méthode `WaitForControlEnabled()` suivante avant la ligne de code incriminée qui a été identifiée précédemment :

    ```csharp
    uICheckBoxCheckBox.WaitForControlEnabled();

    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

13. Dans le fichier *CodedUITest1.cs*, recherchez la méthode **CodedUITestMethod** et supprimez le commentaire de la référence à la méthode SimpleAppTest() d’origine ou renommez la référence, puis remplacez-la par la nouvelle méthode ModifiedSimpleAppTest() :

    ```csharp
    [TestMethod]
            public void CodedUITestMethod1()
            {
                // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
                // For more information on generated code, see http://go.microsoft.com/fwlink/?LinkId=179463
                //this.UIMap.SimpleAppTest();
                this.UIMap.ModifiedSimpleAppTest();
            }
    ```

14. Dans le menu **Générer** , choisissez **Générer la solution**.

15. Cliquez avec le bouton droit sur la méthode **CodedUITestMethod** et sélectionnez **Exécuter les tests**.

16. Cette fois-ci, le test codé de l’interface utilisateur exécute avec succès toutes les étapes du test et la mention **Réussite** s’affiche dans la fenêtre **Explorateur de tests**.

## <a name="refactor-a-control-in-simplewpfapp"></a>Refactoriser un contrôle dans SimpleWPFApp

1.  Dans le fichier *MainWindow.xaml*, dans le concepteur, sélectionnez le contrôle Button.

2.  En haut de la fenêtre **Propriétés**, remplacez la valeur **button1** de la propriété **Nom** par **buttonA**.

3.  Dans le menu **Générer** , choisissez **Générer la solution**.

4.  Dans l’**Explorateur de tests**, exécutez **CodedUITestMethod1**.

     Le test échoue parce que le test codé de l'interface utilisateur ne trouve pas le contrôle Button mappé à l'origine dans UIMap comme button1. La refactorisation peut avoir un impact sur les tests codés de l'interface utilisateur de cette manière.

5.  Dans l’**Explorateur de tests**, dans la section **StackTrace**, choisissez le premier lien en regard de **UIMpa.ModifiedSimpleAppTest()**.

     Le fichier *UIMap.cs* s’ouvre. Le point d'erreur est mis en surbrillance dans le code :

    ```csharp
    // Click 'Start' button
    Mouse.Click(uIStartButton, new Point(27, 10));
    ```

     Notez que la ligne de code présentée précédemment dans cette procédure utilise `UiStartButton` qui est le nom UIMap avant sa refactorisation.

     Pour corriger le problème, vous pouvez ajouter le contrôle refactorisé à UIMap à l’aide du **Générateur de test codé de l’interface utilisateur**. Vous pouvez mettre à jour le code du test pour utiliser le code, comme l’illustre la procédure suivante.

## <a name="map-refactored-control-rerun-the-test"></a>Mapper le contrôle refactorisé pour réexécuter le test

1.  Dans le fichier *CodedUITest1.cs*, dans la méthode **CodedUITestMethod1()**, cliquez avec le bouton droit, sélectionnez **Générer le code pour le test codé de l’interface utilisateur**, puis choisissez **Utiliser le générateur de test codé de l’interface utilisateur**.

     La boîte de dialogue **UIMap - Générateur de test codé de l’interface utilisateur** s’affiche.

2.  À l'aide du raccourci sur le Bureau que vous avez créé précédemment, exécutez l'application SimpleWPFApp créée précédemment.

3.  Dans la boîte de dialogue **UIMap - Générateur de test codé de l’interface utilisateur**, faites glisser l’outil en forme de mire sur le bouton **Start** de SimpleWPFApp.

     Le bouton **Start** est placé dans une zone bleue. Le **Générateur de test codé de l’interface utilisateur** prend quelques secondes pour traiter les données du contrôle sélectionné et afficher les propriétés du contrôle. Notez que la valeur de **AutomationUId** est **buttonA**.

4.  Dans les propriétés du contrôle, choisissez la flèche dans l’angle supérieur gauche pour développer le mappage de contrôle d’interface utilisateur. Notez que **UIStartButton1** est sélectionné.

5.  Dans la barre d’outils, choisissez **Ajouter le contrôle au mappage de contrôle d’interface utilisateur**.

     L’état situé en bas de la fenêtre vérifie l’action en affichant **Le contrôle sélectionné a été ajouté au mappage de contrôle d’interface utilisateur**.

6.  Dans la boîte de dialogue **UIMap - Générateur de test codé de l’interface utilisateur**, choisissez **Générer le code**.

     La boîte de dialogue **Générateur de test codé de l’interface utilisateur - Générer le code** s’affiche avec une note qui indique qu’aucune nouvelle méthode n’est obligatoire et que ce code ne sera généré que pour les modifications apportées au mappage de contrôle d’interface utilisateur.

7.  Choisissez **Générer**.

8.  Fermez SimpleWPFApp.

9. Fermez la boîte de dialogue **UIMap - Générateur de test codé de l’interface utilisateur**.

10. Dans l’**Explorateur de solutions**, ouvrez le fichier *UIMap.Designer.cs*.

11. Dans le fichier *UIMap.Designer.cs*, recherchez la propriété **UIStartButton1**. Notez que `SearchProperties` a pour valeur `"buttonA"` :

    ```csharp
    public WpfButton UIStartButton1
            {
                get
                {
                    if ((this.mUIStartButton1 == null))
                    {
                        this.mUIStartButton1 = new WpfButton(this);
                        #region Search Criteria
                        this.mUIStartButton1.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
                        this.mUIStartButton1.WindowTitles.Add("MainWindow");
                        #endregion
                    }
                    return this.mUIStartButton1;
                }
            }
    ```

     Vous pouvez maintenant modifier le test codé de l'interface utilisateur pour utiliser le nouveau contrôle mappé. Comme signalé dans la procédure précédente, si vous souhaitez remplacer les méthodes ou les propriétés dans le test codé de l’interface utilisateur, vous devez le faire dans le fichier *UIMap.cs*.

12. Dans le fichier *UIMap.cs*, ajoutez un constructeur et spécifiez la propriété `SearchProperties` de la propriété `UIStartButton` pour utiliser la propriété `AutomationID` avec la valeur `"buttonA":`

    ```csharp
    public UIMap()
            {
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
            }
    ```

13. Dans le menu **Générer** , choisissez **Générer la solution**.

14. Dans l’**Explorateur de tests**, exécutez **CodedUITestMethod1**.

     Cette fois-ci, le test codé de l'interface utilisateur exécute avec succès toutes les étapes du test. Dans la fenêtre **Résultats des tests**, l’état **Réussite** s’affiche.

## <a name="videos"></a>Vidéos

![lien vers la vidéo](../data-tools/media/playvideo.gif) [Bien démarrer avec les tests codés de l’interface utilisateur](https://onedrive.live.com/?id=2DB0E1EFE1C1D3B8%21110&cid=2DB0E1EFE1C1D3B8)

## <a name="faq"></a>FAQ

[FAQ concernant les tests codés de l’interface utilisateur](https://social.msdn.microsoft.com/Forums/vsautotest/3a74dd2c-cef8-4923-abbf-7a91f489e6c4/faqs)

## <a name="see-also"></a>Voir aussi

- [Utiliser l’automatisation de l’interface utilisateur pour tester votre code](../test/use-ui-automation-to-test-your-code.md)
- [Plateformes et configurations prises en charge pour les tests codés de l’interface utilisateur et les enregistrements des actions](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Modifier des tests codés de l’interface utilisateur à l’aide de l’éditeur de test codé de l’interface utilisateur](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
