---
title: 'Procédure pas à pas : enregistrement des paramètres utilisateur sur une page de démarrage | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: fe3d1040089a4b78368a4da94933a4a1440afafd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647910"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>Procédure pas à pas : enregistrer les paramètres utilisateur sur une page de démarrage

Vous pouvez conserver les paramètres utilisateur de votre page de démarrage. En suivant cette procédure pas à pas, vous pouvez créer un contrôle qui enregistre un paramètre dans le registre lorsque l’utilisateur clique sur un bouton, puis récupère ce paramètre chaque fois que la page de démarrage est chargée. Étant donné que le modèle de projet page de démarrage comprend un contrôle utilisateur personnalisable et que le code XAML de la page de démarrage par défaut appelle ce contrôle, vous n’êtes pas obligé de modifier la page de démarrage elle-même.

La Banque de paramètres instanciée dans cette procédure pas à pas est une instance de l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore>, qui lit et écrit dans l’emplacement de Registre suivant lorsqu’elle est appelée : **HKCU\Software\Microsoft\VisualStudio\14.0 \\ \<CollectionName >**

Lorsqu’il s’exécute dans l’instance expérimentale de Visual Studio, le magasin de paramètres lit et écrit dans **HKCU\Software\Microsoft\VisualStudio\14.0Exp \\ \<CollectionName >.**

Pour plus d’informations sur la façon de rendre des paramètres persistants, consultez [extension des paramètres et des options utilisateur](../extensibility/extending-user-settings-and-options.md).

## <a name="prerequisites"></a>Configuration requise

> [!NOTE]
> Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Kit de développement logiciel (SDK) Visual Studio](../extensibility/visual-studio-sdk.md).
>
> Vous pouvez télécharger le modèle de projet page de démarrage à l’aide du **Gestionnaire d’extensions**.

## <a name="set-up-the-project"></a>Configurer le projet

1. Créez un projet de page de démarrage comme décrit dans [créer une page de démarrage personnalisée](creating-a-custom-start-page.md). Nommez le projet **SaveMySettings**.

2. Dans **Explorateur de solutions**, ajoutez les références d’assembly suivantes au projet StartPageControl :

    - EnvDTE

    - EnvDTE80

    - Microsoft. VisualStudio. OLE. Interop

    - Microsoft. VisualStudio. Shell. Interop. 11.0

3. Ouvrez *myControl. Xaml*.

4. Dans le volet XAML, dans la définition de l’élément de <xref:System.Windows.Controls.UserControl> de niveau supérieur, ajoutez la déclaration d’événement suivante après les déclarations d’espace de noms.

    ```xml
    Loaded="OnLoaded"
    ```

5. Dans le volet de conception, cliquez sur la zone principale du contrôle, puis appuyez sur la touche **Suppr**.

     Cette étape supprime l’élément <xref:System.Windows.Controls.Border> et tout ce qui se trouve dans celui-ci, et laisse uniquement l’élément de <xref:System.Windows.Controls.Grid> de niveau supérieur.

6. À partir de la **boîte à outils**, faites glisser un contrôle <xref:System.Windows.Controls.StackPanel> vers la grille.

7. À présent, faites glisser un <xref:System.Windows.Controls.TextBlock>, un <xref:System.Windows.Controls.TextBox> et un bouton vers le <xref:System.Windows.Controls.StackPanel>.

8. Ajoutez un attribut **x :Name** pour l' <xref:System.Windows.Controls.TextBox> et un événement `Click` pour le <xref:System.Windows.Controls.Button>, comme indiqué dans l’exemple suivant.

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>Implémenter le contrôle utilisateur

1. Dans le volet XAML, cliquez avec le bouton droit sur l’attribut `Click` de l’élément <xref:System.Windows.Controls.Button>, puis cliquez sur **naviguer vers le gestionnaire d’événements**.

     Cette étape ouvre *myControl.Xaml.cs*et crée un gestionnaire de stub pour l’événement `Button_Click`.

2. Ajoutez les directives de `using` suivantes au début du fichier.

     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]

3. Ajoutez une propriété de `SettingsStore` privée, comme illustré dans l’exemple suivant.

    ```csharp
    private IVsWritableSettingsStore _settingsStore = null;
    private IVsWritableSettingsStore SettingsStore
    {
        get
        {
            if (_settingsStore == null)
            {
                // Get a reference to the DTE from the DataContext.
                var typeDescriptor = DataContext as ICustomTypeDescriptor;
                var propertyCollection = typeDescriptor.GetProperties();
                var dte = propertyCollection.Find("DTE", false).GetValue(
                    DataContext) as DTE2;

                // Get the settings manager from the DTE.
                var serviceProvider = new ServiceProvider(
                    (Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);
                var settingsManager = serviceProvider.GetService(
                    typeof(SVsSettingsManager)) as IVsSettingsManager;

                // Write the user settings to _settingsStore.
                settingsManager.GetWritableSettingsStore(
                    (uint)__VsSettingsScope.SettingsScope_UserSettings,
                    out _settingsStore);
            }
            return _settingsStore;
        }
    }
    ```

     Cette propriété obtient d’abord une référence à l’interface <xref:EnvDTE80.DTE2>, qui contient le modèle objet Automation, à partir de la <xref:System.Windows.FrameworkElement.DataContext%2A> du contrôle utilisateur, puis utilise DTE pour obtenir une instance de l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager>. Elle utilise ensuite cette instance pour retourner les paramètres utilisateur actuels.

4. Renseignez l’événement `Button_Click` comme suit.

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {
        int exists = 0;
        SettingsStore.CollectionExists("MySettings", out exists);
        if (exists != 1)
        {
            SettingsStore.CreateCollection("MySettings");
        }
        SettingsStore.SetString("MySettings", "MySetting", txtblk.Text);
    }
    ```

     Cela écrit le contenu de la zone de texte dans un champ « MySetting » dans une collection « MySettings » dans le registre. Si la collection n’existe pas, elle est créée.

5. Ajoutez le gestionnaire suivant pour l’événement `OnLoaded` du contrôle utilisateur.

    ```csharp
    private void OnLoaded(Object sender, RoutedEventArgs e)
    {
        string value;
        SettingsStore.GetStringOrDefault(
            "MySettings", "MySetting", "", out value);
        txtblk.Text = value;
    }
    ```

     Ce code définit le texte de la zone de texte sur la valeur actuelle de « MySetting ».

6. Générez le contrôle utilisateur.

7. Dans **Explorateur de solutions**, ouvrez *source. extension. vsixmanifest*.

8. Dans l’éditeur de manifeste, définissez **Product Name** pour **enregistrer mes paramètres page de démarrage**.

     Cette fonctionnalité définit le nom de la page de démarrage tel qu’il doit apparaître dans la liste **personnaliser la page de démarrage** de la boîte de dialogue **options** .

9. Générez *startpage. Xaml*.

## <a name="test-the-control"></a>Tester le contrôle

1. Appuyez sur **F5**.

     L’instance expérimentale de Visual Studio s’ouvre.

2. Dans l’instance expérimentale, dans le menu **Outils** , cliquez sur **options**.

3. Dans le nœud **environnement** , cliquez sur **démarrage**puis, dans la liste **personnaliser la page de démarrage** , sélectionnez **[extension installée] enregistrer mes paramètres page de démarrage**.

     Cliquez sur **OK**.

4. Fermez la page de démarrage, si elle est ouverte, puis, dans le menu **affichage** , cliquez sur **page de démarrage**.

5. Dans la page de démarrage, cliquez sur l’onglet **myControl** .

6. Dans la zone de texte, tapez **Cat**, puis cliquez sur **enregistrer mon paramètre**.

7. Fermez la page de démarrage, puis rouvrez-la.

     Le mot « Cat » doit s’afficher dans la zone de texte.

8. Remplacez le mot « CAT » par le mot « Dog ». Ne cliquez pas sur le bouton.

9. Fermez la page de démarrage, puis rouvrez-la.

     Le mot « chien » doit s’afficher dans la zone de texte, même si vous n’avez pas enregistré le paramètre, car Visual Studio conserve les fenêtres outil en mémoire, même si elles sont fermées, jusqu’à ce que Visual Studio se ferme.

10. Fermez l’instance expérimentale de Visual Studio.

11. Appuyez sur **F5** pour rouvrir l’instance expérimentale.

12. Le mot « Cat » doit s’afficher dans la zone de texte.

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez modifier ce contrôle utilisateur pour enregistrer et récupérer un nombre quelconque de paramètres personnalisés en utilisant différentes valeurs de différents gestionnaires d’événements pour obtenir et définir la propriété `SettingsStore`. Tant que vous utilisez un paramètre de `propertyName` différent pour chaque appel à <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>, les valeurs ne sont pas remplacées dans le registre.

## <a name="see-also"></a>Voir aussi

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [Ajout de commandes Visual Studio à une page de démarrage](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
