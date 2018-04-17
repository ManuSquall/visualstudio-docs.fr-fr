---
title: Examiner les propriétés XAML pendant le débogage | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: c48e3623ba073d13a2b9ce2309b47a65ef45befb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="inspect-xaml-properties-while-debugging"></a>Inspecter les propriétés XAML en phase de débogage
Vous pouvez obtenir une vue en temps réel de votre code XAML en cours d’exécution avec la **arborescence d’éléments visuels en direct** et **Explorateur de propriétés dynamique**. Ces outils affichent une arborescence des éléments de l’interface utilisateur de votre application XAML en cours d’exécution et montrent les propriétés d’exécution de tout élément d’interface utilisateur que vous sélectionnez.  
  
 Vous pouvez utiliser ces outils dans les configurations suivantes :  
  
|Type d'application|Système d'exploitation et outils|  
|-----------------|--------------------------------|  
|Applications Windows Presentation Foundation (4.0 et versions ultérieures).|Windows 7 et versions ultérieures|  
|Applications pour la plateforme Windows universelle|Windows 10 et versions ultérieures, avec la [Windows 10 SDK](https://dev.windows.com/en-us/downloads/windows-10-sdk)|  
  
## <a name="looking-at-elements-in-the-live-visual-tree"></a>Examen des éléments dans l’arborescence d’éléments visuels dynamique  
 Commençons par une application WPF très simple qui a un affichage de liste et un bouton. Chaque fois que vous cliquez sur le bouton, un autre élément est ajouté à la liste. Les éléments avec un numéro pair sont en gris, tandis que les éléments avec un numéro impair sont en jaune.  
  
 Créez une application WPF c# (fichier > Nouveau > projet, puis sélectionnez c# et recherchez Application WPF). Nommez-le **TestXAML**.  
  
 Modifiez MainWindow.xaml comme suit :  
  
```xaml  
<Window x:Class="TestXAML.MainWindow"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    xmlns:local="clr-namespace:TestXAML"  
    mc:Ignorable="d"  
     Title="MainWindow" Height="350" Width="525">  
    <Grid>  
        <Button x:Name="button" Background="LightBlue" Content="Add Item" HorizontalAlignment="Left" Margin="216,206,0,0" VerticalAlignment="Top" Width="75" Click="button_Click"/>  
        <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="100" VerticalAlignment="Top" Width="100" Margin="205,80,0,0"/>  
    </Grid>  
</Window>  
```  
  
 Dans le fichier MainWindow.xaml.cs, ajoutez le gestionnaire de commandes suivant :  
  
```csharp 
int count;

private void button_Click(object sender, RoutedEventArgs e)  
{  
    ListBoxItem item = new ListBoxItem();  
    item.Content = "Item" + ++count;  
    if (count % 2 == 0)  
    {  
        item.Background = Brushes.LightGray;  
    }  
    else  
    {  
        item.Background = Brushes.LightYellow;  
    }  
    listBox.Items.Add(item);  
}  
```  
  
 Générez le projet et commencez le débogage. (La configuration de build doit être Debug, et non pas Release. Pour plus d’informations sur les configurations de build, consultez [présentation des Configurations de Build](../ide/understanding-build-configurations.md).)  
  
 Lorsque la fenêtre s’affiche, cliquez sur le **ajouter un élément** bouton plusieurs fois. Vous devez voir quelque chose de similaire à :  
  
 ![Fenêtre principale de l’application](../debugger/media/livevisualtree-app.png "LiveVIsualTree-App")  
  
 Ouvrez maintenant le **arborescence d’éléments visuels en direct** fenêtre (**Déboguer > Windows > arborescence d’éléments visuels en direct**, ou recherchez-la sur le côté gauche de l’IDE). Faites glisser en dehors de sa position d’ancrage afin que nous puissions rechercher dans cette fenêtre et **propriétés Live** fenêtre côte à côte. Dans le **arborescence d’éléments visuels en direct** fenêtre, développez le **ContentPresenter** nœud. Il doit contenir des nœuds pour le bouton et la zone de liste. Développez la zone de liste (, puis le **ScrollContentPresenter** et **ItemsPresenter**) pour rechercher des éléments de zone de la liste. La fenêtre doit ressembler à ceci :  
  
 ![ListBoxItem dans l’arborescence d’éléments visuels en direct](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree-ListBoxItem")  
  
 Revenez à la fenêtre d'application et ajoutez quelques éléments. Vous devriez voir plus d’éléments de zone de liste dans le **arborescence d’éléments visuels en direct**.  
  
 Maintenant nous allons examiner les propriétés de l’un des éléments de la zone de liste. Sélectionnez le premier élément de zone de liste dans le **arborescence d’éléments visuels en direct** et cliquez sur le **afficher les propriétés** icône dans la barre d’outils. Le **Explorateur de propriétés dynamique** doit apparaître. Notez que la **contenu** champ est « Item1 » et le **arrière-plan** champ est **#ffffffe0** (jaune clair). Revenez à la **arborescence d’éléments visuels en direct** et sélectionnez le deuxième élément de zone de liste. Le **Explorateur de propriétés dynamique** doit montrer que le **contenu** champ est « Item2 » et le **arrière-plan** champ est **#ffd3d3d3** (gris clair ).  
  
 La structure réelle du code XAML a un grand nombre d’éléments qui vous intéressent probablement pas directement, et si vous ne connaissez pas bien le code vous pouvez avoir des difficultés à parcourir l’arborescence pour trouver ce que vous cherchez. Par conséquent, le **arborescence d’éléments visuels en direct** a quelques méthodes permettant d’utiliser l’interface utilisateur de l’application pour vous aider à trouver l’élément que vous souhaitez examiner.  
  
 **Activer la sélection dans l’application en cours d’exécution**. Vous pouvez activer ce mode lorsque vous sélectionnez le bouton gauche sur la **arborescence d’éléments visuels en direct** barre d’outils. Avec ce mode est activé, vous pouvez sélectionner un élément d’interface utilisateur dans l’application et le **arborescence d’éléments visuels en direct** (et **visionneuse de propriétés dynamique**) met à jour automatiquement pour afficher le nœud dans l’arborescence correspondant à cet élément, et ses propriétés.  
  
 **Afficher les ornements de disposition dans l’application en cours d’exécution**. Vous pouvez activer ce mode quand vous sélectionnez le bouton situé immédiatement à droite du bouton Activer la sélection. Lorsque **afficher les ornements de disposition** est activé, il provoque la fenêtre d’application afficher les lignes horizontales et verticales le long des limites de l’objet sélectionné afin de voir à quoi il est aligné, ainsi que des rectangles montrant les marges. Par exemple, activez les deux options **activer la sélection** et **mise en forme** , puis sélectionnez le **ajouter un élément** bloc de texte dans l’application. Vous devez voir le nœud de bloc de texte dans le **arborescence d’éléments visuels en direct** et les propriétés du bloc de texte le **visionneuse de propriétés dynamique**, ainsi que les lignes horizontales et verticales sur les limites du bloc de texte.  
  
 ![LivePropertyViewer dans DisplayLayout](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer-DisplayLayout")  
  
 **Aperçu de la sélection**. Vous pouvez activer ce mode en sélectionnant le troisième bouton en partant de la gauche dans la barre d’outils de l’arborescence d’éléments visuels dynamique. Ce mode affiche le code XAML dans lequel l'élément a été déclaré, si vous avez accès au code source de l'application. Sélectionnez **activer la sélection** et **aperçu de la sélection**, puis sélectionnez le bouton dans l’application de test. Le fichier MainWindow.xaml s'ouvre dans Visual Studio et le curseur est placé sur la ligne où le bouton est défini.  
  
## <a name="using-xaml-tools-with-running-applications"></a>Utilisation des outils XAML avec les applications en cours d'exécution  
 Vous pouvez utiliser ces outils XAML même quand vous n’avez pas le code source. Lorsque vous attachez à une application XAML en cours d’exécution, vous pouvez utiliser la **arborescence d’éléments visuels en direct** sur les éléments d’interface utilisateur de l’application trop. Voici un exemple, à l’aide de la même application de test WPF que précédemment.  
  
1.  Démarrer le **TestXaml** application dans la configuration Release. Vous ne pouvez pas attacher à un processus qui s’exécute dans un **déboguer** configuration.  
  
2.  Ouvrez une deuxième instance de Visual Studio et cliquez sur **Déboguer > Attacher au processus**. Rechercher **TestXaml.exe** dans la liste des processus disponibles, puis cliquez sur **attacher**.  
  
3.  L'application démarre.  
  
4.  Dans la deuxième instance de Visual Studio, ouvrez le **arborescence d’éléments visuels en direct** (**Déboguer > Windows > arborescence d’éléments visuels en direct**). Vous devez voir le **TestXaml** éléments d’interface utilisateur et doit être en mesure de les manipuler comme vous avez fait lors du débogage de l’application directement.