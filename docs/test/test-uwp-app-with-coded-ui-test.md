---
title: Tester une application UWP avec un test codé de l’interface utilisateur
ms.date: 05/31/2018
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- uwp
ms.openlocfilehash: aad17d244d70051a363a4cde294c592968093ba0
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85286750"
---
# <a name="create-a-coded-ui-test-to-test-a-uwp-app"></a>Créer un test codé de l’interface utilisateur pour tester une application UWP

Cet article explique comment créer un test codé de l’interface utilisateur pour une application de plateforme Windows universelle (UWP).

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-uwp-app-to-test"></a>Créer une application UWP à tester

La première étape consiste à créer une application UWP simple sur laquelle exécuter le test.

1. Dans Visual Studio, créez un projet à l’aide du modèle **Application vide (Windows universel)** pour Visual C# ou Visual Basic.

   ::: moniker range="vs-2017"

   ![Modèle d’application vide Windows universel](../test/media/blank-uwp-app-template.png)

   ::: moniker-end

1. Dans la boîte de dialogue **Nouveau projet de plateforme Windows universelle**, sélectionnez **OK** pour accepter les versions de plateforme par défaut.

1. Dans l’**Explorateur de solutions**, ouvrez *MainPage.xaml*.

   Le fichier s’ouvre dans le **Concepteur XAML**.

1. Faites glisser un contrôle de bouton et un contrôle de zone de texte depuis la **Boîte à outils** vers l’aire de conception.

     ![Concevoir l’application UWP](../test/media/toolbox-controls.png)

1. Attribuez des noms aux contrôles. Sélectionnez le contrôle de zone de texte, puis dans la fenêtre **Propriétés**, entrez **textBox** dans le champ **Nom**. Sélectionnez le contrôle de bouton, puis dans la fenêtre **Propriétés**, entrez **button** dans le champ **Nom**.

1. Double-cliquez sur le contrôle button et ajoutez le code suivant au corps de la méthode `Button_Click`. Ce code définit simplement le texte de la zone de texte pour le nom du contrôle button, juste pour nous donner quelque chose à vérifier avec le test codé de l’interface utilisateur que nous allons créer plus tard.

   ```csharp
   this.textBox.Text = this.button.Name;
   ```

   ```vb
   Me.textBox.Text = Me.button.Name
   ```

1. Appuyez sur **CTRL** + **F5** pour exécuter l’application. Un résultat tel que celui-ci doit s’afficher :

   ![Application UWP avec une zone de texte et un bouton](media/uwp-app.png)

## <a name="create-a-coded-ui-test"></a>Créer un test d'interface utilisateur codé

1. Pour ajouter un projet de test à une solution, cliquez avec le bouton droit sur la solution dans **l’Explorateur de solutions**, puis choisissez **Ajouter** > **Nouveau projet**.

1. Recherchez et sélectionnez le modèle **Projet de test codé de l’interface utilisateur (Windows universel)**.

   ::: moniker range="vs-2017"

   ![Nouveau projet de test codé de l’interface utilisateur](../test/media/coded-ui-test-project-uwp-template.png)

   ::: moniker-end

   > [!NOTE]
   > Si vous ne voyez pas le modèle **Projet de test codé de l’interface utilisateur (Windows universel)**, vous devez [installer le composant de test codé de l’interface utilisateur](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

1. Dans la boîte de dialogue **Générer le code pour le test codé de l’interface utilisateur**, sélectionnez **Modifier manuellement le test**.

   ![Boîte de dialogue Générer le code pour le test codé de l’interface utilisateur](../test/media/manually-edit-the-test.png)

1. Si votre application UWP n’est pas déjà en cours d’exécution, démarrez-la en appuyant sur **CTRL** + **F5**.

1. Ouvrez la boîte de dialogue **Générateur de test codé de l’interface utilisateur** en plaçant le curseur dans la méthode `CodedUITestMethod1`, puis en choisissant **Test** > **Générer le code pour le test codé de l’interface utilisateur** > **Utiliser le Générateur de test codé de l’interface utilisateur**.

1. Ajoutez les contrôles au mappage de contrôle d’interface utilisateur. Utilisez la croix du **Générateur de test codé de l’interface utilisateur** pour sélectionner le contrôle de bouton dans l’application UWP. Dans la boîte de dialogue **Ajouter des assertions**, développez le volet **Mappage de contrôle d’interface utilisateur** si nécessaire, puis sélectionnez **Ajouter le contrôle au mappage de contrôle d’interface utilisateur**.

     ![Ajouter un contrôle au mappage d'interface utilisateur](../test/media/add-control-to-ui-control-map.png)

1. Répétez l’étape précédente pour ajouter le contrôle de zone de texte au mappage de contrôle d’interface utilisateur.

1. Dans la boîte de dialogue **Générateur de test codé de l’interface utilisateur**, sélectionnez **Générer le code** ou appuyez sur **Ctrl**+**G**. Ensuite, sélectionnez **Générer** afin de créer le code pour les changements du mappage de contrôle d’interface utilisateur.

     ![Générer le code du mappage d'interface utilisateur](../test/media/generate-code-dialog.png)

1. Pour vérifier que le texte de la de zone de texte est bien remplacé par **button** lors d’un clic sur le bouton, cliquez sur le bouton.

     ![Cliquer sur le contrôle de bouton pour définir la valeur de la zone de texte](../test/media/uwp-app-button-textbox.png)

1. Ajoutez une assertion pour vérifier le texte dans le contrôle de zone de texte. Utilisez la croix pour sélectionner le contrôle de zone de texte, puis sélectionnez la propriété **Text** dans la boîte de dialogue **Ajouter des assertions**. Ensuite, sélectionnez **Ajouter une assertion** ou appuyez sur **Alt**+**A**. Dans la zone **Message sur l’échec d’assertion**, entrez **La valeur de la zone de texte est inattendue.** puis sélectionnez **OK**.

     ![Choisir une zone de test avec la croix et ajouter une assertion](../test/media/add-assertion-for-text.png)

1. Générez le code de test pour l’assertion. Dans la boîte de dialogue **Générateur de test codé de l’interface utilisateur**, sélectionnez **Générer le code**. Dans la boîte de dialogue **Générer le code**, sélectionnez **Ajouter et générer**.

     ![Générer le code pour l'assertion d'une zone de texte](../test/media/add-and-generate-assert-method.png)

   Dans l’**Explorateur de solutions**, ouvrez *UIMap.Designer.cs* afin de voir le code ajouté pour la méthode assert et les contrôles.

   > [!TIP]
   > Si vous utilisez Visual Basic, ouvrez *CodedUITest1.vb*. Ensuite, dans le code de la méthode de test `CodedUITestMethod1()`, cliquez avec le bouton droit sur l’appel de la méthode assert `Me.UIMap.AssertMethod1()` et choisissez **Atteindre la définition**. *UIMap.Designer.vb* s’ouvre dans l’éditeur de code, ce qui vous permet de voir le code ajouté pour la méthode assert et les contrôles.

    > [!WARNING]
    > Ne modifiez pas directement les fichiers *UIMap.Designer.cs* ou *UIMap.Designer.vb*. Si vous les modifiez, vos changements sont écrasés quand le test est généré.

    La méthode assert se présente comme suit :

    ```csharp
    public void AssertMethod1()
    {
        #region Variable Declarations
        XamlEdit uITextBoxEdit = this.UIUWPAppWindow.UITextBoxEdit;
        #endregion

        // Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(this.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.");
    }
    ```

    ```vb
    Public Sub AssertMethod1()
        Dim uITextBoxEdit As XamlEdit = Me.UIApp2Window.UITextBoxEdit

        'Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.")
    End Sub
    ```

1. Ensuite, nous avons besoin d’obtenir le **AutomationId** de l’[application](#create-a-uwp-app-to-test) UWP que nous voulons tester. Ouvrez le menu **Démarrer** Windows pour voir la vignette de l’application. Ensuite, faites glisser la croix ![Icône de cible](media/target-icon.png) depuis la boîte de dialogue **Générateur de test codé de l’interface utilisateur** vers la vignette de votre application. Lorsqu’une zone bleue entoure la vignette, relâchez la souris.

   ![Croix](media/cross-hair-tool.png)

   La boîte de dialogue **Ajouter des assertions** s’ouvre et affiche l’**AutomationId** de votre application. Cliquez avec le bouton droit sur **AutomationId** et choisissez **Copier la valeur dans le Presse-papiers**.

   ![AutomationID dans la boîte de dialogue Ajouter une assertion](../test/media/automation-id.png)

1. Ajoutez le code à la méthode de test pour lancer l’application UWP. Dans l’**Explorateur de solutions**, ouvrez *CodedUITest1.cs* ou *CodedUITest1.vb*. Au-dessus de l’appel vers `AssertMethod1`, ajouter le code pour lancer l’application UWP :

   ```csharp
   XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")
   ```

   ```vb
   XamlWindow myAppWindow = XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");
   ```

   Remplacez l’ID d’automation dans l’exemple de code avec la valeur que vous avez copiée dans le Presse-papiers à l’étape précédente.

   > [!IMPORTANT]
   > Découpez le début de l’ID d’automation pour supprimer les caractères comme **P~**. Si vous n’enlevez pas ces caractères, le test lève `Microsoft.VisualStudio.TestTools.UITest.Extension.PlaybackFailureException` lorsqu’il tente de lancer l’application.

1. Ensuite, ajoutez le code à la méthode de test pour cliquer sur le bouton. Dans la ligne après `XamlWindow.Launch`, ajoutez un mouvement permettant d’appuyer sur le contrôle de bouton :

   ```csharp
   Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);
   ```

   ```vb
   Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)
   ```

   Une fois le code ajouté, la méthode de test complète `CodedUITestMethod1` doit ressembler à ce qui suit :

   ```csharp
   [TestMethod]
   public void CodedUITestMethod1()
   {
       XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");

       Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);

       // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
       this.UIMap.AssertMethod1();
   }
   ```

   ```vb
   <CodedUITest(CodedUITestType.WindowsStore)>
   Public Class CodedUITest1

       <TestMethod()>
       Public Sub CodedUITestMethod1()

           ' Launch the app.
           XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")

           '// Tap the button.
           Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)

           Me.UIMap.AssertMethod1()
       End Sub
   ```

1. Générez le projet de test, puis ouvrez **l’Explorateur de tests** en sélectionnant **Test** > **Windows** > **Explorateur de tests**.

1. Sélectionnez **Exécuter tout** pour exécuter le test.

   L’application s’ouvre, le bouton est appuyé et la propriété **Text** de la zone de texte est renseignée. La méthode assert valide la propriété **Text** de la zone de texte.

   Une fois le test terminé, l’**Explorateur de tests** affiche que le test a réussi.

   ![Les tests réussis s'affichent dans l'Explorateur de tests](../test/media/test-explorer-coded-ui-test-passed.png)

## <a name="q--a"></a>Questions et réponses

### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>Q : Pourquoi l’option d’enregistrement de mon test codé de l’interface utilisateur ne figure-t-elle pas dans la boîte de dialogue Générer le code pour le test codé de l’interface utilisateur ?

**R** : L’option d’enregistrement n’est pas prise en charge pour les applications UWP.

### <a name="q-can-i-create-a-coded-ui-test-for-my-uwp-apps-based-on-winjs"></a>Q : Puis-je créer un test codé de l’interface utilisateur pour mes applications UWP basées sur WinJS ?

**R** : Non, seules les applications XAML sont prises en charge.

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>Q : Pourquoi ne puis-je pas modifier le code du fichier UIMap.Designer ?

**R** : Toutes les modifications de code que vous effectuez dans le fichier *UIMapDesigner.cs* sont remplacées chaque fois que vous générez du code dans le **Générateur de test codé de l’interface utilisateur**. Si vous devez modifier une méthode enregistrée, copiez-la dans le fichier *UIMap.cs* et renommez-la. Le fichier *UIMap.cs* peut être utilisé pour substituer les méthodes et les propriétés dans le fichier *UIMapDesigner.cs* . Supprimez la référence à la méthode d’origine dans le fichier *CodedUITest.cs* et remplacez-la par le nom de la méthode renommée.

## <a name="see-also"></a>Voir aussi

- [Utiliser UI Automation pour tester votre code](../test/use-ui-automation-to-test-your-code.md)
- [Définir des propriétés Automation uniques pour les contrôles UWP](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)
