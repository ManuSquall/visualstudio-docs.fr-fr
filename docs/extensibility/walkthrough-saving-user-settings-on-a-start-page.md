---
title: 'Procédure pas à pas : enregistrement des paramètres utilisateur sur une page de démarrage | Microsoft Docs'
description: Découvrez comment conserver les paramètres utilisateur pour votre page de démarrage en enregistrant un paramètre dans le registre à l’aide de cette procédure pas à pas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 2f7dddfca06d7bc475286c73087828305464daa5
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217214"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>Procédure pas à pas : enregistrer les paramètres utilisateur sur une page de démarrage

Vous pouvez conserver les paramètres utilisateur de votre page de démarrage. En suivant cette procédure pas à pas, vous pouvez créer un contrôle qui enregistre un paramètre dans le registre lorsque l’utilisateur clique sur un bouton, puis récupère ce paramètre chaque fois que la page de démarrage est chargée. Étant donné que le modèle de projet page de démarrage comprend un contrôle utilisateur personnalisable et que le code XAML de la page de démarrage par défaut appelle ce contrôle, vous n’êtes pas obligé de modifier la page de démarrage elle-même.

La Banque de paramètres instanciée dans cette procédure pas à pas est une instance de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> interface, qui lit et écrit dans l’emplacement de Registre suivant quand elle est appelée : **HKCU\Software\Microsoft\VisualStudio\14.0 \\ \<CollectionName>**

Lorsqu’il s’exécute dans l’instance expérimentale de Visual Studio, le magasin de paramètres lit et écrit dans **HKCU\Software\Microsoft\VisualStudio\14.0Exp \\ \<CollectionName> .**

Pour plus d’informations sur la façon de rendre des paramètres persistants, consultez [extension des paramètres et des options utilisateur](../extensibility/extending-user-settings-and-options.md).

## <a name="prerequisites"></a>Prérequis

> [!NOTE]
> Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Kit de développement logiciel (SDK) Visual Studio](../extensibility/visual-studio-sdk.md).
>
> Vous pouvez télécharger le modèle de projet page de démarrage à l’aide du **Gestionnaire d’extensions**.

## <a name="set-up-the-project"></a>Configuration du projet

1. Créez un projet de page de démarrage comme décrit dans [créer une page de démarrage personnalisée](creating-a-custom-start-page.md). Nommez le projet **SaveMySettings**.

2. Dans **Explorateur de solutions**, ajoutez les références d’assembly suivantes au projet StartPageControl :

    - EnvDTE

    - EnvDTE80

    - Microsoft. VisualStudio. OLE. Interop

    - Microsoft. VisualStudio. Shell. Interop. 11.0

3. Ouvrez *myControl. Xaml*.

4. Dans le volet XAML, dans la définition de l’élément de niveau supérieur <xref:System.Windows.Controls.UserControl> , ajoutez la déclaration d’événement suivante après les déclarations d’espace de noms.

    ```xml
    Loaded="OnLoaded"
    ```

5. Dans le volet de conception, cliquez sur la zone principale du contrôle, puis appuyez sur la touche **Suppr**.

     Cette étape supprime l' <xref:System.Windows.Controls.Border> élément et tout ce qui se trouve dans celui-ci, et laisse uniquement l’élément de niveau supérieur <xref:System.Windows.Controls.Grid> .

6. À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Controls.StackPanel> contrôle vers la grille.

7. À présent, faites glisser un <xref:System.Windows.Controls.TextBlock> , un <xref:System.Windows.Controls.TextBox> et un bouton vers le <xref:System.Windows.Controls.StackPanel> .

8. Ajoutez un attribut **x :Name** pour <xref:System.Windows.Controls.TextBox> et un `Click` événement pour <xref:System.Windows.Controls.Button> , comme indiqué dans l’exemple suivant.

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>Implémenter le contrôle utilisateur

1. Dans le volet XAML, cliquez avec le bouton droit sur l' `Click` attribut de l' <xref:System.Windows.Controls.Button> élément, puis cliquez sur **naviguer vers le gestionnaire d’événements**.

     Cette étape ouvre *myControl. Xaml. cs* et crée un gestionnaire de stubs pour l' `Button_Click` événement.

2. Ajoutez les `using` directives suivantes au début du fichier.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/startpagedte/cs/startpagecontrol/mycontrol.xaml.cs" id="Snippet11":::

3. Ajoutez une `SettingsStore` propriété privée, comme illustré dans l’exemple suivant.

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

     Cette propriété obtient d’abord une référence à l' <xref:EnvDTE80.DTE2> interface, qui contient le modèle objet Automation, à partir du <xref:System.Windows.FrameworkElement.DataContext%2A> du contrôle utilisateur, puis utilise l’DTE pour obtenir une instance de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> interface. Elle utilise ensuite cette instance pour retourner les paramètres utilisateur actuels.

4. Renseignez l' `Button_Click` événement comme suit.

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

5. Ajoutez le gestionnaire suivant pour l' `OnLoaded` événement du contrôle utilisateur.

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

3. Dans le nœud **environnement** , cliquez sur **démarrage** puis, dans la liste **personnaliser la page de démarrage** , sélectionnez **[extension installée] enregistrer mes paramètres page de démarrage**.

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

Vous pouvez modifier ce contrôle utilisateur pour enregistrer et récupérer un nombre quelconque de paramètres personnalisés en utilisant différentes valeurs de différents gestionnaires d’événements pour obtenir et définir la `SettingsStore` propriété. Tant que vous utilisez un paramètre différent `propertyName` pour chaque appel à <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A> , les valeurs ne remplacent pas les unes des autres dans le registre.

## <a name="see-also"></a>Voir aussi

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [Ajout de commandes Visual Studio à une page de démarrage](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
