---
title: 'Procédure pas à pas : création d’un kit de développement logiciel (SDK) en C# ou Visual Basic | Microsoft Docs'
description: Découvrez comment créer un simple kit de développement logiciel (SDK) de bibliothèque mathématique à l’aide de Visual C#, puis empaqueter le kit de développement logiciel en tant qu’extension Visual Studio à l’aide de cette procédure
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 5b44566e4a8df323af6132128a8881b54c6f493f
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217292"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>Procédure pas à pas : création d’un kit de développement logiciel à l’aide de C# ou Visual Basic
Dans cette procédure pas à pas, vous allez apprendre à créer un kit de développement logiciel (SDK) de bibliothèque mathématique simple à l’aide de Visual C#, puis à empaqueter le kit de développement logiciel en tant qu’extension Visual Studio (VSIX). Vous allez effectuer les procédures suivantes :

- [Pour créer le composant Windows Runtime SimpleMath](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

- [Pour créer le projet d’extension SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
- [Pour créer un exemple d’application qui utilise la bibliothèque de classes](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>Prérequis
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Kit de développement logiciel (SDK) Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a> Pour créer le composant Windows Runtime SimpleMath

1. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet**.

2. Dans la liste des modèles, développez **Visual C#** ou **Visual Basic**, choisissez le nœud **Windows Store** , puis choisissez le modèle de **composant Windows Runtime** .

3. Dans la zone **nom** , spécifiez **SimpleMath**, puis choisissez le bouton **OK** .

4. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet **SimpleMath** , puis choisissez **Propriétés**.

5. Renommez **Class1. cs** en **Arithmetic. cs** et mettez-le à jour pour qu’il corresponde au code suivant :

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmath/arithmetic.cs" id="Snippet3":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmath/arithmetic.vb" id="Snippet3":::

6. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud **« SimpleMath »** de la Solution, puis choisissez **Configuration Manager**.

    La boîte de dialogue **Configuration Manager** s’ouvre.

7. Dans la liste Configuration de la **solution active** , choisissez **version**.

8. Dans la colonne **configuration** , vérifiez que **SimpleMath** Row est défini sur **Release**, puis choisissez le bouton **Fermer** pour accepter la modification.

   > [!IMPORTANT]
   > Le kit de développement logiciel (SDK) pour le composant SimpleMath n’intègre qu’une seule configuration. Cette configuration doit être la version Release, ou les applications qui utilisent le composant ne passeront pas la certification pour le [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] .

9. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet **SimpleMath** , puis choisissez **générer**.

## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a> Pour créer le projet d’extension SimpleMathVSIX

1. Dans le menu contextuel du nœud **« SimpleMath »** de la solution, choisissez **Ajouter**  >  **nouveau projet**.

2. Dans la liste des modèles, développez **Visual C#** ou **Visual Basic**, choisissez le nœud **extensibilité** , puis choisissez le modèle de **projet VSIX** .

3. Dans la zone **nom** , spécifiez **SimpleMathVSIX**, puis choisissez le bouton **OK** .

4. Dans **Explorateur de solutions**, choisissez l’élément **source. extension. vsixmanifest** .

5. Dans la barre de menus, choisissez **Afficher** le  >  **code**.

6. Remplacez le code XML existant par le code XML suivant :

   ```xml
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Metadata>
       <Identity Id="SimpleMath" Version="1.0" Language="en-US" Publisher="[YourName]" />
       <DisplayName>SimpleMath Library</DisplayName>
       <Description xml:space="preserve">Basic arithmetic operations in a WinRT-compatible library. Implemented in C#.</Description>
     </Metadata>
     <Installation Scope="Global" AllUsers="true">
       <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />
     </Installation>
     <Prerequisites>
       <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[14.0,16.0]" />
     </Prerequisites>
     <Dependencies>
       <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />
     </Dependencies>
     <Assets>
       <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />
     </Assets>
   </PackageManifest>
   ```

7. Dans **Explorateur de solutions**, choisissez le projet **SimpleMathVSIX** .

8. Dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément**.

9. Dans la liste des **éléments communs**, développez **données**, puis choisissez **fichier XML**.

10. Dans la zone **nom** , spécifiez `SDKManifest.xml` , puis cliquez sur le bouton **Ajouter** .

11. Dans **Explorateur de solutions**, ouvrez le menu contextuel de `SDKManifest.xml` , choisissez **Propriétés**, puis remplacez la valeur de la propriété **inclure dans VSIX** par **true**.

12. Remplacez le contenu du fichier par le code XML suivant :

    **C#**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (CS)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

    **Visual Basic**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (VB)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

13. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **SimpleMathVSIX** , choisissez **Ajouter**, puis **nouveau dossier**.

14. Renommez le dossier `references` .

15. Ouvrez le menu contextuel du dossier **références** , cliquez sur **Ajouter**, puis choisissez **nouveau dossier**.

16. Renommez le sous-dossier `commonconfiguration` , créez un sous-dossier dans celui-ci, puis nommez-le `neutral` .

17. Répétez les quatre étapes précédentes, en renommant le premier dossier en `redist` .

     Le projet contient maintenant la structure de dossiers suivante :

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **SimpleMath** , puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers**.

19. Dans **l’Explorateur de fichiers**, accédez au dossier *bin\Release* , ouvrez le menu contextuel du fichier **SimpleMath. winmd** , puis choisissez **copier**.

20. Dans **Explorateur de solutions**, collez le fichier dans le dossier *References\commonconfiguration\neutral* du projet **SimpleMathVSIX** .

21. Répétez l’étape précédente, en collant le fichier **SimpleMath. pri** dans le dossier *Redist\commonconfiguration\neutral* du projet **SimpleMathVSIX** .

22. Dans **Explorateur de solutions**, choisissez **SimpleMath. winmd**.

23. Dans la barre de menus, choisissez **Afficher**  >  les **Propriétés** (clavier : Appuyez sur la touche **F4** ).

24. Dans la fenêtre **Propriétés** , affectez à la propriété **action de génération** la valeur **contenu**, puis remplacez la propriété **inclure dans VSIX** par **true**.

25. Dans **Explorateur de solutions**, répétez ce processus pour **SimpleMath. pri**.

26. Dans **Explorateur de solutions**, choisissez le projet **SimpleMathVSIX** .

27. Dans la barre de menus, choisissez **générer**  >  **générer SimpleMathVSIX**.

28. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **SimpleMathVSIX** , puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers**.

29. Dans l' **Explorateur de fichiers**, accédez au dossier *\bin\release* , puis exécutez *SimpleMathVSIX. vsix* pour l’installer.

30. Choisissez le bouton **installer** , attendez que l’installation se termine, puis redémarrez Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Pour créer un exemple d’application qui utilise la bibliothèque de classes

1. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet**.

2. Dans la liste des modèles, développez **Visual C#** ou **Visual Basic**, puis choisissez le nœud **Windows Store** .

3. Choisissez le modèle **application vide** , nommez le projet **ArithmeticUI**, puis choisissez le bouton **OK** .

4. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **ArithmeticUI** , puis choisissez **Ajouter** une  >  **référence**.

5. Dans la liste des types de référence, développez **Windows**, puis choisissez **Extensions**.

6. Dans le volet d’informations, choisissez l’extension de la **Bibliothèque mathématique WinRT** .

    Des informations supplémentaires sur votre kit de développement logiciel (SDK) s’affichent. Vous pouvez choisir le lien **plus d’informations** à ouvrir https://msdn.microsoft.com/ , comme vous l’avez spécifié dans le fichier SDKManifest.xml plus haut dans cette procédure pas à pas.

7. Dans la boîte de dialogue **Gestionnaire de références** , activez la case à cocher **Bibliothèque mathématique WinRT** , puis choisissez le bouton **OK** .

8. Dans la barre de menus, choisissez **Afficher** l'  >  **Explorateur d’objets**.

9. Dans la liste **Parcourir** , choisissez **Math simple**.

     Vous pouvez maintenant explorer ce qui se trouve dans le kit de développement logiciel (SDK).

10. Dans **Explorateur de solutions**, ouvrez **MainPage. Xaml** et remplacez son contenu par le code XAML suivant :

    **C#**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

    **Visual Basic**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

11. Mettez à jour **MainPage. Xaml. cs** pour qu’elle corresponde au code suivant :

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Windows.Foundation;
using Windows.Foundation.Collections;
using Windows.UI.Xaml;
using Windows.UI.Xaml.Controls;
using Windows.UI.Xaml.Controls.Primitives;
using Windows.UI.Xaml.Data;
using Windows.UI.Xaml.Input;
using Windows.UI.Xaml.Media;
using Windows.UI.Xaml.Navigation;

// The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238

namespace ArithmeticUI
{
    /// <summary>
    /// An empty page that can be used on its own or navigated to within a Frame.
    /// </summary>
    public sealed partial class MainPage : Page
    {
        public static string operation = null;

        public MainPage()
        {
            this.InitializeComponent();
        }

        /// <summary>
        /// Invoked when this page is about to be displayed in a Frame.
        /// </summary>
        /// <param name="e">Event data that describes how this page was reached.  The Parameter
        /// property is typically used to configure the page.</param>
        protected override void OnNavigatedTo(NavigationEventArgs e)
        {
        }

        /// <summary>
        /// Sets the operator chosen by the user
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void OnOperatorClick(object sender, RoutedEventArgs e)
        {
            operation = (sender as Button).Content.ToString();
        }

        /// <summary>
        /// Calls the SimpleMath SDK to do simple arithmetic
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void OnResultsClick(object sender, RoutedEventArgs e)
        {
            try
            {
                float firstNumber = float.Parse(this._firstNumber.Text);
                float secondNumber = float.Parse(this._secondNumber.Text);

                SimpleMath.Arithmetic math = new SimpleMath.Arithmetic();

                switch (operation)
                {
                    case "+":
                        this._result.Text = (math.add(firstNumber, secondNumber)).ToString();
                        break;
                    case "-":
                        this._result.Text = (math.subtract(firstNumber, secondNumber)).ToString();
                        break;
                    case "*":
                        this._result.Text = (math.multiply(firstNumber, secondNumber)).ToString();
                        break;
                    case "/":
                        this._result.Text = (math.divide(firstNumber, secondNumber)).ToString();
                        break;
                    default:
                        this._result.Text = "Choose operator";
                        break;
                }
            }
            catch
            {
                this._result.Text = "Enter valid #";
            }
        }
    }
}
```

```vb
' The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238

''' <summary>
''' An empty page that can be used on its own or navigated to within a Frame.
''' </summary>
Public NotInheritable Class MainPage
    Inherits Page

    ''' <summary>
    ''' Invoked when this page is about to be displayed in a Frame.
    ''' </summary>
    ''' <param name="e">Event data that describes how this page was reached.  The Parameter
    ''' property is typically used to configure the page.</param>
    Protected Overrides Sub OnNavigatedTo(e As Navigation.NavigationEventArgs)
    
    End Sub

    Public Shared operation As String = Nothing

    ''' <summary>
    ''' Sets the operator chosen by the user
    ''' </summary>
    ''' <param name="sender"></param>
    ''' <param name="e"></param>
    Private Sub OnOperatorClick(ByVal sender As Object, ByVal e As RoutedEventArgs)
        operation = If(TypeOf sender Is Button, CType(sender, Button), Nothing).Content.ToString()
    End Sub


    ''' <summary>
    ''' Calls the SimpleMath SDK to do simple arithmetic
    ''' </summary>
    ''' <param name="sender"></param>
    ''' <param name="e"></param>
    Private Sub OnResultsClick(ByVal sender As Object, ByVal e As RoutedEventArgs)

        Try

            Dim firstNumber As Single = Single.Parse(Me._firstNumber.Text)
            Dim secondNumber As Single = Single.Parse(Me._secondNumber.Text)

            Dim math As New SimpleMath.Arithmetic()

            Select Case (operation)

                Case "+"
                    Me._result.Text = (math.Add(firstNumber, secondNumber)).ToString()

                Case "-"
                    Me._result.Text = (math.Subtract(firstNumber, secondNumber)).ToString()
                Case "*"
                    Me._result.Text = (math.Multiply(firstNumber, secondNumber)).ToString()
                Case "/"
                    Me._result.Text = (math.Divide(firstNumber, secondNumber)).ToString()
                Case Else
                    Me._result.Text = "Choose operator"

            End Select

        Catch
            Me._result.Text = "Enter valid #"
        End Try
    End Sub
End Class
```

12. Appuyez sur la touche **F5** pour exécuter l’application.

13. Dans l’application, entrez deux nombres, choisissez une opération, puis cliquez sur le **=** bouton.

     Le résultat correct s’affiche.

    Vous avez créé et utilisé avec succès un kit de développement logiciel (SDK) d’extension.

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : création d’un SDK à l’aide de C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Procédure pas à pas : créer un SDK à l’aide de JavaScript](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [Créer un Kit de développement logiciel](../extensibility/creating-a-software-development-kit.md)
