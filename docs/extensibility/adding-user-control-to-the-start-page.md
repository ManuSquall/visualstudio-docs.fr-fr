---
title: Ajout d’un contrôle utilisateur à la page de démarrage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 1d093ecc8afd9fe822c19c2c1f2ceb5765208865
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90011994"
---
# <a name="add-user-control-to-the-start-page"></a>Ajouter un contrôle utilisateur à la page de démarrage

Cette procédure pas à pas montre comment ajouter une référence de DLL à une page de démarrage personnalisée. L’exemple ajoute un contrôle utilisateur à la solution, génère le contrôle utilisateur, puis référence l’assembly généré à partir du fichier Start page *. Xaml* . Un nouvel onglet héberge le contrôle utilisateur, qui fonctionne comme un navigateur Web de base.

Vous pouvez utiliser le même processus pour ajouter n’importe quel assembly pouvant être appelé à partir d’un fichier *. Xaml* .

## <a name="add-a-wpf-user-control-to-the-solution"></a>Ajouter un contrôle utilisateur WPF à la solution

Tout d’abord, ajoutez un contrôle utilisateur Windows Presentation Foundation (WPF) à la solution page de démarrage.

1. Créez une page de démarrage à l’aide de la création d' [une page de démarrage personnalisée](../extensibility/creating-a-custom-start-page.md).

2. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur la solution, cliquez sur **Ajouter**, puis sur **nouveau projet**.

3. Dans le volet gauche de la boîte de dialogue **nouveau projet** , développez le nœud **Visual Basic** ou **Visual C#** , puis cliquez sur **Windows**. Dans le volet central, sélectionnez **bibliothèque de contrôles utilisateur WPF**.

4. Nommez le contrôle `WebUserControl` , puis cliquez sur **OK**.

## <a name="implement-the-user-control"></a>Implémenter le contrôle utilisateur

Pour implémenter un contrôle utilisateur WPF, générez l’interface utilisateur (IU) en XAML, puis écrivez les événements code-behind en C# ou un autre langage .NET.

### <a name="to-write-the-xaml-for-the-user-control"></a>Pour écrire le XAML pour le contrôle utilisateur

1. Ouvrez le fichier XAML pour le contrôle utilisateur. Dans l' `<Grid>` élément, ajoutez les définitions de ligne suivantes au contrôle.

    ```vb
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>

    ```

2. Dans l' `<Grid>` élément principal, ajoutez le nouvel `<Grid>` élément suivant, qui contient une zone de texte pour la saisie d’adresses Web et un bouton pour définir la nouvelle adresse.

    ```xml
    <Grid Grid.Row="0">
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="*" />
            <ColumnDefinition Width="Auto" />
        </Grid.ColumnDefinitions>
        <TextBox x:Name="UserSource" Grid.Column="0" />
        <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
    </Grid>
    ```

3. Ajoutez le frame suivant à l’élément de niveau supérieur `<Grid>` juste après l' `<Grid>` élément qui contient le bouton et la zone de texte.

    ```vb
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
    ```

4. L’exemple suivant montre le code XAML terminé pour le contrôle utilisateur.

    ```xml
    <UserControl x:Class="WebUserControl.UserControl1"
                 xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
                 xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
                 mc:Ignorable="d"
                 d:DesignHeight="300" d:DesignWidth="300">
        <Grid>
            <Grid.RowDefinitions>
                <RowDefinition Height="Auto"/>
                <RowDefinition Height="*" />
            </Grid.RowDefinitions>
            <Grid Grid.Row="0">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>
                <TextBox x:Name="UserSource" Grid.Column="0" />
                <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
            </Grid>
            <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
        </Grid>
    </UserControl>

    ```

### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Pour écrire les événements code-behind pour le contrôle utilisateur

1. Dans le concepteur XAML, double-cliquez sur le bouton **définir une adresse** que vous avez ajouté au contrôle.

    Le fichier *UserControl1.cs* s’ouvre dans l’éditeur de code.

2. Renseignez le gestionnaire d’événements SetButton_Click comme suit.

    ```csharp
    private void SetButton_Click(object sender, RoutedEventArgs e)
    {
        try
        {
            this.WebFrame.Source = new Uri(this.UserSource.Text, UriKind.Absolute);
        }
        catch (Exception error)
        {
            MessageBox.Show(error.Message);
        }
    }
    ```

    Ce code définit l’adresse Web qui est tapée dans la zone de texte en tant que cible du navigateur Web. Si l’adresse n’est pas valide, le code génère une erreur.

3. Vous devez également gérer l’événement WebFrame_Navigated :

    ```csharp
    private void WebFrame_Navigated(object sender, EventArgs e)
    { }
    ```

4. Générez la solution.

## <a name="add-the-user-control-to-the-start-page"></a>Ajouter le contrôle utilisateur à la page de démarrage

Pour rendre ce contrôle disponible pour le projet de page de démarrage, dans le fichier projet de la page de démarrage, ajoutez une référence à la nouvelle bibliothèque de contrôles. Vous pouvez ensuite ajouter le contrôle au balisage XAML de la page de démarrage.

1. Dans **Explorateur de solutions**, dans le projet page de démarrage, cliquez avec le bouton droit sur **références** , puis cliquez sur **Ajouter une référence**.

2. Sous l’onglet **projets** , sélectionnez **webusercontrol** , puis cliquez sur **OK**.

3. Dans le menu **Générer**, cliquez sur **Générer la solution**.

    La génération de la solution rend le contrôle utilisateur disponible pour IntelliSense pour d’autres fichiers de la solution.

    Pour ajouter le contrôle au balisage XAML de la page de démarrage, ajoutez une référence d’espace de noms à l’assembly, puis placez le contrôle sur la page.

### <a name="to-add-the-control-to-the-markup"></a>Pour ajouter le contrôle à la balise

1. Dans **Explorateur de solutions**, ouvrez le fichier Start page *. Xaml* .

2. Dans le volet **XAML** , ajoutez la déclaration d’espace de noms suivante à l’élément de niveau supérieur <xref:System.Windows.Controls.Grid> .

   ```xml
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
   ```

3. Dans le volet **XAML** , faites défiler jusqu’à la \<Grid> section.

    La section contient un <xref:System.Windows.Controls.TabControl> élément dans un <xref:System.Windows.Controls.Grid> élément.

4. Ajoutez un \<TabControl> élément contenant un \<TabItem> qui contient une référence à votre contrôle utilisateur.

    ```xml

    <TabItem Header="Web" Height="Auto">
        <vsc:UserControl1 />
    </TabItem>

    ```

    Vous pouvez maintenant tester le contrôle.

## <a name="test-a-manually-created-custom-start-page"></a>Tester une page de démarrage personnalisée créée manuellement

1. Copiez votre fichier XAML, ainsi que tous les fichiers texte de prise en charge ou fichiers de balisage, dans le dossier *%UserProfile%\My Documents\Visual Studio 2015 \ StartPages \\ *

2. Si votre page de démarrage fait référence à des contrôles ou des types dans des assemblys qui ne sont pas installés par Visual Studio, copiez les assemblys, puis collez-les dans le _dossier d’installation de Visual Studio_** \\ \Common7\IDE\PrivateAssemblies**.

3. À une invite de commandes Visual Studio, tapez **devenv/Rootsuffix exp** pour ouvrir une instance expérimentale de Visual Studio.

4. Dans l’instance expérimentale, accédez à la **Tools**  >  page de démarrage de l’environnement**options**  >  **Environment**  >  **Startup** des outils et sélectionnez votre fichier XAML dans la liste déroulante personnaliser la **page de démarrage** .

5. Dans le menu **Affichage** , cliquez sur **Page de démarrage**.

    Votre page de démarrage personnalisée doit être affichée. Si vous souhaitez modifier des fichiers, vous devez fermer l’instance expérimentale, apporter les modifications, copier et coller les fichiers modifiés, puis rouvrir l’instance expérimentale pour voir les modifications.

## <a name="see-also"></a>Voir aussi

- [Contrôles de conteneur WPF](/previous-versions/bb675291(v=vs.110))
- [Procédure pas à pas : ajouter du code XAML personnalisé à la page de démarrage](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)