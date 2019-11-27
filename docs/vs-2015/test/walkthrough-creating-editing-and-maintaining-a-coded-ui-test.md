---
title: 'Procédures pas à pas : création, édition et gestion d’un test codé de l’interface utilisateur | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: f7c25ba7-5c9c-455b-9242-701cda56f90c
caps.latest.revision: 43
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b4d3e7c597766c3b416a7cb637cf0e5e99f71d5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302057"
---
# <a name="walkthrough-creating-editing-and-maintaining-a-coded-ui-test"></a>Procédures pas à pas : création, édition et gestion d'un test codé de l'interface utilisateur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans cette procédure pas à pas, vous allez créer une simple application WPF (Windows Presentation Foundation) afin de montrer comment créer, modifier et gérer un test codé de l'interface utilisateur. La procédure pas à pas fournit des solutions pour la correction des tests interrompus par différents problèmes de synchronisation et de refactorisation des contrôles.

## <a name="prerequisites"></a>Configuration requise
 Pour exécuter cette procédure pas à pas, vous avez besoin de :

- Visual Studio Enterprise

### <a name="create-a-simple-wpf-application"></a>Créer une application WPF simple

1. Dans le menu **FICHIER**, pointez sur **Nouveau** puis sélectionnez **Projet**.

     La boîte de dialogue **Nouveau projet** s'affiche.

2. Dans le volet **Installé**, développez **Visual C#** puis sélectionnez **Bureau Windows**.

3. Au-dessus du volet central, vérifiez que la liste déroulante des frameworks cibles est définie sur **.NET Framework 4.5**.

4. Dans le volet central, sélectionnez le modèle **Application WPF**.

5. Dans la zone de texte **Nom**, tapez **SimpleWPFApp**.

6. Choisissez un dossier dans lequel enregistrer le projet. Dans la zone de texte **Emplacement**, tapez le nom du dossier.

7. Cliquez sur **OK**.

     Le Concepteur WPF pour Visual Studio s'ouvre et affiche le MainWindow du projet.

8. Si la boîte à outils n'est pas encore ouverte, ouvrez-la. Choisissez le menu **AFFICHAGE** puis **Boîte à outils**.

9. Sous la section **Tous les contrôles WPF**, faites glisser un contrôle **Button**, **CheckBox** et **ProgressBar** sur la fenêtre MainWindow de l’aire de conception.

10. Sélectionnez le contrôle Button. Dans la fenêtre Propriétés, changez la valeur de la propriété **Nom** de \<Sans nom> en button1. Changez ensuite la valeur de la propriété **Contenu** de Button en Start.

11. Sélectionnez le contrôle ProgressBar. Dans la fenêtre Propriétés, changez la valeur de la propriété **Nom** de \<Sans nom> en progressBar1. Changez ensuite la valeur de la propriété **Maximum** de **100** en **10000**.

12. Sélectionnez le contrôle Checkbox. Dans la fenêtre Propriétés, changez la valeur de la propriété **Nom** de \<Sans nom> en checkBox1 et effacez la valeur de la propriété **IsEnabled**.

     ![Application WPF simple](../test/media/codedui-wpfapp.png "CodedUI_WPFApp")

13. Double-cliquez sur le contrôle bouton pour ajouter un gestionnaire d'événements Click.

     MainWindow.xmal.cs s'affiche dans l'Éditeur de code avec le curseur dans la nouvelle méthode button1_Click.

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

### <a name="verify-the-wpf-application-runs-correctly"></a>Vérifier l'exécution correcte de l'application WPF

1. Dans le menu **DÉBOGAGE**, sélectionnez **Démarrer le débogage** ou appuyez sur **F5**.

2. Notez que le contrôle CheckBox est désactivé. Choisissez **Démarrer**.

     En quelques secondes, la barre de progression atteint 100 %.

3. Vous pouvez maintenant sélectionner le contrôle CheckBox.

4. Fermez SimpleWPFApp.

### <a name="create-and-run-a-coded-ui-test-for-simplewpfapp"></a>Créer et exécuter un test codé de l'interface utilisateur pour SimpleWPFApp

1. Recherchez l'application SimpleWPFApp que vous avez créée précédemment. Par défaut, l’application se trouve dans C:\Users\\<nom_utilisateur\>\Documents\Visual Studio \<version>\Projects\SimpleWPFApp\SimpleWPFApp\bin\Debug\SimpleWPFApp.exe

2. Créez un raccourci sur le bureau à l'application SimpleWPFApp. Cliquez avec le bouton droit sur SimpleWPFApp.exe et choisissez **Copier**. Sur votre Bureau, cliquez avec le bouton droit et choisissez **Coller le raccourci**.

    > [!TIP]
    > Un raccourci vers l'application simplifie l'ajout ou la modification des tests codés de l'interface utilisateur de votre application. Il permet en effet de démarrer l'application rapidement.

3. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur la solution, choisissez **Ajouter** puis sélectionnez **Nouveau projet**.

     La boîte de dialogue **Ajouter un nouveau projet** apparaît.

4. Dans le volet **Installé**, développez **Visual C#** puis sélectionnez **Test**.

5. Dans le volet central, sélectionnez le modèle **Projet de test codé de l’interface utilisateur**.

6. Cliquez sur **OK**.

     Dans l’Explorateur de solutions, le nouveau projet de test codé de l’interface utilisateur nommé **CodedUITestProject1** est ajouté à votre solution.

     La boîte de dialogue **Générer le code pour le test codé de l’interface utilisateur** s’affiche.

7. Sélectionnez l’option **Enregistrer les actions, modifier le mappage de l’interface utilisateur ou ajouter des assertions** et choisissez **OK**.

     L'UIMap – Générateur de test codé de l'interface utilisateur apparaît, et la fenêtre Visual Studio est réduite.

     Pour plus d’informations sur les options de la boîte de dialogue, consultez [Création de tests codés de l’interface utilisateur](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).

8. Choisissez **Démarrer l’enregistrement** dans l’UIMap – Générateur de test codé de l’interface utilisateur.

     ![Démarrer l’enregistrement](../test/media/cuit-builder-record.png "CUIT_Builder_Record")

     Vous pouvez mettre l'enregistrement en pause si nécessaire, par exemple si vous recevez du courrier électronique et que vous souhaitez y répondre.

     ![Suspendre l’enregistrement](../test/media/cuit.png "CUIT_")

    > [!WARNING]
    > Toutes les actions effectuées sur le Bureau sont enregistrées. Mettez l'enregistrement en pause si vous effectuez des actions susceptibles d'inclure des données confidentielles dans l'enregistrement.

9. Démarrez SimpleWPFApp à l'aide du raccourci sur le Bureau.

     Comme précédemment, notez que le contrôle CheckBox est désactivé.

10. Sur SimpleWPFApp, choisissez **Démarrer**.

     En quelques secondes, la barre de progression atteint 100 %.

11. Sélectionnez le contrôle CheckBox qui est maintenant activé.

12. Fermez l'application SimpleWPFApp.

13. Sur UIMap - Générateur de test codé de l’interface utilisateur, choisissez **Générer le code**.

14. Dans la zone Nom de la méthode, tapez **SimpleAppTest** et choisissez **Ajouter et générer**. En quelques secondes, le test codé de l'interface utilisateur s'affiche et est ajouté à la solution.

15. Fermez la boîte de dialogue UIMap – Générateur de test codé de l'interface utilisateur.

     Le fichier CodedUITest1.cs s'affiche dans l'Éditeur de code.

16. Enregistrez votre projet.

### <a name="run-the-coded-ui-test"></a>Exécuter le test codé de l'interface utilisateur

1. Dans le menu **TEST**, choisissez **Fenêtres** puis **Explorateur de tests**.

2. Dans le menu **GÉNÉRER** , cliquez sur **Générer la solution**.

3. Dans le fichier CodedUITest1.cs, recherchez la méthode **CodedUITestMethod**, cliquez avec le bouton droit et sélectionnez **Exécuter les tests** ou exécutez le test à partir de l’Explorateur de tests.

     Pendant l'exécution du test codé de l'interface utilisateur, SimpleWPFApp est visible. Les étapes que vous avez effectuées dans la procédure précédente sont exécutées. Toutefois, quand le test tente de cocher la case du contrôle CheckBox, la fenêtre Résultats des tests indique que le test a échoué. Cela s'explique par le fait que le test tente de cocher la case, mais ne sait pas que le contrôle CheckBox est désactivé tant que la barre de progression n'a pas atteint 100 %. Vous pouvez corriger ce problème et d'autres problèmes connexes à l'aide des différentes méthodes `UITestControl.WaitForControlXXX()` disponibles pour les tests codés de l'interface utilisateur. La procédure suivante montrera l'utilisation de la méthode `WaitForControlEnabled()` pour corriger le problème à l'origine de l'échec de ce test. Pour plus d’informations, consultez [Suspension des tests codés de l’interface utilisateur en attendant des événements spécifiques pendant la lecture](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

### <a name="edit-and-rerun-the-coded-ui-test"></a>Modifier et réexécuter le test codé de l'interface utilisateur

1. Dans la fenêtre de l’Explorateur de tests, sélectionnez le test qui a échoué et, dans la section **StackTrace**, choisissez le premier lien vers **UIMap.SimpleAppTest()** .

2. Le fichier UIMap.Designer.cs s'ouvre avec le point d'erreur mis en surbrillance dans le code :

    ```csharp

    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

3. Pour résoudre ce problème, le test codé de l'interface utilisateur peut attendre que le contrôle CheckBox soit activé avant de continuer sur cette ligne à l'aide de la méthode `WaitForControlEnabled()`.

    > [!WARNING]
    > Ne modifiez pas le fichier UIMap.Designer.cs. Toutes les modifications de code que vous effectuées dans le fichier UIMapDesigner.cs seront remplacées chaque fois que vous générez du code dans UIMap - Générateur de test codé de l'interface utilisateur. Si vous devez modifier une méthode enregistrée, vous devez la copier dans le fichier UIMap.cs et la renommer. Le fichier UIMap.cs peut être utilisé pour remplacer les méthodes et les propriétés dans le fichier UIMapDesigner.cs. Vous devez supprimer la référence à la méthode d’origine dans le fichier Coded UITest.cs et la remplacer par le nom de la méthode renommée.

4. Dans l’Explorateur de solutions, recherchez **UIMap.uitest** dans votre projet de test codé de l’interface utilisateur.

5. Ouvrez le menu contextuel pour **UIMap.uitest** et choisissez **Ouvrir**.

     Le test codé de l'interface utilisateur s'affiche dans l'éditeur de test codé de l'interface utilisateur. Vous pouvez à présent afficher et modifier le test codé de l'interface utilisateur.

6. Dans le volet **Action d’interface utilisateur**, sélectionnez la méthode de test (SimpleAppTest) que vous voulez déplacer dans le fichier UIMap.cs ou UIMap.vb pour faciliter la fonctionnalité du code personnalisé et faire en sorte que celui-ci ne soit pas remplacé lors de la recompilation du code du test.

7. Choisissez le bouton **Déplacer le code** dans la barre d’outils de l’éditeur de test codé de l’interface utilisateur.

8. Une boîte de dialogue Microsoft Visual Studio s'affiche. Elle vous informe que la méthode sera déplacée du fichier UIMap.uitest dans le fichier UIMap.cs et que vous ne pourrez plus la modifier à l'aide de l'éditeur de test codé de l'interface utilisateur. Cliquez sur **Oui**.

     La méthode de test est supprimée du fichier UIMap.uitest et n'apparaît plus dans le volet Actions d'interface utilisateur. Pour pouvoir modifier le fichier de test déplacé, ouvrez le fichier UIMap.cs dans l'Explorateur de solutions.

9. Dans la barre d’outils [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], choisissez **Enregistrer**.

     Les mises à jour apportées à la méthode de test sont enregistrées dans le fichier UIMap.Designer.

    > [!CAUTION]
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

13. Dans le fichier CodedUITest1.cs, recherchez la méthode **CodedUITestMethod** et supprimez le commentaire de la référence à la méthode SimpleAppTest() d’origine ou renommez la référence, puis remplacez-la par la nouvelle méthode ModifiedSimpleAppTest() :

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

14. Dans le menu **BUILD**, choisissez **Générer la solution**.

15. Cliquez avec le bouton droit sur la méthode **CodedUITestMethod** et sélectionnez **Exécuter les tests**.

16. Cette fois-ci, le test codé de l’interface utilisateur exécute avec succès toutes les étapes du test et la mention **Réussite** s’affiche dans la fenêtre Explorateur de tests.

### <a name="refactor-a-control-in-the-simplewpfapp"></a>Refactoriser un contrôle dans SimpleWPFApp

1. Dans le fichier MainWindow.xaml, dans le Concepteur, sélectionnez le contrôle Button.

2. En haut de la fenêtre Propriétés, remplacez la valeur button1 de la propriété **Nom** par buttonA.

3. Dans le menu **BUILD**, choisissez **Générer la solution**.

4. Dans l’Explorateur de tests, exécutez **CodedUITestMethod1**.

     Le test échoue parce que le test codé de l'interface utilisateur ne trouve pas le contrôle Button mappé à l'origine dans UIMap comme button1. La refactorisation peut avoir un impact sur les tests codés de l'interface utilisateur de cette manière.

5. Dans la fenêtre de l’Explorateur de tests, dans la section **StackTrace**, choisissez le premier lien en regard de **UIMpa.ModifiedSimpleAppTest()** .

     Le fichier UIMap.cs s'ouvre. Le point d'erreur est mis en surbrillance dans le code :

    ```csharp

    // Click 'Start' button
    Mouse.Click(uIStartButton, new Point(27, 10));
    ```

     Notez que la ligne de code présentée précédemment dans cette procédure utilise `UiStartButton` qui est le nom UIMap avant sa refactorisation.

     Pour corriger le problème, vous pouvez ajouter le contrôle refactorisé à UIMap à l'aide du Générateur de test codé de l'interface utilisateur. Vous pouvez mettre à jour le code du test pour utiliser le code, comme l'illustre la procédure suivante.

### <a name="map-refactored-control-and-edit-and-rerun-the-coded-ui-test"></a>Mapper le contrôle refactorisé et modifier et réexécuter le test codé de l'interface utilisateur

1. Dans le fichier CodedUITest1.cs, dans la méthode **CodedUITestMethod1()** , cliquez avec le bouton droit, sélectionnez **Générer le code pour le test codé de l’interface utilisateur**, puis choisissez **Utiliser le générateur de test codé de l’interface utilisateur**.

     La boîte de dialogue UIMap – Générateur de test codé de l'interface utilisateur s'affiche.

2. À l'aide du raccourci sur le Bureau que vous avez créé précédemment, exécutez l'application SimpleWPFApp créée précédemment.

3. Dans la boîte de dialogue UIMap – Générateur de test codé de l’interface utilisateur, faites glisser l’outil en forme de mire sur le bouton **Start** de SimpleWPFApp.

     Le bouton **Start** apparaît dans une zone bleue et le Générateur de test codé de l’interface utilisateur prend quelques secondes pour traiter les données du contrôle sélectionné et affiche les propriétés des contrôles. Notez que **AutomationUId** est nommé **buttonA**.

4. Dans les propriétés du contrôle, choisissez la flèche dans l’angle supérieur gauche pour développer le mappage de contrôle d’interface utilisateur. Notez que **UIStartButton1** est sélectionné.

5. Dans la barre d’outils, choisissez **Ajouter le contrôle au mappage de contrôle d’interface utilisateur**.

     L’état situé en bas de la fenêtre vérifie l’action en affichant **Le contrôle sélectionné a été ajouté au mappage de contrôle d’interface utilisateur**.

6. Dans UIMap - Générateur de test codé de l’interface utilisateur, choisissez **Générer le code**.

     Le Générateur de test codé de l'interface utilisateur - Générer le code s'affiche avec une note qui indique qu'aucune nouvelle méthode n'est obligatoire et ce code ne sera généré que pour les modifications apportées au mappage de contrôle d'interface utilisateur.

7. Choisissez **Générer**.

8. Fermez SimpleWPFApp.exe.

9. Fermez la boîte de dialogue UIMap – Générateur de test codé de l'interface utilisateur.

     La boîte de dialogue UIMap – Générateur de test codé de l'interface utilisateur prend quelques secondes pour traiter les modifications du mappage de contrôle d'interface utilisateur.

10. Dans l'Explorateur de solutions, ouvrez le fichier UIMap.Designer.cs.

11. Dans le fichier UIMap.Designer.cs, recherchez la propriété UIStartButton1. Notez que `SearchProperties` a pour valeur `"buttonA"` :

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

     Vous pouvez maintenant modifier le test codé de l'interface utilisateur pour utiliser le nouveau contrôle mappé. Comme signalé dans la procédure précédente, si vous souhaitez remplacer les méthodes ou les propriétés dans le test codé de l'interface utilisateur, vous devez le faire dans le fichier UIMap.cs.

12. Dans le fichier UIMap.cs, ajoutez un constructeur et spécifiez la propriété `SearchProperties` de la propriété `UIStartButton` pour utiliser la propriété `AutomationID` avec la valeur `"buttonA":`

    ```csharp

    public UIMap()
            {
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
            }

    ```

13. Dans le menu **BUILD**, choisissez **Générer la solution**.

14. Dans l'Explorateur de tests, exécutez CodedUITestMethod1.

     Cette fois-ci, le test codé de l'interface utilisateur exécute avec succès toutes les étapes du test.  Dans la fenêtre Résultats des tests, l’état **Réussite** s’affiche.

## <a name="external-resources"></a>Ressources externes

### <a name="videos"></a>Vidéos
 ![lien vers](../data-tools/media/playvideo.gif "PlayVideo") [les tests codés de l’interface utilisateur-DeepDive-Episode1-gettingstarted](https://go.microsoft.com/fwlink/?LinkID=230573)

 ![lien vers](../data-tools/media/playvideo.gif "PlayVideo") [les tests codés de l’interface utilisateur-DeepDive-Episode2-maintenanceetdébogage](https://go.microsoft.com/fwlink/?LinkID=230574)

 ![lien vers](../data-tools/media/playvideo.gif "PlayVideo") [les tests codés de l’interface utilisateur-DeepDive-Episode3-codagemanuel](https://go.microsoft.com/fwlink/?LinkID=230575)

### <a name="hands-on-lab"></a>Ateliers pratiques
 [Laboratoire virtuel MSDN : Introduction à la création de tests codés de l’interface utilisateur avec Visual Studio 2010](https://go.microsoft.com/fwlink/?LinkID=22508)

### <a name="faq"></a>Forum aux questions
 [FAQ concernant les tests codés de l’interface utilisateur - 1](https://go.microsoft.com/fwlink/?LinkID=230576)

 [FAQ concernant les tests codés de l’interface utilisateur - 2](https://go.microsoft.com/fwlink/?LinkID=230578)

### <a name="forum"></a>Forum
 [Tests d’automation de l’interface utilisateur de Visual Studio (inclut CodedUI)](https://go.microsoft.com/fwlink/?LinkID=224497)

## <a name="see-also"></a>Voir aussi
 [Utiliser UI Automation pour tester votre Code](../test/use-ui-automation-to-test-your-code.md) [prise en main avec les](https://msdn.microsoft.com/18e61d03-b96a-4058-a166-8ec6b3f6116b) [plateformes et configurations prises en charge par le Concepteur WPF pour les tests codés de l’interface utilisateur et les enregistrements des actions](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md) [modification des tests codés de l’interface utilisateur à l’aide de l’éditeur de test codé](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
