---
title: 'Procédure pas à pas : Enregistrer les paramètres de l’utilisateur sur une page de démarrage (fr) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 8c791bb33d6c6a3952c14d5073857b0c3131cecf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697068"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>Procédure pas à pas : enregistrez les paramètres de l’utilisateur sur une page de démarrage

Vous pouvez maintenir les paramètres de l’utilisateur pour votre page de démarrage. En suivant cette procédure pas à pas, vous pouvez créer un contrôle qui enregistre un paramètre au registre lorsque l’utilisateur clique sur un bouton, puis récupère ce réglage chaque fois que la page de démarrage se charge. Étant donné que le modèle de projet Start Page inclut un contrôle utilisateur personnalisable et que la page de démarrage par défaut XAML appelle ce contrôle, vous n’avez pas à modifier la page de démarrage elle-même.

Le magasin de paramètres qui est instantané dans cette procédure <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> pas à pas est un exemple de l’interface, qui se lit et écrit à l’emplacement du registre suivant quand il s’appelle: **HKCU -Software-Microsoft-VisualStudio -14.0\\\<CollectionName>**

Lorsqu’il est en cours d’exécution dans l’instance expérimentale de Visual Studio, le magasin de paramètres lit et écrit à **HKCU-Software-Microsoft-VisualStudio-14.0Exp\\\<CollectionName>.**

Pour plus d’informations sur la façon de persister les paramètres, voir [Extension paramètres et options utilisateur](../extensibility/extending-user-settings-and-options.md).

## <a name="prerequisites"></a>Prérequis

> [!NOTE]
> Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, voir [Visual Studio SDK](../extensibility/visual-studio-sdk.md).
>
> Vous pouvez télécharger le modèle de projet Start Page en utilisant **Extension Manager**.

## <a name="set-up-the-project"></a>Configuration du projet

1. Créez un projet de page de démarrage tel que décrit dans [Créer une page de démarrage personnalisée](creating-a-custom-start-page.md). Nommez le projet **SaveMySettings**.

2. Dans **Solution Explorer**, ajoutez les références d’assemblage suivantes au projet StartPageControl :

    - EnvDTE

    - EnvDTE80

    - Microsoft.VisualStudio.OLE.Interop

    - Microsoft.VisualStudio.Shell.Interop.11.0

3. Ouvrez *MyControl.xaml*.

4. À partir de la vitre XAML, dans la définition d’élément de haut niveau, <xref:System.Windows.Controls.UserControl> ajouter la déclaration d’événement suivante après les déclarations de l’espace de nom.

    ```xml
    Loaded="OnLoaded"
    ```

5. Dans le volet de conception, cliquez sur la zone principale du contrôle, puis appuyez sur **Supprimer**.

     Cette étape supprime <xref:System.Windows.Controls.Border> l’élément et tout ce qu’il y a dedans, et ne laisse que l’élément de niveau <xref:System.Windows.Controls.Grid> supérieur.

6. De la boîte à <xref:System.Windows.Controls.StackPanel> **outils,** faites glisser un contrôle à la grille.

7. Maintenant, <xref:System.Windows.Controls.TextBlock>faites <xref:System.Windows.Controls.TextBox>glisser un , <xref:System.Windows.Controls.StackPanel>un , et un bouton à la .

8. Ajouter un attribut **x:Name** pour le <xref:System.Windows.Controls.TextBox>, et un `Click` événement pour le <xref:System.Windows.Controls.Button>, comme indiqué dans l’exemple suivant.

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>Mettre en œuvre le contrôle de l’utilisateur

1. Dans la vitre XAML, cliquez `Click` à <xref:System.Windows.Controls.Button> droite sur l’attribut de l’élément, puis cliquez sur **Naviguer vers Event Handler**.

     Cette étape ouvre *MyControl.xaml.cs*et crée un gestionnaire `Button_Click` de talon pour l’événement.

2. Ajoutez les `using` directives suivantes en haut du fichier.

     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]

3. Ajoutez une `SettingsStore` propriété privée, comme le montre l’exemple suivant.

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

     Cette propriété obtient d’abord une référence à l’interface, <xref:EnvDTE80.DTE2> qui contient le modèle d’objet Automation, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> <xref:System.Windows.FrameworkElement.DataContext%2A> à partir du contrôle de l’utilisateur, puis utilise le DTE pour obtenir une instance de l’interface. Ensuite, il utilise cette instance pour retourner les paramètres actuels de l’utilisateur.

4. Remplissez `Button_Click` l’événement comme suit.

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

     Cela écrit le contenu de la boîte de texte à un champ "MySetting" dans une collection "MySettings" dans le registre. Si la collection n’existe pas, elle est créée.

5. Ajoutez le gestionnaire `OnLoaded` suivant pour l’événement du contrôle de l’utilisateur.

    ```csharp
    private void OnLoaded(Object sender, RoutedEventArgs e)
    {
        string value;
        SettingsStore.GetStringOrDefault(
            "MySettings", "MySetting", "", out value);
        txtblk.Text = value;
    }
    ```

     Ce code définit le texte de la boîte de texte à la valeur actuelle de "MySetting".

6. Construisez le contrôle de l’utilisateur.

7. Dans **Solution Explorer**, open *source.extension.vsixmanifest*.

8. Dans l’éditeur manifeste, définissez **le nom du produit** pour enregistrer ma page de démarrage **paramètres**.

     Cette fonctionnalité définit le nom de la page de démarrage telle qu’elle doit apparaître dans la liste de la **page de démarrage personnalisée** dans la boîte de dialogue **Options.**

9. Construire *StartPage.xaml*.

## <a name="test-the-control"></a>Tester le contrôle

1. Appuyez sur **F5**.

     L’exemple expérimental de Visual Studio s’ouvre.

2. Dans le cas expérimental, sur le menu **Tools,** cliquez sur **Options**.

3. Dans le nœud **Environnement,** cliquez sur **Startup**, puis, dans la liste de la **page de démarrage personnalisée,** sélectionnez **[Extension installée] Enregistrer ma page de démarrage Paramètres**.

     Cliquez sur **OK**.

4. Fermez la page de démarrage si elle est ouverte, puis, sur le menu **View,** cliquez sur **Page Démarrer**.

5. Sur la page de départ, cliquez sur l’onglet **MyControl.**

6. Dans la boîte de texte, tapez **Cat**, puis cliquez sur **Enregistrer mon réglage**.

7. Fermez la page de démarrage, puis ouvrez-la à nouveau.

     Le mot "Cat" doit être affiché dans la boîte à texte.

8. Remplacez le mot "Cat" par le mot "Chien". Ne cliquez pas sur le bouton.

9. Fermez la page de démarrage, puis ouvrez-la à nouveau.

     Le mot "Chien" doit être affiché dans la boîte à texte, même si vous n’avez pas enregistrer le paramètre parce que Visual Studio garde les fenêtres de l’outil en mémoire, même si elles sont fermées, jusqu’à ce que Visual Studio lui-même ferme.

10. Fermez l’instance expérimentale de Visual Studio.

11. Appuyez **sur F5** pour rouvrir l’instance expérimentale.

12. Le mot "Cat" doit être affiché dans la boîte à texte.

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez modifier ce contrôle utilisateur pour enregistrer et récupérer n’importe quel nombre de `SettingsStore` paramètres personnalisés en utilisant différentes valeurs de différents gestionnaires d’événements pour obtenir et définir la propriété. Tant que vous utilisez `propertyName` un paramètre <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>différent pour chaque appel, les valeurs ne se sursocrivent pas les uns les autres dans le registre.

## <a name="see-also"></a>Voir aussi

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [Ajout de commandes Visual Studio à une page de démarrage](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
