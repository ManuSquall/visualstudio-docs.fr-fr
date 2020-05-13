---
title: Ajout du contrôle utilisateur à la page de démarrage (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: b426cfbbfca2e301797644a1fc73f188054d0cfa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740132"
---
# <a name="add-user-control-to-the-start-page"></a>Ajouter le contrôle utilisateur à la page de démarrage

Ce pas-là montre comment ajouter une référence DLL à une page de démarrage personnalisée. L’exemple ajoute un contrôle utilisateur à la solution, construit le contrôle de l’utilisateur, puis fait référence à l’assemblage construit à partir du fichier Start Page *.xaml.* Un nouvel onglet héberge le contrôle de l’utilisateur, qui fonctionne comme un navigateur Web de base.

Vous pouvez utiliser le même processus pour ajouter n’importe quel assemblage qui peut être appelé à partir d’un fichier *.xaml.*

## <a name="add-a-wpf-user-control-to-the-solution"></a>Ajouter un contrôle utilisateur WPF à la solution

Tout d’abord, ajoutez un contrôle utilisateur de la Windows Presentation Foundation (WPF) à la solution Start Page.

1. Créez une page de démarrage en utilisant nous avons créé dans [Créer une page de démarrage personnalisée](../extensibility/creating-a-custom-start-page.md).

2. Dans **Solution Explorer**, cliquez à droite sur la solution, cliquez sur **Ajouter,** puis cliquez sur **New Project**.

3. Dans le volet gauche de la boîte de dialogue **New Project,** étendre le nœud **Visual Basic** ou **Visual CMD,** et cliquez sur **Windows**. Dans le volet du milieu, sélectionnez **WPF User Control Library**.

4. Nommez `WebUserControl` le contrôle, puis cliquez **sur OK**.

## <a name="implement-the-user-control"></a>Mettre en œuvre le contrôle de l’utilisateur

Pour implémenter un contrôle utilisateur WPF, créez l’interface utilisateur (interface utilisateur) dans XAML, puis écrivez les événements de code-derrière dans C ou une autre langue .NET.

### <a name="to-write-the-xaml-for-the-user-control"></a>Pour écrire le XAML pour le contrôle de l’utilisateur

1. Ouvrez le fichier XAML pour le contrôle de l’utilisateur. Dans `<Grid>` l’élément, ajoutez les définitions de ligne suivantes au contrôle.

    ```vb
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>

    ```

2. Dans l’élément principal, `<Grid>` `<Grid>` ajoutez le nouvel élément suivant, qui contient une boîte de texte pour taper des adresses Web et un bouton pour définir la nouvelle adresse.

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

3. Ajoutez le cadre suivant à `<Grid>` l’élément `<Grid>` de haut niveau juste après l’élément qui contient le bouton et la boîte à texte.

    ```vb
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
    ```

4. L’exemple suivant montre le XAML complété pour le contrôle de l’utilisateur.

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

### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Pour écrire les événements de code-derrière pour le contrôle de l’utilisateur

1. Dans le concepteur XAML, cliquez double sur le bouton **Set Address** que vous avez ajouté au contrôle.

    Le *fichier UserControl1.cs* s’ouvre dans l’éditeur de code.

2. Remplissez le gestionnaire d’événements SetButton_Click comme suit.

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

    Ce code définit l’adresse Web qui est tapée dans la boîte de texte comme cible pour le navigateur Web. Si l’adresse n’est pas valide, le code lance une erreur.

3. Vous devez également vous occuper de l’événement WebFrame_Navigated :

    ```csharp
    private void WebFrame_Navigated(object sender, EventArgs e)
    { }
    ```

4. Générez la solution.

## <a name="add-the-user-control-to-the-start-page"></a>Ajouter le contrôle utilisateur à la page de démarrage

Pour mettre ce contrôle à la disposition du projet Start Page, dans le dossier du projet Start Page, ajoutez une référence à la nouvelle bibliothèque de contrôle. Ensuite, vous pouvez ajouter le contrôle à la page de démarrage XAML balisage.

1. Dans **Solution Explorer**, dans le projet Start Page, cliquez à droite **Références,** puis cliquez sur **Ajouter référence**.

2. Sur l’onglet **Projets,** sélectionnez **WebUserControl,** puis cliquez **sur OK**.

3. Dans le menu **Générer**, cliquez sur **Générer la solution**.

    La construction de la solution rend le contrôle utilisateur disponible pour IntelliSense pour d’autres fichiers dans la solution.

    Pour ajouter le contrôle à la balisage Start Page XAML, ajoutez une référence d’espace nom à l’assemblage, puis mettez le contrôle sur la page.

### <a name="to-add-the-control-to-the-markup"></a>Pour ajouter le contrôle à la majoration

1. Dans **Solution Explorer**, ouvrez le fichier Start Page *.xaml.*

2. Dans la vitre **XAML,** ajoutez la déclaration d’espace nom suivant à l’élément de haut niveau. <xref:System.Windows.Controls.Grid>

   ```xml
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
   ```

3. Dans la vitre **XAML,** \<faites défiler la section Grid>.

    La section <xref:System.Windows.Controls.TabControl> contient un <xref:System.Windows.Controls.Grid> élément dans un élément.

4. Ajoutez \<un élément TabControl> \<contenant un> TabItem qui contient une référence à votre contrôle utilisateur.

    ```xml

    <TabItem Header="Web" Height="Auto">
        <vsc:UserControl1 />
    </TabItem>

    ```

    Maintenant, vous pouvez tester le contrôle.

## <a name="test-a-manually-created-custom-start-page"></a>Testez une page de démarrage personnalisée créée manuellement

1. Copiez votre fichier XAML, et tous les fichiers texte à l’appui ou fichiers de *balisage, au\\ dossier %USERPROFILE%-My Documents-Visual Studio 2015-StartPages.*

2. Si votre page de démarrage fait référence à des contrôles ou des types dans des assemblages qui ne sont pas installés par Visual Studio, copiez les assemblages et collez-les dans le _dossier d’installation Visual Studio_**'Common7'IDE’PrivateAssemblies\\**.

3. Lors d’une invite de commande Visual Studio, type **devenv/rootsuffix Exp** pour ouvrir une instance expérimentale de Visual Studio.

4. Dans le cas expérimental, rendez-vous sur la page **Tools** > **Options** > **Environment** > **Startup** et sélectionnez votre fichier XAML à partir de la page De démarrage **personnalisée.**

5. Dans le menu **Affichage** , cliquez sur **Page de démarrage**.

    Votre page de démarrage personnalisée doit être affichée. Si vous souhaitez modifier des fichiers, vous devez fermer l’instance expérimentale, apporter les modifications, copier et coller les fichiers modifiés, puis rouvrir l’instance expérimentale pour afficher les modifications.

## <a name="see-also"></a>Voir aussi

- [Contrôles des conteneurs WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
- [Procédure pas à pas : Ajoutez XAML personnalisé à la page de départ](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
