---
title: Ajout du contrôle utilisateur à la Page de démarrage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 48f079d29fee5587617f95791bc6de7148741735
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60069387"
---
# <a name="adding-user-control-to-the-start-page"></a>Ajout d’un contrôle utilisateur à la page de démarrage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas montre comment ajouter une référence DLL à une Page de démarrage personnalisée. L’exemple ajoute un contrôle utilisateur à la solution, génère le contrôle utilisateur et fait référence à l’assembly généré à partir du fichier .xaml de Page de démarrage. Un nouvel onglet héberge le contrôle utilisateur, qui fonctionne comme un navigateur Web de base.  
  
 Vous pouvez utiliser le même processus pour ajouter n’importe quel assembly qui peut être appelée à partir d’un fichier .xaml.  
  
## <a name="adding-a-wpf-user-control-to-the-solution"></a>Ajout d’un contrôle utilisateur WPF à la Solution  
 Tout d’abord, ajoutez un contrôle utilisateur de Windows Presentation Foundation (WPF) à la solution de Page de démarrage.  
  
1. Créer une Page de démarrage à l’aide, nous avons créé dans [création d’une Page de démarrage personnalisée](../extensibility/creating-a-custom-start-page.md).  
  
2. Dans **l’Explorateur de solutions**, avec le bouton droit de la solution, cliquez sur **ajouter**, puis cliquez sur **nouveau projet**.  
  
3. Dans le volet gauche de la **nouveau projet** boîte de dialogue, développez soit le **Visual Basic** ou **Visual C#** nœud, puis cliquez sur **Windows**. Dans le volet central, sélectionnez **bibliothèque de contrôles utilisateur WPF**.  
  
4. Nommez le contrôle `WebUserControl` puis cliquez sur **OK**.  
  
## <a name="implementing-the-user-control"></a>Implémentation du contrôle utilisateur  
 Pour implémenter un contrôle utilisateur WPF, générer l’interface utilisateur (IU) dans XAML, puis écrire les événements code-behind en c# ou un autre langage .NET.  
  
#### <a name="to-write-the-xaml-for-the-user-control"></a>Pour écrire le XAML pour le contrôle utilisateur  
  
1. Ouvrez le fichier XAML pour le contrôle utilisateur. Dans le \<grille > élément, ajoutez les définitions de ligne suivantes au contrôle.  
  
    ```vb  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto"/>  
        <RowDefinition Height="*" />  
    </Grid.RowDefinitions>  
  
    ```  
  
2. Dans le principal `Grid` élément, ajoutez le code suivant nouvelle `Grid` élément, qui contient une zone de texte pour taper des adresses Web et un bouton pour définir la nouvelle adresse.  
  
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
  
3. Ajouter le frame suivant au niveau supérieur `Grid` élément juste après le `Grid` élément qui contient le bouton et une zone de texte.  
  
    ```vb  
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />  
    ```  
  
4. L’exemple suivant montre le XAML terminé pour le contrôle utilisateur.  
  
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
  
#### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Pour écrire les événements code-behind pour le contrôle utilisateur  
  
1. Dans le concepteur XAML, double-cliquez sur le **définition de l’adresse** bouton que vous avez ajouté au contrôle.  
  
     Le fichier UserControl1.cs s’ouvre dans l’éditeur de code.  
  
2. Renseignez le Gestionnaire d’événements SetButton_Click comme suit.  
  
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
  
     Ce code définit l’adresse Web qui est tapée dans la zone de texte comme cible pour le navigateur Web. Si l’adresse n’est pas valide, le code génère une erreur.  
  
3. Vous devez également gérer l’événement WebFrame_Navigated :  
  
    ```csharp  
    private void WebFrame_Navigated(object sender, EventArgs e)  
    { }  
    ```  
  
4. Générez la solution.  
  
## <a name="adding-the-user-control-to-the-start-page"></a>Ajout du contrôle utilisateur à la Page de démarrage  
 Pour rendre ce contrôle soit disponible pour le projet de la Page de démarrage, dans le fichier de projet Page de démarrage, ajoutez une référence à la nouvelle bibliothèque de contrôle. Vous pouvez ensuite ajouter le contrôle au balisage XAML de Page Démarrer.  
  
1. Dans **l’Explorateur de solutions**, dans le projet de la Page de démarrage, cliquez sur **références** puis cliquez sur **ajouter une référence**.  
  
2. Sur le **projets** onglet, sélectionnez **WebUserControl, plus** puis cliquez sur **OK**.  
  
3. Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
    Génération de la solution rend le contrôle utilisateur disponibles pour IntelliSense pour les autres fichiers dans la solution.  
  
   Pour ajouter le contrôle au balisage XAML de Page Démarrer, ajoutez une référence d’espace de noms à l’assembly, puis placez le contrôle sur la page.  
  
#### <a name="to-add-the-control-to-the-markup"></a>Pour ajouter le contrôle au balisage  
  
1. Dans **l’Explorateur de solutions**, ouvrez le fichier .xaml de Page de démarrage.  
  
2. Dans le **XAML** volet, ajoutez la déclaration d’espace de noms suivante au niveau supérieur <xref:System.Windows.Controls.Grid> élément.  
  
   ```xml  
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
   ```  
  
3. Dans le **XAML** volet, faites défiler vers le \<grille > section.  
  
    La section contient un <xref:System.Windows.Controls.TabControl> élément dans un <xref:System.Windows.Controls.Grid> élément.  
  
4. Ajouter un \<TabControl > élément contenant un \<TabItem > qui contient une référence à votre contrôle utilisateur.  
  
   ```xml  
  
   <TabItem Header="Web" Height="Auto">  
       <vsc:UserControl1 />  
   </TabItem>  
  
   ```  
  
   Vous pouvez maintenant tester le contrôle.  
  
## <a name="testing-a-manually-created-custom-start-page"></a>Test d’une Page de démarrage personnalisée créée manuellement  
  
1. Copie de votre fichier XAML et les fichiers texte ou balisage des fichiers, à la **%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\**  dossier.  
  
2. Si votre page de démarrage fait référence à des contrôles ou les types dans les assemblys qui ne sont pas installés par Visual Studio, copiez les assemblys et les coller ensuite dans _dossier d’installation de Visual Studio_**\Common7\IDE\ PrivateAssemblies\\**.  
  
3. À une invite de commandes Visual Studio, tapez **devenv /rootsuffix Exp** pour ouvrir une instance expérimentale de Visual Studio.  
  
4. Dans l’instance expérimentale, accédez à la **Outils / Options / environnement / démarrage** page et sélectionnez votre fichier XAML à partir de la **personnaliser la Page de démarrage** liste déroulante.  
  
5. Dans le menu **Affichage** , cliquez sur **Page de démarrage**.  
  
     Votre page de démarrage personnalisée doit être affiché. Si vous souhaitez modifier tous les fichiers, fermez l’instance expérimentale, apportez les modifications, copiez et collez les fichiers modifiés et puis ouvrez à nouveau l’instance expérimentale pour afficher les modifications.  
  
## <a name="see-also"></a>Voir aussi  
 [Conteneur des contrôles WPF](http://msdn.microsoft.com/a0177167-d7db-4205-9607-8ae316952566)   
 [Procédure pas à pas : Ajout de XAML personnalisé à la Page de démarrage](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
